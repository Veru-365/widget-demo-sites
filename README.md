# Veru365 Widget Demo Sites

Fake "client" marketing pages hosted on a **separate domain** (GitHub Pages) that embed the
Veru365 chat widget from staging — demonstrating that one reseller client can put the same
widget on their main website **and** multiple separate landing pages with a single script tag:

```html
<script src="https://ihf-frontend-staging-mr64uhwn4a-uc.a.run.app/widget.js"
        data-org="veru365"
        data-base="https://ihf-frontend-staging-mr64uhwn4a-uc.a.run.app" defer></script>
```

## Pages
- `acme-wealth/index.html` — the client's main website
- `acme-wealth/retirement-landing.html` — campaign landing page 1
- `acme-wealth/tax-landing.html` — campaign landing page 2

Because these pages are served from github.io (a genuinely different origin), this exercises
the real cross-origin path: the widget iframe relies on the `frame-ancestors *` exception
scoped to `/widget/*` on staging, and branding loads through the CORS-enabled
`/api/widget-branding` proxy.

**Demo scope only.** Production hardening (per-org domain allowlists for frame-ancestors/CORS,
real anonymous auth, rate limiting) is tracked in Veru-365/frontend#2013 follow-ups.
