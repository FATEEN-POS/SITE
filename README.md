# Fateen Digital Solutions — Landing Page

**فطين ديجيتال سليوشنز | index.html**

Landing page for Fateen Digital Solutions, a tech company based in Aswan, Egypt, specializing in AI-powered POS, sales, and accounting systems for the Egyptian retail market.

---

## Overview

Single-file HTML landing page (RTL, Arabic). No build tools or dependencies — open `index.html` directly in any browser.

**Live demo:** [fateen-os.netlify.app](https://fateen-os.netlify.app)

---

## Structure

| Section | ID / Class | Description |
|---|---|---|
| Navbar | `nav` | Fixed top bar with logo and CTA button |
| Hero | `#hero` | Full-screen intro with animated logo |
| Services | `#services` | 4-card grid (POS, Websites, Design, Hotel Reservations) |
| POS Detail | `#pos-detail` | Feature breakdown for the smart cashier system |
| Web Detail | `#web-detail` | Website service features |
| Vision | `#vision` | Company vision + key stats |
| About | `#about` | Company description |
| Contact | `#contact` | WhatsApp, email, Facebook cards |
| Footer | `footer` | Copyright |
| Modal | `#modal` | Contact modal overlay |

---

## Assets

| File | Usage |
|---|---|
| `لوجو فطين اسود.png` | Logo used in hero and footer — must be in same directory as `index.html` |

> If the logo file is missing, a text fallback (`FATEEN`) is shown automatically via `onerror`.

---

## Fonts (Google Fonts CDN)

- **Tajawal** — primary Arabic UI font (weights 300–900)
- **Playfair Display** — display/heading serif font

---

## CSS Variables

Defined in `:root`:

```css
--black:     #080808   /* page background */
--white:     #f5f0e8   /* heading text */
--gold:      #c9a84c   /* primary brand color */
--gold-light:#e8cc7a   /* hover state */
--gold-dim:  rgba(201,168,76,0.12)  /* card backgrounds */
--gold-line: rgba(201,168,76,0.3)   /* borders/dividers */
--gray:      #1a1a1a
--gray2:     #242424
--muted:     #888      /* secondary text */
--text:      #e8e0d0   /* body text */
```

---

## JavaScript

All JS is inline at the bottom of `index.html`:

- `openModal()` / `closeModal()` — contact modal toggle
- `Escape` key closes modal
- `IntersectionObserver` — triggers `.visible` class on `.fade-up` elements for scroll animations

---

## Services Status

| # | Service | Status |
|---|---|---|
| 01 | نظام المبيعات الذكي (POS) | ✅ Live |
| 02 | إنشاء المواقع الإلكترونية | ✅ Live |
| 03 | خدمة الديزاين | 🔜 Coming soon |
| 04 | نظام الحجوزات للفنادق | 🔜 Coming soon |

---

## Contact

- **WhatsApp:** +20 127 392 9303
- **Email:** configured via Cloudflare email obfuscation
- **Facebook:** coming soon

---

## Notes

- Email links use **Cloudflare email protection** (`/cdn-cgi/...`) — requires Cloudflare proxy to decode correctly in production.
- Page is fully RTL (`dir="rtl"`, `lang="ar"`).
- No frameworks, no bundlers — pure HTML/CSS/JS.
