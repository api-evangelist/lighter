---
name: Manage Lighter account tier, API keys and withdrawals
description: >-
  Inspect account limits and positions, switch execution tier, configure maker-only API keys, and
  move funds out via withdrawal history and fast withdrawals — with the guardrails each step enforces.
api: openapi/lighter-zklighter-openapi-original.json
operations:
  - account
  - accountLimits
  - positionFunding
  - accountActiveOrders
  - changeAccountTier
  - getMakerOnlyApiKeys
  - setMakerOnlyApiKeys
  - fastwithdraw_info
  - fastwithdraw
  - withdraw_history
  - deposit_history
  - transfer_history
generated: '2026-07-19'
method: generated
source: https://apidocs.lighter.xyz/docs/account-types
---

# Manage Lighter account tier, API keys and withdrawals

These are the account-administration flows. Several are rate-limited to a handful of calls per
minute and some are irreversible for 24 hours — check preconditions before acting.

## Inspect the account

- **`account`** — account state by account index or L1 address.
- **`accountLimits`** — the limits that apply to this account's tier.
- **`positionFunding`** — funding paid or received per position.
- **`accountActiveOrders`** — open orders (auth required).

## Switch execution tier

**`changeAccountTier`** moves the L1 address between Standard, Plus and Premium. Preconditions,
all enforced server-side:

- no open positions (`62004`),
- no open orders (`62005`),
- at least 24 hours since the last change (`62006`),
- the target tier must differ from the current one (`62003`).

A change already in flight returns `62001`. This endpoint carries a weight of **3000** — both
standard and premium accounts get roughly 8 calls per rolling minute.

Tier economics (staked LIT sets the Premium sub-tier) are captured in `plans/lighter-plans.yml`.
Standard trades at 0% maker and 0% taker with 300ms taker latency; Premium buys 0ms maker/cancel
latency and higher `sendTx` throughput.

## Maker-only API keys

On a Premium account, up to 251 keys per account index can be restricted to post-only (ALO) orders,
modifies on ALO orders, and cancels — in exchange for a lower-latency execution path.

- **`getMakerOnlyApiKeys`** — read the current set.
- **`setMakerOnlyApiKeys`** — write the set.

Keys 0-3 are reserved for Lighter's own clients and cannot be marked maker-only. There is a
one-hour cooldown between changes.

## Move funds out

Two withdrawal paths, with different trust and signing requirements:

**Secure withdrawal** — can be executed with the API key alone, but only to the same L1 address that
created the account. Status becomes `claimable` when ready; it does not reach `completed`.

**Fast withdrawal** — can go to a different L1 address, and therefore **requires signing with the
wallet's Ethereum private key**, not just the API key. Call **`fastwithdraw_info`** first for
current parameters, then **`fastwithdraw`**. Fast withdrawals via Arbitrum are the ones that reach
`completed`. Weight 3000.

Transfers to another L1 address carry the same wallet-signature requirement.

## Audit the money movement

**`deposit_history`**, **`transfer_history`** and **`withdraw_history`**. `transfer_history`
requires `auth` to resolve an account index unless the account is a public pool.

## Error handling

| Code | Meaning |
|---|---|
| 21111 / 21112 | account in pre-liquidation or liquidation — transactions that do not improve health are blocked |
| 21116 / 21117 | withdrawal amount too low / too high |
| 21126 | an account with zero collateral cannot change its public key |
| 21137 | withdrawals restricted for this asset |
| 23004 | too many L2 withdrawal requests |
| 62001-62006 | tier change failures, see above |

Full registry: `errors/lighter-error-codes.yml`.
