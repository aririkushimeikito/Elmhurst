# Elmhurst Medical — Website Developer Handoff

This package contains the complete, finished website for **elmhurstmedical.com**, ready to deploy.

- **`/site/`** — the entire website (42 pages + assets). This is what gets published.
- **`/brand-assets/`** — logo (SVG + PNG), flower mark, favicon sizes, and provider headshots.
- **`Elmhurst-Medical-Brand-Guidelines.pdf`** — colors, fonts, logo usage, voice.

---

## What this is (tech overview)

- **Plain static HTML5.** No framework, no build step, no database, no server code. Every page is a
  self-contained `.html` file with its CSS in an inline `<style>` block.
- **Images are embedded** as base64 data-URIs inside the HTML (photos, logos, illustrations), so there
  are almost no separate image files to manage. Exceptions: `og-image.jpg` (social share image) and two
  external embeds — **Google Fonts** and a **Google Maps iframe** on `contact.html`.
- **Fonts** (loaded from Google Fonts): Bricolage Grotesque (headings), Plus Jakarta Sans (body),
  Fraunces (italic accents), Hanken Grotesk (wordmark), Noto Sans Bengali (Bengali text).
- **Fully responsive**, mobile-first, with a hamburger menu under 940px. No horizontal scroll at any width.

## Deploy it

It's a static site — host it anywhere and point the domain at it:

- **Any static host** (Cloudflare Pages, Netlify, Vercel, GitHub Pages, S3): upload the contents of
  `/site/` so `index.html` is at the web root.
- **cPanel / traditional hosting**: upload the contents of `/site/` into `public_html`.
- `index.html` is the homepage. Links are **root-relative** (e.g. `/services.html`), so the site must be
  served from the domain root, not a subfolder.
- HTTPS: use the host's automatic SSL (Let's Encrypt on Netlify/Cloudflare).
- **Note on the current domain:** elmhurstmedical.com currently runs WordPress on GoDaddy, and email is
  Microsoft 365. To go live without breaking email, keep DNS at GoDaddy and change **only** the website
  records (A record for `@`, CNAME for `www`) to the new host — leave all MX / SPF / DKIM / autodiscover
  records untouched.

## Page structure

- **Core:** `index.html` (home), `services.html`, `providers.html`, `insurance.html`, `contact.html`, `blog.html`
- **Provider profiles:** `dr-choudhury-hasan.html`, `dr-ferdous-salauddin.html`, `keerthana-rajagopal.html`
- **Blog / guides:** ~30 article pages (`blog-*.html` and keyword-slug pages like
  `what-is-glp-1-medication.html`, `health-screenings-by-age.html`, etc.)
- **`sitemap.xml`**, **`robots.txt`**, **`og-image.jpg`**

## Editing notes for the developer

- **Repeated components** (nav bar and footer) are duplicated on every page. If you change the nav/footer,
  change it on all pages (a simple find-and-replace across `/site/*.html`, or move to includes/a templating
  system if you migrate the site).
- **SEO is already built in** on every page: `<title>`, meta description, `<meta name="keywords">`, canonical
  URL, Open Graph + Twitter cards, geo meta, and JSON-LD structured data
  (`MedicalClinic`, `MedicalWebPage`, `BlogPosting`, `FAQPage`, `Physician`/`ProfilePage`, `BreadcrumbList`).
  All 42 pages are listed in `sitemap.xml`. Please preserve these if you refactor.
- **Booking / contact wiring:** phone `tel:+17186827090`, WhatsApp `https://wa.me/17186827090`, email
  `office@elmhurstmedical.com`, and the Zocdoc profile link
  `https://www.zocdoc.com/practice/elmhurst-medical-68107?...` (appears on booking buttons site-wide).
- **Contact map:** `contact.html` embeds a Google Maps iframe for 40-16 74th Street, Elmhurst, NY 11373.

## Brand quick reference

- Colors: Marigold `#F4A81D` · Forest `#123F33` · Teal `#0F7A6B` · Coral `#E97A6D` · Cream `#FCF7EE`
  · Sand `#F3E9D7` · Sage `#E7EFE5` · Ink `#221E17`. Wordmark "MEDICAL" gold `#E5920E`.
- Logo files are in `/brand-assets/` (vector SVG flower + transparent PNG wordmarks, light & dark).
- Full rules are in the Brand Guidelines PDF.

## Clinic facts

Elmhurst Medical — Primary & Walk-In Urgent Care
40-16 74th Street, Elmhurst, NY 11373 · (718) 682-7090 · elmhurstmedical.com
Hours: Mon–Fri 10:00 AM–7:30 PM · Sat 2:30–7:30 PM · Closed Sunday
Languages: English, Spanish, Bengali, Hindi, Urdu

---
Questions about the design system or structure can be answered from the Brand Guidelines PDF and this file.
