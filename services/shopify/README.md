---
name: Shopify
slug: shopify
type: service
license: n/a
stars: n/a
last_verified: 2026-05-27
maintainer: shopify
related: [scoped-delegation-tokens]
---

# Shopify

Shopify custom apps issue an Admin API access token at install time. The token is shown once, so capture it directly into a vault. Online tokens (user session) and offline tokens (custom app) carry different lifetimes.

## Credential types

- **Custom app Admin API access token (offline)**: store-scoped, long-lived.
- **Online tokens**: tied to a user session.
- **Public app OAuth**: for marketplace apps.
- **Storefront tokens**: for client-side storefront calls.

## Recommended pattern

Custom app installed per store with read-only Admin API scopes. Capture the token at install (it appears once) directly into a vault. The agent reads from the vault on each task.

## Critical scopes to refuse

`write_orders`, `write_customers`, `write_inventory`, `write_files`, `write_themes` when `read_*` is sufficient.

## Rotation

Reinstall the app to mint a new token. Tokens are shown once; store immediately.

## Example

```bash
curl https://example.myshopify.com/admin/api/2026-04/products.json \
  -H "X-Shopify-Access-Token: shpat_..."
```

## Docs

- [Generate access tokens for custom apps](https://shopify.dev/docs/apps/build/authentication-authorization/access-tokens/generate-app-access-tokens-admin)

---

Curated by [Authsome](https://authsome.dev) · agent identity for third-party APIs.
