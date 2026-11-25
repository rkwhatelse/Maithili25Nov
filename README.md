# Shakti Energy Reset – Landing Page (Maithili Janye)

Static one-page site. No build step: `index.html` + `assets/`.

## Before going live – edit `index.html`
Scroll to the bottom → `CONFIG`:
- `date` – e.g. `"21–22 NOV 2026"`
- `time` – e.g. `"11:00 AM IST"`
- `paymentLink` – already set to the TagMango page (every button uses it)

Also replace the coach-bio placeholders: `[15 years]`, `[50+ books]`, `[8–10]`.

## Images
| File | Where it shows |
|---|---|
| `assets/coach-hero.jpg` | Hero photo |
| `assets/prana-report.jpg` | Prana Energy Diagnosis |
| `assets/coach-guide.jpg` | "A Guide Who Has Walked This Path" |
| `assets/testimonial-1.mp4`, `testimonial-2.mp4`, `mamata.jpg` | Success stories |
| `favicon.ico`, `assets/*icon*.png` | Browser tab / home-screen icon |
| `assets/og-image.jpg` | Preview image when the link is shared on WhatsApp / Facebook |

## Publish free on GitHub Pages
1. github.com → **New repository** → name it e.g. `shakti-energy-reset` → **Public** → Create.
2. **Add file → Upload files** → drag in `index.html`, `.nojekyll`, `README.md` **and the `assets` folder** → Commit.
3. **Settings → Pages** → Source: *Deploy from a branch* → Branch: `main` / `(root)` → Save.
4. In 1–2 minutes your site is live at `https://<your-username>.github.io/shakti-energy-reset/`

To update later: upload the changed file(s) again → Commit. The site refreshes in a minute or two.

## Tracking
Meta Pixel 1713339420211886: `PageView` on load, `InitiateCheckout` (₹69 INR) on every Register / Reserve button click.
