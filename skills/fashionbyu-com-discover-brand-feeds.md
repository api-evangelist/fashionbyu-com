---
name: Discover a brand's machine-readable catalog, feed and policies
description: Read-only discovery of a hosted brand storefront — brand index, catalog search, ACP-compatible product feed, per-brand llms.txt and policy URLs. No credentials, no side effects.
api: openapi/fashionbyu-com-iriz-platform-api-openapi.yml
mcp: mcp/fashionbyu-com-mcp.yml
operations:
  - GET /iriz/v1/agent/catalog
tools: [search_catalog, get_product_feed, get_policies]
generated: '2026-09-19'
method: generated
---

# Discover a brand's catalog, feed and policies

Every URL below returned HTTP 200 on 2026-09-19 from `mirror.fashionbyu.com`. The same
`/brand/<slug>/feed.json` and `/brand/<slug>/llms.txt` paths also answer on `fashionbyu.com`;
the `/iriz/agent/*` routes do not.

## Steps

1. `GET /iriz/agent/brands` -> `{brand_count, brands:[{slug, name, storefront, feed, llms_txt}]}`.
2. `search_catalog` `{brand_slug, query?, limit, offset}` (or `GET /iriz/v1/agent/catalog?slug=`,
   `GET /iriz/agent/search?slug=&q=`). Each product carries `pdp_url`, `variants[]`,
   `agent_actions[]` and a schema.org `Product` JSON-LD string.
3. `get_product_feed` `{brand_slug, page_origin?}` returns the feed and llms.txt URLs:
   `GET /brand/<slug>/feed.json` is an `openai-product-feed/acp-compatible` document
   (`items[]` with price, availability, seller_privacy_policy, seller_tos, return_policy,
   enable_search, enable_checkout); `GET /brand/<slug>/llms.txt` is text/markdown.
4. `get_policies` `{brand_slug}` (or `GET /iriz/agent/policies?slug=`) returns shipping, delivery,
   returns, refund, privacy, terms and contact page URLs. Those pages are HTML behind a
   Cloudflare managed challenge — fetch them as a browser, not as a bare HTTP client.

## Notes

- Prices: the feed quotes GBP strings; the catalog quotes `price_cents` with `currency: USD`
  for the same products. Treat the catalog's `checkout_contract` as authoritative for checkout.
- Pagination is offset-based (`limit` default 24, max 48); there is no `has_more`.
