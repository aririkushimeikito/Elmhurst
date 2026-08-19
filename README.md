# Elmhurst Medical — elmhurstmedical.com

Static website for **Elmhurst Medical — Primary & Walk-In Urgent Care**,
40-16 74th Street, Elmhurst, NY 11373 · (718) 682-7090.

Live preview (GitHub Pages): **https://aririkushimeikito.github.io/Elmhurst/**

## What's here

- **43 public pages** — plain HTML5, no framework, no build step. Each page is self-contained
  (inline CSS; branded photos embedded as data URIs, stock photography served from `images/`
  as optimized WebP, ~26 KB average).
- **Core pages:** `index.html`, `services.html`, `providers.html`, `insurance.html`,
  `contact.html`, `booking.html`, `blog.html`, plus 3 provider profiles.
- **Blog / guides:** 33 article pages, all linked from `blog.html` (English, Spanish, Bengali).
- **SEO:** every page has title, meta description, keywords, canonical URL, Open Graph + Twitter
  cards, geo meta and JSON-LD structured data (`MedicalClinic`, `MedicalWebPage`, `BlogPosting`,
  `FAQPage`, `Physician`, `BreadcrumbList`). Site-level: `sitemap.xml` (43 URLs), `robots.txt`
  (all major AI/answer-engine crawlers explicitly allowed), `llms.txt`, branded `404.html`,
  favicons in `brand-assets/`.
- **Booking:** `booking.html` — Zocdoc online booking, phone, SMS and WhatsApp, walk-in hours,
  what to bring, FAQ (with `FAQPage` + `ScheduleAction` schema). Linked from the nav, footer and
  every "Book a visit" CTA site-wide.
- **Responsive:** mobile-first, hamburger menu under 940px, verified at 375 / 768 / 1024 / 1440 px
  with no horizontal scroll.
- Internal links are **relative**, so the site works at the domain root *and* under a subpath
  (GitHub Pages preview).

## Design system

Modern layout refresh (Aug 2026): hero with arched photo and floating badge chips, angled trust
marquee, mission collage with stats, photo-driven service and blog cards, forest stats band, and
a consistent inline SVG icon set (stroke style, brand colors) replacing emoji icons. Brand fonts
(Bricolage Grotesque / Plus Jakarta Sans / Fraunces) and the brand palette are unchanged.

## Deployment

`.github/workflows/pages.yml` deploys the repo to GitHub Pages on every push to `main`.

## Going live on elmhurstmedical.com (GoDaddy)

The domain currently runs WordPress on GoDaddy; email is Microsoft 365. All canonical URLs,
sitemap, robots and structured data in this repo already point to `https://elmhurstmedical.com/`,
so no code change is needed at cutover:

1. Upload the repo's HTML files plus `og-image.jpg`, `sitemap.xml`, `robots.txt`, `llms.txt`,
   `404.html` and `brand-assets/` into `public_html` on the GoDaddy hosting (so `index.html` is at
   the web root) — or point DNS at any static host.
2. **Change only the website DNS records** (A record for `@`, CNAME for `www`). Leave every
   MX / SPF / DKIM / autodiscover record untouched so Microsoft 365 email keeps working.
3. Enable HTTPS (Let's Encrypt / host SSL).
4. In Google Search Console, verify the domain and submit `https://elmhurstmedical.com/sitemap.xml`.
5. Create/claim the Google Business Profile and link it to the site for local rankings.

## Reference docs

- `docs/HANDOFF.md` — original developer handoff notes
- `docs/Elmhurst-Medical-Brand-Guidelines.pdf` — brand colors, fonts, logo usage
- `brand-guidelines.html` — internal brand reference page (noindexed)
