# Lighter

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Lighter is a decentralized perpetual futures exchange built on zkLighter, a zero-knowledge rollup that produces verifiable proofs of order matching and liquidations while targeting the latency of a centralized venue. Traders register a Lighter account by signing with an Ethereum wallet, then operate it through up to 256 API keys across master and sub-accounts. The public zkLighter REST API exposes 78 operations covering order books, trades, candles, funding rates, accounts, positions, public pools, referrals, deposits, transfers and withdrawals, alongside a WebSocket stream carrying order book, trade, candle, position and account-transaction channels. Writes are signed transactions rather than plain authenticated calls: clients sign an order, cancel, modify or transfer body with an API private key and submit it via sendTx or sendTxBatch. Lighter ships first-party Python and Go SDKs, runs a full testnet deployment, publishes a 239-entry numeric error registry, weighted per-tier rate limits, and a vulnerability disclosure policy.

**Areas:** Company · Trading · Cryptocurrency · Decentralized Finance · Perpetual Futures · Exchange · Blockchain · Zero Knowledge · Market Data · WebSocket · Real-Time

## Lighter on APIs.io

Everything profiled for Lighter is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/lighter/](https://apis.io/providers/lighter/)** — or go straight to one of the APIs or properties below.

### APIs (13)

- [Lighter Account API](https://apis.io/apis/lighter/lighter-account-api/) — The account API from Lighter — 26 operation(s) for account.
- [Lighter Announcement API](https://apis.io/apis/lighter/lighter-announcement-api/) — The announcement API from Lighter — 1 operation(s) for announcement.
- [Lighter Block API](https://apis.io/apis/lighter/lighter-block-api/) — The block API from Lighter — 3 operation(s) for block.
- [Lighter Bridge API](https://apis.io/apis/lighter/lighter-bridge-api/) — The bridge API from Lighter — 6 operation(s) for bridge.
- [Lighter Candlestick API](https://apis.io/apis/lighter/lighter-candlestick-api/) — The candlestick API from Lighter — 2 operation(s) for candlestick.
- [Lighter Funding API](https://apis.io/apis/lighter/lighter-funding-api/) — The funding API from Lighter — 1 operation(s) for funding.
- [Lighter Info API](https://apis.io/apis/lighter/lighter-info-api/) — The info API from Lighter — 5 operation(s) for info.
- [Lighter Notification API](https://apis.io/apis/lighter/lighter-notification-api/) — The notification API from Lighter — 1 operation(s) for notification.
- [Lighter Order API](https://apis.io/apis/lighter/lighter-order-api/) — The order API from Lighter — 12 operation(s) for order.
- [Lighter Referral API](https://apis.io/apis/lighter/lighter-referral-api/) — The referral API from Lighter — 6 operation(s) for referral.
- [Lighter Root API](https://apis.io/apis/lighter/lighter-root-api/) — The root API from Lighter — 2 operation(s) for root.
- [Lighter Tokenlist API](https://apis.io/apis/lighter/lighter-tokenlist-api/) — The tokenlist API from Lighter — 1 operation(s) for tokenlist.
- [Lighter Transaction API](https://apis.io/apis/lighter/lighter-transaction-api/) — The transaction API from Lighter — 12 operation(s) for transaction.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Lighter zkLighter WebSocket API](https://apis.io/asyncapis/lighter/lighter-zklighter-asyncapi/)

#### Event channels (22)

Individual events and webhooks the provider emits.

- [account_all/{accountId}](https://apis.io/channels/lighter/account-all-accountid/)
- [account_all_assets/{accountId}](https://apis.io/channels/lighter/account-all-assets-accountid/)
- [account_all_orders/{accountId}](https://apis.io/channels/lighter/account-all-orders-accountid/)
- [account_all_positions/{accountId}](https://apis.io/channels/lighter/account-all-positions-accountid/)
- [account_all_trades/{accountId}](https://apis.io/channels/lighter/account-all-trades-accountid/)
- [account_market/{marketId}/{accountId}](https://apis.io/channels/lighter/account-market-marketid-accountid/)
- [account_orders/{marketIndex}/{accountId}](https://apis.io/channels/lighter/account-orders-marketindex-accountid/)
- [account_spot_avg_entry_prices/{accountId}](https://apis.io/channels/lighter/account-spot-avg-entry-prices-accountid/)
- [account_tx/{accountId}](https://apis.io/channels/lighter/account-tx-accountid/)
- [candle/{marketId}/{resolution}](https://apis.io/channels/lighter/candle-marketid-resolution/)
- [height](https://apis.io/channels/lighter/height/)
- [mark_price_candle/{marketId}/{resolution}](https://apis.io/channels/lighter/mark-price-candle-marketid-resolution/)
- [market_stats/{marketIndex}](https://apis.io/channels/lighter/market-stats-marketindex/)
- [notification/{accountId}](https://apis.io/channels/lighter/notification-accountid/)
- [order_book/{marketIndex}](https://apis.io/channels/lighter/order-book-marketindex/)
- [pool_data/{accountId}](https://apis.io/channels/lighter/pool-data-accountid/)
- [pool_info/{accountId}](https://apis.io/channels/lighter/pool-info-accountid/)
- [rfq](https://apis.io/channels/lighter/rfq/)
- [spot_market_stats/{marketIndex}](https://apis.io/channels/lighter/spot-market-stats-marketindex/)
- [ticker/{marketIndex}](https://apis.io/channels/lighter/ticker-marketindex/)
- [trade/{marketIndex}](https://apis.io/channels/lighter/trade-marketindex/)
- [user_stats/{accountId}](https://apis.io/channels/lighter/user-stats-accountid/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [lighter](https://apis.io/servers/lighter/lighter/)

#### Collections (13)

Postman and Open Collection request collections.

- [Lighter account API](https://apis.io/collections/lighter/open-lighter-account-api/)
- [Lighter account announcement API](https://apis.io/collections/lighter/open-lighter-announcement-api/)
- [Lighter account block API](https://apis.io/collections/lighter/open-lighter-block-api/)
- [Lighter account bridge API](https://apis.io/collections/lighter/open-lighter-bridge-api/)
- [Lighter account candlestick API](https://apis.io/collections/lighter/open-lighter-candlestick-api/)
- [Lighter account funding API](https://apis.io/collections/lighter/open-lighter-funding-api/)
- [Lighter account info API](https://apis.io/collections/lighter/open-lighter-info-api/)
- [Lighter account notification API](https://apis.io/collections/lighter/open-lighter-notification-api/)
- [Lighter account order API](https://apis.io/collections/lighter/open-lighter-order-api/)
- [Lighter account referral API](https://apis.io/collections/lighter/open-lighter-referral-api/)
- [Lighter account root API](https://apis.io/collections/lighter/open-lighter-root-api/)
- [Lighter account tokenlist API](https://apis.io/collections/lighter/open-lighter-tokenlist-api/)
- [Lighter account transaction API](https://apis.io/collections/lighter/open-lighter-transaction-api/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Lighter Zklighter Overlay](https://apis.io/overlays/lighter/lighter-zklighter-overlay/)

#### Security (3)

Authentication, trust centre, and vulnerability disclosure.

- [Lighter Authentication](https://apis.io/security/lighter/lighter-authentication/)
- [Lighter Domain Security](https://apis.io/security/lighter/lighter-domain-security/)
- [Lighter Vulnerability Disclosure](https://apis.io/security/lighter/lighter-vulnerability-disclosure/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Lighter Plans](https://apis.io/plans/lighter/lighter-plans/)

#### Rate limits (1)

Published request limits.

- [Lighter Rate Limits](https://apis.io/rate-limits/lighter/lighter-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://lighter.xyz)
- [Documentation](https://docs.lighter.xyz/)
- [Getting started](https://apidocs.lighter.xyz/docs/get-started)
- [API reference](https://apidocs.lighter.xyz/reference/systemconfig)
- [Pricing](https://docs.lighter.xyz/trading/trading-fees)
- [Sign up](https://app.lighter.xyz/)
- [Support](https://discord.gg/lighterxyz)
- [Blog](https://lighter.xyz/blog)
- [Security](https://docs.lighter.xyz/security/security-vulnerability-disclosure-policy)
- [Terms of service](https://lighter.xyz/terms)
- [GitHub](https://github.com/elliottech)
- [Status](https://status.lighter.xyz/)

## API Evangelist rating

**Kin Score 51.0** — developing · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 51.9 |
| Contract governance | 4.5 |
| Operational transparency | 52.6 |
| Developer ergonomics | 60.1 |
| Access clarity | 52.6 |

**Agent readiness 32.8** — agent-ready

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | — |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | documented (partial credit) |
| Error Semantics | verified |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | derived (partial credit) |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | paginated |
| Operation Distinctiveness | distinct |

**Regulatory alignment 30.6** — Securities & Market Data

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/lighter/](https://apis.io/providers/lighter/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for Lighter: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/lighter/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
