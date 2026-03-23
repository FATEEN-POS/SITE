# Security Policy

**Fateen Digital Solutions — فطين ديجيتال سليوشنز**

---

## Scope

This policy covers the landing page (`index.html`) and any associated assets hosted under the Fateen Digital Solutions domain.

---

## Known Security Considerations

### 1. Email Obfuscation (Cloudflare)
Email addresses are protected via Cloudflare's email obfuscation (`/cdn-cgi/l/email-protection`).
- **Requires:** Cloudflare proxy to be active — do not serve the page without it or real email addresses will be exposed in plain HTML.
- **Do not** hardcode raw email addresses in any HTML attribute or JS string.

### 2. External Scripts
The page loads from two external CDNs:

| Source | Resource |
|---|---|
| `fonts.googleapis.com` | Tajawal & Playfair Display fonts |
| `/cdn-cgi/scripts/...` | Cloudflare email decode script |

- Do not add additional third-party scripts without review.
- Consider adding a **Content Security Policy (CSP)** header at the server/CDN level.

### 3. No Backend / No Form Submissions
The contact form is modal-only and routes to WhatsApp and email — there is no server-side form handler. No user input is stored or transmitted through the page itself.

### 4. `alert()` Usage
Two `alert()` calls are used as placeholders for the Facebook link (coming soon). Replace these before any production expansion to avoid poor UX and potential phishing confusion.

### 5. Logo Asset Path
The logo (`لوجو فطين اسود.png`) uses an Arabic filename. Ensure the web server and deployment pipeline handle Unicode filenames correctly. Use URL encoding if needed.

### 6. `target="_blank"` Links
External links (WhatsApp, demo) use `target="_blank"`. All should include `rel="noopener noreferrer"` to prevent tab-napping:

```html
<!-- Current -->
<a href="https://wa.me/..." target="_blank">

<!-- Secure -->
<a href="https://wa.me/..." target="_blank" rel="noopener noreferrer">
```

### 7. No HTTPS Enforcement in Code
HTTPS must be enforced at the Cloudflare/hosting level. Verify that HTTP → HTTPS redirect is active on the deployed domain.

---

## Recommended Headers (Cloudflare / Server)

```
Content-Security-Policy: default-src 'self'; font-src fonts.gstatic.com; style-src 'self' fonts.googleapis.com 'unsafe-inline'; script-src 'self' /cdn-cgi/;
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
```

---

## Reporting a Vulnerability

Contact directly via:

- **WhatsApp:** +20 127 392 9303
- **Email:** fateen.digitalsolutions@gmail.com

Please include a clear description of the issue and steps to reproduce. We aim to respond within **48 hours**.

---

## Out of Scope

- Social engineering attacks
- Issues requiring physical access to infrastructure
- Third-party services (WhatsApp, Google Fonts, Netlify, Cloudflare) — report those to the respective vendors
