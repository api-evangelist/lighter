---
name: Pull Lighter market data and account history
description: >-
  Read-only workflow for market discovery, order book depth, trade prints, candles, funding rates
  and bulk account history export — using a long-lived read-only token that cannot trade.
api: openapi/lighter-zklighter-openapi-original.json
operations:
  - systemConfig
  - orderBooks
  - orderBookDetails
  - orderBookOrders
  - recentTrades
  - candles
  - funding-rates
  - exchangeStats
  - trades
  - export
  - tokens_create
  - tokens_revoke
generated: '2026-07-19'
method: generated
source: https://apidocs.lighter.xyz/
---

# Pull Lighter market data and account history

Use this skill for analytics, dashboards and backtesting. It never signs a transaction.

Base URL: `https://mainnet.zklighter.elliot.ai`.

## Use a read-only credential

For account-scoped reads, mint a **read-only token** with **`tokens_create`** rather than handing an
agent a signing key. Read-only tokens:

- can query auth-gated endpoints and channels,
- **cannot** place trades or request withdrawals,
- have the form `ro:{account_index}:{single|all}:{expiry_unix}:{random_hex}`,
- last between 1 day and 10 years, 10 per account maximum.

Revoke with **`tokens_revoke`**. Users can also mint them at
`https://app.lighter.xyz/read-only-tokens/`.

Public market data below needs no credential at all.

## Market discovery

1. **`systemConfig`** — system-level configuration.
2. **`orderBooks`** — the market list with fees and precision. Read `supported_size_decimals`,
   `supported_price_decimals`, `supported_quote_decimals`, `min_base_amount` and `min_quote_amount`.
   Taker and maker fees are percentages.
3. **`orderBookDetails`** — order book metadata.

## Depth, prints and series

- **`orderBookOrders`** — current resting orders for a market.
- **`recentTrades`** — recent public prints.
- **`candles`** — OHLC series. Bad ranges return `22400` (end must exceed start), `22402`
  (unsupported resolution) or `22403` (time range exceeds the maximum for that resolution).
- **`funding-rates`** — funding rate series.
- **`exchangeStats`** — exchange-wide statistics.

For live data prefer the WebSocket stream over polling — see
`asyncapi/lighter-zklighter-asyncapi.yml`. Channels `order_book/{market}`, `trade/{market}`,
`candle/{market}/{resolution}` and `market_stats/all` cover most needs, and
`wss://mainnet.zklighter.elliot.ai/stream?readonly=true` works without an account.

## Account history

- **`trades`** — fills for an account, sub-accounts and public pools. `auth` is required for master
  and sub-accounts.
- **`export`** — bulk export of trades and funding payments. Hard limits: at most 12 months or 1M
  trades per call, and both timestamps must be at or after **2025-01-17T00:00:00Z**, Lighter's
  mainnet genesis. Chunk longer ranges into 12-month windows.

## Rate limit discipline

Limits are weighted per rolling minute. The heavy calls in this skill are expensive:

| Operation | Weight |
|---|---|
| `trades`, `recentTrades` | 600 |
| `tokens_create` | 23000 |
| everything else here | 300 |

A standard account gets 60 requests per rolling minute; premium gets 24,000 weighted. Authenticating
every request moves you off IP-based limits onto L1-address limits. Back off on `23000`
(Too Many Requests). Full detail in `rate-limits/lighter-rate-limits.yml`.
