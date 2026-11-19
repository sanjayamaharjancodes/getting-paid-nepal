# Getting Paid in Nepal

Source of https://gettingpaid.scaleturn.com/, a free, plain-language guide for Nepali freelancers and IT exporters on
receiving money from Upwork, Fiverr and direct international clients, published by Scaleturn
(https://scaleturn.com/).

This README lives in `.github/` so the Pages build does not publish it; GitHub still shows it on the repository page.

## How it works

- **Plain static HTML and one CSS file.** No build step, no framework. The only scripts are the GoatCounter page
  counter and Google's AdSense code. All links and assets use relative paths.
- **AdSense code on every page except the privacy policy** (since 19 Nov 2026, task ct-004). Each page's `<head>`
  loads Google's AdSense auto-ads loader, byte for byte as on scaleturn.com (`adsbygoogle.js?client=ca-pub-5554189148912369`,
  async, just before `style.css`); copy it into any new page. Google places any ads itself once it approves the site.
  `privacy-policy.html` makes Google's advertising disclosures and loads no ad code: Google asks that privacy pages
  linked from its consent message host no ad tags (AdSense Help, answer 10961370). The `ads.txt` at scaleturn.com
  covers this subdomain.
- **`style.css`** holds design tokens at the top, then components (header, banner, disclaimer/note boxes, cards,
  table, footer), then one mobile breakpoint.
- **Shared header and footer are copied by hand** into every page. Edit all pages when either changes.
- **No active affiliate links.** The Payoneer call-to-action is a plain link. Do not add a referral claim until a real
  referral link exists and its terms have been checked.
- **Nothing for sale.** A paid PDF edition was offered here until November 2026 and retired after it made no
  sales. Its checkout, download and refund pages were removed; the guide is free.
- **No Wise guide.** Wise does not offer Nepal-resident receiving accounts, so it appears only as "not usable for
  receiving". Re-check before changing that.

## Content rules

- Every fee, rate and rule comes from a primary source (the platform's own help page, Payoneer's pricing page, the
  Inland Revenue Department or Nepal Rastra Bank), with the date it was read and a link. Worked examples use only those
  figures.
- Where no primary source has been found, the page says the figure is unconfirmed rather than printing it as fact.
- Each content page has a `<span class="freshness-stamp">`. Update it, and the page's `lastmod` in `sitemap.xml`,
  when you re-check or materially revise the page.

## SEO basics

- `<title>`, `<meta name="description">` and `<link rel="canonical">` on every page.
- `sitemap.xml` with `lastmod`, and `robots.txt`.
- Responsive viewport and a CSS breakpoint; no web fonts.

## Deployment

GitHub Pages serves the repository root of `main`, at the custom domain in `CNAME` (`gettingpaid.scaleturn.com`).
Keep internal links relative.
