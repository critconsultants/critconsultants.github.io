# CR IT Consultants, LLC — Company Website

Static single-page site for CR IT Consultants, hosted on GitHub Pages with a
custom domain registered at GoDaddy. No build step — `index.html` is the whole site.

## Before going live

- [ ] Optional: add a business phone number to the Contact section of `index.html`
      once one is set up (Google Voice, Teams Phone, etc.).

## Deploy to GitHub Pages

1. The site lives at https://github.com/critconsultants/critconsultants.github.io —
   as the org's `.github.io` repo, GitHub Pages publishes it from `main` automatically.
2. If Pages settings ever need adjusting: **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main`, folder `/ (root)`.
3. Still in the Pages settings, enter the custom domain: `www.critconsultants.net`.
   GitHub commits a `CNAME` file to the repo.
4. After DNS propagates (below), check **Enforce HTTPS**.

## GoDaddy DNS (do NOT use "Domain Forwarding")

In GoDaddy → My Products → your domain → **DNS / Manage Zones**, add these records
**alongside** the existing Office 365 records:

| Type  | Name | Value                     |
|-------|------|---------------------------|
| A     | @    | 185.199.108.153           |
| A     | @    | 185.199.109.153           |
| A     | @    | 185.199.110.153           |
| A     | @    | 185.199.111.153           |
| CNAME | www  | `critconsultants.github.io` |

> Verify the A-record IPs against GitHub's current docs:
> https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site

**Do not touch** the existing MX, TXT/SPF, or `autodiscover` CNAME records —
those are what keep Office 365 email working.

## Updating the site

Edit `index.html`, commit, push. GitHub Pages redeploys automatically within a minute or two.
