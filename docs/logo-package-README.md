# Elmhurst Medical — Logo & Brand Asset Package

Everything a developer needs to implement the Elmhurst Medical identity on web.
All SVGs have the wordmark font (Bricolage Grotesque) **embedded as base64** — they render
identically everywhere with no font dependency and no external requests.

---

## 1. Folder contents

```
logo/       Master vector logos (SVG) — use these wherever possible
png/        Raster fallbacks, transparent background, 512 / 1024 / 2048px
favicon/    Browser tab, home-screen, and PWA icons + site.webmanifest
social/     Open Graph share card + square profile avatar
```

### logo/
| File | When to use |
|---|---|
| `elmhurst-logo-primary.svg` | **Default.** Jade seal on the cream field. Header, footer, letterhead. |
| `elmhurst-logo-transparent.svg` | No filled disc. Use over photography or any non-cream background. |
| `elmhurst-logo-reversed.svg` | Cream mark on a jade field. Dark sections, hero overlays. |
| `elmhurst-logo-1color-jade.svg` | Single ink. Stamps, embroidery, engraving, fax/photocopy. Rarely needed on web. |

### favicon/
| File | Purpose |
|---|---|
| `favicon.ico` | Legacy browsers (contains 16 / 32 / 48px) |
| `favicon.svg` | Modern browsers — scales cleanly, tiny file |
| `bloom-16/32/48.png` | PNG fallbacks |
| `bloom-180.png` | `apple-touch-icon` (iOS home screen) |
| `bloom-192.png`, `bloom-512.png` | Android / PWA |
| `icon-512-maskable.png` | Android adaptive icon — bloom inset inside the safe zone |
| `site.webmanifest` | PWA manifest, pre-filled |

### social/
| File | Purpose |
|---|---|
| `og-image-1200x630.png` | Open Graph / Twitter share card |
| `profile-avatar-1000.png` | Google Business, Instagram, Facebook profile photo |

---

## 2. Critical implementation rule

**The full seal is NOT the favicon.** The ring text ("ELMHURST MEDICAL") turns to
illegible mush below roughly 48px. The `favicon/` folder therefore uses the bare
marigold bloom — no ring, no text. Do not substitute the seal there.

- Seal (with ring text): **48px and up**
- Bloom only: **anything smaller**

---

## 3. Paste-in `<head>` snippet

Assumes assets are served from `/favicon/` and `/social/`. Adjust paths to match the build.

```html
<link rel="icon" href="/favicon/favicon.ico" sizes="any">
<link rel="icon" href="/favicon/favicon.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="/favicon/bloom-180.png">
<link rel="manifest" href="/favicon/site.webmanifest">
<meta name="theme-color" content="#0F7A6B">

<!-- Open Graph -->
<meta property="og:type" content="website">
<meta property="og:site_name" content="Elmhurst Medical">
<meta property="og:title" content="Elmhurst Medical — Primary &amp; Urgent Care in Queens">
<meta property="og:description" content="Same-week appointments. All insurances accepted. Open Mon–Sat, 10am–7:30pm in Elmhurst, Queens.">
<meta property="og:url" content="https://elmhurstmedical.com/">
<meta property="og:image" content="https://elmhurstmedical.com/social/og-image-1200x630.png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta name="twitter:card" content="summary_large_image">
```

Note: `og:image` must be an **absolute URL** or most platforms will silently skip it.

---

## 4. Brand tokens (CSS)

```css
:root {
  /* Core palette — "Sunrise over Jade" */
  --em-marigold:      #F4A81D;
  --em-marigold-deep: #BE7A08;
  --em-jade:          #0F7A6B;
  --em-coral:         #F0685C;
  --em-forest:        #123F33;
  --em-cream:         #FBF4E8;
  --em-espresso:      #221F1B;

  /* Typography */
  --em-font-display: 'Bricolage Grotesque', system-ui, sans-serif;
  --em-font-body:    'Plus Jakarta Sans', system-ui, sans-serif;
  --em-font-accent:  'Fraunces', Georgia, serif;   /* italic only */
  --em-font-bengali: 'Noto Sans Bengali', sans-serif;
}
```

Web fonts (Google Fonts):

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:opsz,wght@12..96,200..800&family=Plus+Jakarta+Sans:ital,wght@0,200..800;1,200..800&family=Fraunces:ital,opsz,wght@1,9..144,100..900&family=Noto+Sans+Bengali:wght@100..900&display=swap" rel="stylesheet">
```

---

## 5. Logo usage rules

**Clear space.** Keep empty space around the seal equal to at least **12% of its
diameter** on all sides. Nothing — text, buttons, image edges, borders — inside that ring.

**Minimum size on screen.** 48px diameter. Below that, swap to the bloom-only mark.

**Do not:**
- Stretch, squash, or rotate the seal
- Recolor the ring or wordmark outside the palette above
- Add drop shadows, outer glows, strokes, or bevels
- Place the transparent version over a busy area of a photo — use the reversed version on a solid jade panel instead
- Re-typeset the ring text; the wordmark is part of the vector artwork

**Accessibility.** Jade `#0F7A6B` on cream `#FBF4E8` passes WCAG AA for normal text.
Marigold `#F4A81D` does **not** pass on cream — never use marigold for body text
or small UI labels, only as a fill in artwork and large decorative shapes.

---

## 6. Implementation tips

- Prefer the SVG over PNG everywhere — it is sharp on every display and typically
  smaller than the 512px PNG.
- Inline SVG is fine, but if you inline more than one logo variant on the same page,
  note they already use unique internal element IDs, so they will not collide.
- Give every logo an accessible name: `<img src="..." alt="Elmhurst Medical">`, or
  for decorative repeats use `alt=""`.
- Serve the assets from a path with long cache headers; they are immutable.

---

## 7. Open items to confirm before launch

- Verify the OG description copy matches whatever the final homepage messaging says.
- If a dedicated online booking page is created, update any logo-linked CTAs to point there.
