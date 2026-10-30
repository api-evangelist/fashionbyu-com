# IRIZ Platform

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

IRIZ Platform is the multi-brand, agent-first fashion storefront platform behind fashionbyu.com (brands such as BWET Swimwear, Me+Em, Kitri Studio, Lisou London and Réalisation Par are hosted as /brand/<slug> storefronts). It publishes a first-party OpenAPI 3.0.0 ("IRIZ Platform API", 108 operations, canonical base path /iriz/v1/) at https://mirror.fashionbyu.com/iriz/v1/docs/spec.json with a Swagger UI at /iriz/docs, a live hosted MCP server (iriz-agent-commerce, protocol 2025-06-18, nine tools: search_catalog, get_product_feed, get_policies, create_cart, mutate_cart, get_cart, quote_cart, confirm_checkout, get_order) whose tools/list answers unauthenticated, two A2A agent cards (a Storefront Commerce card at the canonical /.well-known/agent-card.json and a Platform Interop card at the legacy /.well-known/agent.json, both flavored: protocolVersions[] instead of protocolVersion), an llms.txt and an agent-welcoming robots.txt, and per-brand OpenAI/ACP-compatible product feeds (/brand/<slug>/feed.json) with schema.org Product JSON-LD. The platform runs on Cloudflare Workers (D1/KV/R2/queues/Durable Objects per /iriz/health); HTML pages sit behind a Cloudflare managed challenge while the JSON surfaces answer directly. The registrable domain fashionbyu.com serves the interop card, llms.txt and the brand feeds but 404s the MCP and REST routes, which live on mirror.fashionbyu.com; every link inside the provider's own llms.txt and robots.txt points at www.fashionbyu.com, which does not resolve (NXDOMAIN on 2026-09-19).

**Areas:** Company · Fashion · E-Commerce · Agentic Commerce · Storefront · Product Feeds · MCP · A2A · AI Agents · Checkout · Cart · Order

## IRIZ Platform on APIs.io

