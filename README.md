# Getting Paid in Nepal

Static, framework-free affiliate/informational site for Nepali freelancers and
IT exporters on how to legally receive USD from Upwork, Fiverr, and direct
international clients. Track-2 owned asset for MyAgentOrganization.

## How it works

- **Plain static HTML + one CSS file.** No build step, no framework, no
  JavaScript dependency. Every `.html` file is a complete, standalone page —
  open any file in a browser and it renders correctly (all links/assets use
  relative paths, so it also works correctly under a GitHub Pages *project*
  subpath like `/getting-paid-nepal/`, not just at a domain root).
- **`style.css`** holds all design tokens (CSS custom properties: colors,
  spacing, type scale) at the top, then components (header, affiliate banner,
  disclaimer/note/disclosure boxes, cards, table, footer), then a single
  mobile breakpoint. Change a token once to re-theme the whole site.
- **Shared header/footer** are duplicated by hand at the top/bottom of every
  page (no templating engine, by design — see Build constraint below). If you
  edit the nav or footer, you currently have to edit it in all 11 `.html`
  files. This is the accepted tradeoff for a zero-build static site; if the
  page count grows much further, consider a static-site generator (11ty,
  Hugo) as a v2 migration, not now.
- **Affiliate links are placeholders.** Every Payoneer call-to-action uses the
  literal placeholder `[PAYONEER-AFFILIATE-LINK]` as its `href`. **These are
  not live links.** Before this site is promoted/monetized, replace every
  occurrence with the real Payoneer referral URL once Sanjay's Payoneer
  affiliate/referral program approval is in hand:
  ```
  grep -rl "\[PAYONEER-AFFILIATE-LINK\]" *.html
  ```
  Find-and-replace that exact string across all matching files.
- **Premium product checkout link is also a placeholder.** `premium.html`'s
  "Buy the PDF — $9" button uses the literal placeholder
  `[PADDLE-CHECKOUT-LINK]` as its `href`. Replace it with the real Paddle
  checkout URL once the `$9` "Getting Paid in Nepal — Complete PDF Edition"
  product/price is live in the Paddle catalog (must match the $9 shown on the
  page). `grep -rl "\[PADDLE-CHECKOUT-LINK\]" *.html` to find it.
- **v1.1 (this patch):** contact email is now live
  (`sanjayamaharjan.codes@gmail.com`, Sanjay-approved), and three pages were
  added: `refund-policy.html` (14-day no-questions-asked refund on the paid
  PDF, processed via Paddle) and `premium.html` (the $9 PDF product page).
  The actual PDF product — source HTML + rendered PDF — is **not** in this
  repo. It lives at `D:/Lab/assets/getting-paid-nepal-premium/` in its own
  git repo with **no public remote**, so the paid deliverable isn't sitting
  in a public GitHub repo next to the free site.
- **No Wise page/link.** The original spec included a Wise guide, but Wise
  does not currently support Nepal-resident receiving accounts, so a
  dedicated Wise guide (and any Wise affiliate link) would be inaccurate.
  Wise is mentioned only as a "does not work for receiving" note on the home
  and comparison pages. If Wise adds Nepal-resident receiving support in the
  future, add a guide page then — don't undo this decision without checking.
- **Content honesty discipline.** Nepal-specific regulatory/tax claims (the
  ~5% presumptive tax figure, the ~50% IT-export exemption, the bank
  classification/FIRC content) are deliberately hedged, not stated as settled
  fact — they trace to the org's own research
  (`memory/episodic/2026/06/02-nepal-bank-usd-remittance-research.md`,
  `06/27-export-usd-firc-product-legal-scope.md`,
  `06/29-scan-*-budget/circular*.md` in the org-memory repo, not shipped
  here), which itself carries conf:medium/low tags due to a standing 403
  wall on primary NRB/IRD PDFs. Do not "clean up" the hedging language to
  make it read more confidently — that is the point, not a rough draft.

## Updating content

Every content page has a `<span class="freshness-stamp">Last reviewed: ...`
near the top — update it when you materially revise a page. There is no CMS;
edit the `.html` files directly.

## SEO basics already in place (for Growth to iterate on)

- Per-page `<title>` and `<meta name="description">`.
- `<link rel="canonical">` on every page (absolute URLs).
- `sitemap.xml` (submit to Google Search Console / Bing Webmaster Tools —
  not done automatically by this build) and `robots.txt`.
- Mobile-friendly (responsive `<meta name="viewport">`, CSS breakpoint,
  fluid card grid).
- No JS blocking render; no web fonts; fast by default.

Not included (intentionally, to avoid scope creep beyond the spec): JSON-LD
schema markup, analytics/tracking script. Add analytics only
with a privacy-respecting tool and update `privacy-policy.html` accordingly
if you do.

## Deployment

Hosted on GitHub Pages, served from the repo root of the `main` branch
(legacy Pages build, no Jekyll processing needed — plain HTML/CSS only, so
add a `.nojekyll` file if Pages ever mis-serves an underscore-prefixed
path; not currently needed since no filenames start with `_`).

Custom domain: `gettingpaid.scaleturn.com` (via a `CNAME` file at the repo
root + DNS `CNAME` record pointing at `sanjayamaharjancodes.github.io`,
configured through the GitHub Pages settings API). Because a custom domain
serves from the domain root rather than a `/getting-paid-nepal/` subpath,
every internal link/asset reference must stay relative (no leading `/`) —
already true of this build, verified after migration.

Live URL: https://gettingpaid.scaleturn.com/
