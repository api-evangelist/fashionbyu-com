---
name: Shop a brand storefront and confirm checkout via MCP
description: Search a hosted brand catalog, build and quote a cart, confirm checkout and track the order using the IRIZ Storefront Commerce MCP server (nine tools, tools/list open). Grounded in the live tools/list of 2026-09-19 and the four backing REST operations in the OpenAPI.
api: openapi/fashionbyu-com-iriz-platform-api-openapi.yml
mcp: mcp/fashionbyu-com-mcp.yml
operations:
  - GET /iriz/v1/agent/catalog
  - POST /iriz/v1/agent/cart/session
  - POST /iriz/v1/agent/cart/quote
  - POST /iriz/v1/agent/checkout/confirm
tools: [search_catalog, create_cart, mutate_cart, get_cart, quote_cart, confirm_checkout, get_order]
generated: '2026-09-19'
method: generated
---

# Shop a brand storefront and confirm checkout

The OpenAPI declares no operationIds, so operations are named here by method + path. The
MCP tool inputSchema (mcp/fashionbyu-com-mcp-tools-list.json) is the only published request
contract — the OpenAPI has no requestBody or schemas.

## Endpoint

- MCP: `POST https://mirror.fashionbyu.com/iriz/v1/agent/mcp` (JSON-RPC, streamable-http).
  The legacy `/iriz/agent/mcp` still answers but returns `Deprecation: true`.
- Do not use `www.fashionbyu.com` (the host llms.txt advertises): it does not resolve.
- Read tools need no credentials. Write tools take `Authorization: Bearer <token>` only when
  the operator has configured `IRIZ_AGENT_COMMERCE_TOKEN`; the agent card says `token_required: false`.

## Steps

1. Pick a brand slug. `GET https://mirror.fashionbyu.com/iriz/agent/brands` lists them
   (`bwet` on the mirror host; the root-host llms.txt lists eight brands).
2. `search_catalog` `{brand_slug, query?, limit<=48, offset?}` — backed by
   `GET /iriz/v1/agent/catalog?slug=`. Read `products[].id`, `sku`, `variants[].sku`,
   `price_cents`, `currency`, `available`, and the `checkout_contract` route map.
3. `create_cart` `{brand_slug, items:[{product_id|sku, qty}], buyer_email?}` — backed by
   `POST /iriz/v1/agent/cart/session`. Keep the returned `cart_token`.
4. Adjust with `mutate_cart` `{cart_token, action: add|set|remove, items}`; verify with
   `get_cart` `{cart_token}`. `set` replaces and is safe to repeat; `add` is not.
5. `quote_cart` `{cart_token, shipping?}` — backed by `POST /iriz/v1/agent/cart/quote`.
   This PLACES AN INVENTORY HOLD; it is not a side-effect-free dry run. Keep `quote_id`.
6. `confirm_checkout` `{cart_token, quote_id, payment?, buyer_email}` — backed by
   `POST /iriz/v1/agent/checkout/confirm` ("demo or Stripe"). A `409 Quote mismatch`
   means the cart changed after the quote: re-run step 5, never retry blindly.
7. `get_order` `{order_id}` to track.

## Rules that apply

- No idempotency key exists (conventions: `idempotency.coverage: none`). Do not resend
  `confirm_checkout` on a timeout without first checking `get_order` / `get_cart`.
- No reversal operation exists (conventions: `reversibility: none`). Once confirmed, an order
  can only be undone through the brand's human returns/refund policy pages
  (`get_policies` returns their URLs). Confirm only with explicit user intent.
- Errors arrive as `{ok:false, error, code?}`; see errors/fashionbyu-com-problem-types.yml.
- No rate limits are documented or signalled; `limit` max 48 is a page size.