Everything profiled for IRIZ Platform is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/fashionbyu-com/](https://apis.io/providers/fashionbyu-com/)** — or go straight to one of the APIs or properties below.

### APIs (29)

- [IRIZ Storefront Commerce MCP Server](https://apis.io/apis/fashionbyu-com/iriz-storefront-commerce-mcp-server/) — Hosted, remote MCP server (serverInfo iriz-agent-commerce 1.0.0, protocolVersion 2025-06-18, transport streamable-http) at…
- [IRIZ Platform A2A Interop Agent](https://apis.io/apis/fashionbyu-com/iriz-platform-a2a-interop-agent/) — A2A agent card ("IRIZ Platform Agent", version 1.0.0, protocolVersions ["0.3","A2A-1.4"]) served at the legacy path…
- [IRIZ Platform About API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-about-api/) — The About API from IRIZ Platform — 1 operation(s) for about.
- [IRIZ Platform Account API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-account-api/) — The Account API from IRIZ Platform — 1 operation(s) for account.
- [IRIZ Platform Admin API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-admin-api/) — The Admin API from IRIZ Platform — 1 operation(s) for admin.
- [IRIZ Platform Agent Memory API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-agent-memory-api/) — The Agent Memory API from IRIZ Platform — 1 operation(s) for agent memory.
- [IRIZ Platform App Health API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-app-health-api/) — The App Health API from IRIZ Platform — 1 operation(s) for app health.
- [IRIZ Platform Boss Agent API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-boss-agent-api/) — The Boss Agent API from IRIZ Platform — 1 operation(s) for boss agent.
- [IRIZ Platform Boss API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-boss-api/) — The Boss API from IRIZ Platform — 1 operation(s) for boss.
- [IRIZ Platform Boss App API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-boss-app-api/) — The Boss App API from IRIZ Platform — 1 operation(s) for boss app.
- [IRIZ Platform Boss Ws API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-boss-ws-api/) — The Boss Ws API from IRIZ Platform — 1 operation(s) for boss ws.
- [IRIZ Platform Cart API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-cart-api/) — The Cart API from IRIZ Platform — 1 operation(s) for cart.
- [IRIZ Platform Chat API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-chat-api/) — The Chat API from IRIZ Platform — 3 operation(s) for chat.
- [IRIZ Platform Debug API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-debug-api/) — The Debug API from IRIZ Platform — 3 operation(s) for debug.
- [IRIZ Platform Discover API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-discover-api/) — The Discover API from IRIZ Platform — 1 operation(s) for discover.
- [IRIZ Platform Healer API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-healer-api/) — The Healer API from IRIZ Platform — 5 operation(s) for healer.
- [IRIZ Platform Health API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-health-api/) — The Health API from IRIZ Platform — 1 operation(s) for health.
- [IRIZ Platform Herald API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-herald-api/) — The Herald API from IRIZ Platform — 7 operation(s) for herald.
- [IRIZ Platform Intake API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-intake-api/) — The Intake API from IRIZ Platform — 1 operation(s) for intake.
- [IRIZ Platform Iris Deploy API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-iris-deploy-api/) — The Iris Deploy API from IRIZ Platform — 1 operation(s) for iris deploy.
- [IRIZ Platform Iris Source API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-iris-source-api/) — The Iris Source API from IRIZ Platform — 1 operation(s) for iris source.
- [IRIZ Platform Iriz API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-iriz-api/) — The Iriz API from IRIZ Platform — 56 operation(s) for iriz.
- [IRIZ Platform Manifest.json API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-manifest-json-api/) — The Manifest.json API from IRIZ Platform — 1 operation(s) for manifest.json.
- [IRIZ Platform MCP API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-mcp-api/) — The Mcp API from IRIZ Platform — 1 operation(s) for mcp.
- [IRIZ Platform Robots.txt API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-robots-txt-api/) — The Robots.txt API from IRIZ Platform — 1 operation(s) for robots.txt.
- [IRIZ Platform Scribe API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-scribe-api/) — The Scribe API from IRIZ Platform — 4 operation(s) for scribe.
- [IRIZ Platform Sentinel API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-sentinel-api/) — The Sentinel API from IRIZ Platform — 4 operation(s) for sentinel.
- [IRIZ Platform Status API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-status-api/) — The Status API from IRIZ Platform — 1 operation(s) for status.
- [IRIZ Platform Vigil API](https://apis.io/apis/fashionbyu-com/fashionbyu-com-vigil-api/) — The Vigil API from IRIZ Platform — 7 operation(s) for vigil.

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [iriz-agent-commerce](https://apis.io/servers/fashionbyu-com/iriz-agent-commerce/)

#### Agentic access (1)

Which operations an agent can call, which act, and which need a human in the loop.

- [Fashionbyu Com Agentic Access](https://apis.io/agentic-access/fashionbyu-com/fashionbyu-com-agentic-access/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Fashionbyu Com Iriz Platform Api Overlay](https://apis.io/overlays/fashionbyu-com/fashionbyu-com-iriz-platform-api-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Fashionbyu Com Authentication](https://apis.io/security/fashionbyu-com/fashionbyu-com-authentication/)
- [Fashionbyu Com Domain Security](https://apis.io/security/fashionbyu-com/fashionbyu-com-domain-security/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Fashionbyu Com Plans Pricing](https://apis.io/plans/fashionbyu-com/fashionbyu-com-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Fashionbyu Com Rate Limits](https://apis.io/rate-limits/fashionbyu-com/fashionbyu-com-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://fashionbyu.com/)
- [Documentation](https://mirror.fashionbyu.com/iriz/docs)

## API Evangelist rating

**Kin Score 24.0** — emerging · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 71.7 |
| Contract quality | 35.6 |
| Contract governance | 18.2 |
| Operational transparency | 7.9 |
| Developer ergonomics | 30.4 |
| Access clarity | 0.0 |

**Agent readiness 27.9** — agent-aware

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | derived (partial credit) |
| Reversibility Documented | — |
| MCP Server | documented (partial credit) |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | derived (partial credit) |
| OpenAPI Examples | — |
| Rate Limit Signal | documented (partial credit) |
| Event Surface Described | — |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | flavored (partial credit) |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | na |
| Operation Distinctiveness | distinct |

**Regulatory alignment 15.2** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/fashionbyu-com/](https://apis.io/providers/fashionbyu-com/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for IRIZ Platform: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/fashionbyu-com/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).
