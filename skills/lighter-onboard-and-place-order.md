---
name: Onboard a Lighter account and place an order
description: >-
  Resolve an Ethereum address to a Lighter account index, confirm the API key, fetch the market's
  precision rules, obtain the next nonce, then sign and submit a create-order transaction with a
  unique client_order_index.
api: openapi/lighter-zklighter-openapi-original.json
operations:
  - accountsByL1Address
  - apikeys
  - orderBooks
  - nextNonce
  - sendTx
  - accountActiveOrders
generated: '2026-07-19'
method: generated
source: https://apidocs.lighter.xyz/docs/get-started
---

# Onboard a Lighter account and place an order

Lighter is a zk-proven perpetuals exchange. Reads are ordinary REST calls; **writes are signed
transactions**, not plain authenticated requests. You sign a transaction body with an API private
key and submit it through `sendTx`.

Base URL: `https://mainnet.zklighter.elliot.ai` (testnet: `https://testnet.zklighter.elliot.ai`).

## 1. Resolve the account index

Call **`accountsByL1Address`** with the user's Ethereum address. It returns every account tied to
that wallet, including sub-accounts. The integer `index` is what every other call means by
"account index" — never assume it equals 0.

## 2. Confirm the API key

Call **`apikeys`** with the account index. Pass `api_key_index=255` to list all keys on the account.

- Indexes 0-3 are reserved for Lighter's web and mobile clients. Use 2-254 for your own keys.
- Each key carries its own nonce.
- If the key is missing or unregistered you will get error `21109` (api key not found) or `21108`
  (invalid PublicKey, please run changePubKey). Registering a key requires the L1 wallet — that is
  an onboarding step outside this skill.

## 3. Read the market's precision rules

Call **`orderBooks`**. For the target market read `supported_size_decimals`,
`supported_price_decimals`, `min_base_amount` and `min_quote_amount`.

`base_amount` and `price` are submitted as **integers scaled by those decimals**. Getting this
wrong is the most common cause of `21701` (invalid base amount) and `21702` (invalid price).

## 4. Get the next nonce

Call **`nextNonce`** with the account index and API key index. The server requires
`new_nonce = old_nonce + 1` unless you set `skip_nonce`. A wrong value returns `21104`
(invalid nonce); in a batch, a non-increasing sequence returns `21105`.

The Python SDK manages nonces for you. Manage them locally only if you are running multiple keys
for latency reasons.

## 5. Sign and submit

Sign the create-order body (tx type `14`, `TxTypeL2CreateOrder`) with the API private key, then call
**`sendTx`**. Use `sendTxBatch` for up to 50 transactions per REST batch (15 per WebSocket message);
every transaction in a batch must use the same account and API key or you get `21121`.

**Choose a `client_order_index` that is unique across all markets for the account.** This is
Lighter's idempotency handle:

- A duplicate is rejected with `21728` (client order index already exists), so a retried submission
  cannot double-place the order.
- You need it again to cancel or modify the order.

Never generate a fresh `client_order_index` on retry — reuse the original one so the retry stays
idempotent.

## 6. Confirm

Call **`accountActiveOrders`** (auth required) to confirm placement, or subscribe to the
`account_orders/{market_index}/{account_id}` WebSocket channel for push updates. Use `tx` to look up
the submitted transaction by hash; status `2` means executed, `0` means failed.

## Error handling

Lighter returns a numeric business error code plus a message, not RFC 9457 problem details. The
full 239-code registry is in `errors/lighter-error-codes.yml`. Watch for:

| Code | Meaning | Action |
|---|---|---|
| 21104 / 21105 | invalid or non-increasing nonce | re-read `nextNonce`, resubmit |
| 21728 | client order index already exists | the order is already in flight — do not retry with a new index |
| 21733 / 21734 | price flagged as accidental, or too far from mark price | re-check scaling and the mark price |
| 21739 | not enough margin to create the order | reduce size or add collateral |
| 23000 | too many requests | back off; see `rate-limits/lighter-rate-limits.yml` |

Standard accounts are capped at 60 requests per rolling minute. Authenticate every request so only
L1-address limits apply rather than IP limits.
