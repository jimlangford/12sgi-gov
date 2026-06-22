# gov.12sgi.com redirect (no nameserver change needed)

Wix blocks pointing nameservers to Cloudflare on this plan. We don't need them moved for `gov` — it just
redirects to the apex govOS (`12sgi.com`). This is a tiny GitHub Pages site that does that, with free
HTTPS, while DNS STAYS at Wix.

## Files
- `index.html` - 301-style client redirect to https://12sgi.com (preserves path + query)
- `CNAME` - tells GitHub Pages this site's custom domain is `gov.12sgi.com`

## One-time setup (owner steps)
1. **GitHub:** create a new public repo `jimlangford/12sgi-gov` -> upload these 3 files (or `git push`).
   Settings -> Pages -> Source = `main` / root. (The `CNAME` file sets the custom domain automatically.)
2. **Wix DNS** (allowed even though nameserver change isn't): add a record
   `Type CNAME | Host gov | Value jimlangford.github.io` (TTL default).
3. Wait for GitHub to provision the cert (Settings -> Pages shows "DNS check successful" then HTTPS).
4. Verify: open https://gov.12sgi.com -> lands on the govOS at 12sgi.com.

No Cloudflare, no nameserver change. For the LATER full plan (live app./tenant. subdomains via tunnels)
the domain would need to transfer to Cloudflare Registrar - separate, optional step.
