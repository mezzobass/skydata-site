# skydata-site

Personal landing page for Mark Biesterfeld, served at https://skydata.one.

Single static HTML file. Deployed to Vercel from this repo on push to `main`.

## Architecture

| Component | Provider |
|---|---|
| Domain registrar | Squarespace Domains (managed via Google Workspace admin) |
| DNS | Google Cloud DNS |
| Website host | Vercel (project `skydata-site`) |
| Email (info@skydata.one) | Google Workspace — independent of website hosting |

## DNS records

Managed in the Squarespace DNS panel (reached via admin.google.com → Domains → Manage Domain → SSO into Squarespace):

| Type | Name | Data |
|---|---|---|
| A | `@` | `216.198.79.1` |
| CNAME | `www` | `cname.vercel-dns.com` |
| MX (×5) | `@` | Google Workspace (`aspmx.l.google.com` + alts) |
| TXT | `@` | `v=spf1 include:_spf.google.com ~all` |
| TXT | `google._domainkey` | DKIM key |

## Editing

Edit `index.html`, commit, push to `main`. Vercel auto-deploys.
