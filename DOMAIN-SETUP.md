# Custom Domain Setup — memorablebottles.com

Status as of 2026-06-08: **memorablebottles.com is NOT registered yet** (DNS returns NXDOMAIN).
Current live URL: https://qbstabletampa-creator.github.io/memorable-bottles/

## Step 1 — Register the domain
Grab `memorablebottles.com` at any registrar (Namecheap, Cloudflare, Porkbun, GoDaddy). ~$12/yr.
Cloudflare or Porkbun are cheapest with no upsell. Tell Claude which registrar after.

## Step 2 — DNS records (add at the registrar)
For an apex domain (memorablebottles.com) on GitHub Pages:

| Type | Name | Value |
|------|------|-------|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | qbstabletampa-creator.github.io |

(Optional IPv6 AAAA for @: 2606:50c0:8000::153, 2606:50c0:8001::153, 2606:50c0:8002::153, 2606:50c0:8003::153)

## Step 3 — Claude finishes it (2 min)
Once DNS is set, Claude will:
1. Add a `CNAME` file (containing `memorablebottles.com`) to the repo root and push.
2. Set the custom domain + "Enforce HTTPS" in the repo Pages settings (`gh api`).
3. Update the FormSubmit `_next` redirect in `intake.html` to the new domain.
4. Verify the live site + form on the new domain.

DNS propagation is usually 5-30 min. Do NOT add the CNAME file before DNS exists (it breaks the working github.io URL until DNS resolves).

## Notes
- Repo: `qbstabletampa-creator/memorable-bottles` (branch master, GitHub Pages).
- A subdomain instead (e.g. shop.memorablebottles.com) only needs ONE CNAME -> qbstabletampa-creator.github.io. Simpler if the apex is used elsewhere.
