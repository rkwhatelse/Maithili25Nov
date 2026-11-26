# CLAUDE.md – Prana Shakti Reset landing page (Maithili Janye)

Single-page static site. Source on GitHub (`rkwhatelse`), deployed by **Vercel** (`maithilicoach.vercel.app`)
with the custom domain **https://coach.divinehealhealth.com/** (live URL used in canonical/OG/JSON-LD/sitemap).
No build step, no framework: everything is in `index.html` (inline CSS + JS) plus `assets/`.
`vercel.json` redirects `/CLAUDE.md` and `/README.md` to the home page so these internal notes are not public on the site. Keep it when adding new internal files.

## Workflow for every change
1. Edit files.
2. Check the page still works on mobile (≈390px) and desktop (≈1366px) – open `index.html` in a browser or take screenshots.
3. `git add -A && git commit -m "<what changed>" && git push` – Vercel redeploys in about a minute.
Keep changes small and only touch what was asked.

## Current event
One live **90-minute** session on **Sunday 29 Nov 2026, 11:00 AM IST** (hero card shows "29 Nov | Sunday") (Zoom, Marathi + English).
The format changed from 2 days to 1 day: never reintroduce "2-Day", "Day 1 / Day 2" or "both days".
When the date/time changes, also update the JSON-LD `startDate`, the FAQ "What is the Prana Shakti Reset?"
(visible + JSON-LD) and the sticky-bar tip `'29 Nov · 11:00 AM IST · 90 mins'`.

## Quick edits (most common)
All at the bottom of `index.html` in `const CONFIG = {...}`:
- `date` → shown in hero "Date" card, e.g. `"29 Nov | Sunday"` (also update the static fallback text in the hero card)
- `time` → hero "Time" card, e.g. `"11:00 AM IST"`
- `paymentLink` → every button (currently TagMango `https://learn.divinehealhealth.com/l/645b4dbd8e`)

**Price** is ₹69. If it changes, replace `₹69` everywhere in `index.html` AND update:
- JSON-LD `"price": "69"` in `<head>`
- Meta Pixel `InitiateCheckout` `value: 69` in the CONFIG script
- FAQ answers "How much does it cost?" / "How will I get the link?" (visible FAQ and the FAQPage JSON-LD must stay identical)

**Coach bio placeholders** still to fill: `[15 years]`, `[50+ books]`, `[8–10]` (section "A Guide Who Has Walked This Path").

## Content & language rules (from the client)
- Exact spelling: **"Prana Shakti"** (never "Prana-Shakti"). Program name: **"Prana Shakti Reset"** (matches TagMango product "Prana Shakti Reset Masterclass").
- Coach name: **Maithili Janye** (always full name, incl. the bio greeting "नमस्कार, मी Maithili Janye.") – Energy Healer & Life Coach.
- Hero: English, except the lower description which is Marathi + English mix (Marglish).
- All lower sections: **English only**, except "A Guide Who Has Walked This Path" bio which is Marglish
  (Marathi sentence structure with English words, e.g. "माझे **reports normal** होते, तरीही ...").
- Audience line (yellow strip): "Curated for 25+ Ambitious Maharashtrian Women who are Multitaskers & Decision-makers".
- No "exclusive / early-bird / ₹999 / % OFF" offer anywhere – not part of this program.
- Keep it clean and uncluttered (client found earlier versions "jammed"/"spammy"): no emoji except in the Bonus section, no repeated price lines.
- Report section title: "Self-Discovery **Prana Shakti Report**" (orange, no marker/underline highlight) with "(Worth ₹1,248 - Included for Every Participant)".
- Testimonials are real – never invent new ones or names. Second video is labelled "Participant story" (name unknown).

## Design system
- Font: Poppins (Google Fonts). Colors in `:root`: navy `#1b1440`, orange `#f2622a` (highlights `.hl`), yellow `#ffc533`, green checks `#22b573`, CTA purple gradient `#6d3df2 → #8b5cf6`.
- Layout follows the client's reference: centered single column, alternating light / soft / dark (`.sec`, `.soft`, `.dark`) sections, two-tone `<h2>` titles with a small diamond divider.
- Hero: desktop = text left, circular photo right (`assets/coach-hero.jpg`, square image in dashed circle). Mobile order: title → photo → Marathi description → Duration/Date/Language/Time cards → CTA → report → What's Covered.
- **Every section ends with a CTA** (`.cta` block). Mobile has a sticky bottom bar (`.sticky`, hidden ≥900px) with ₹69 + "Reserve My Spot" and rotating tips.
- Buttons: `<a class="btn js-cta" href="PAYMENT" target="_blank" rel="noopener"><span class="ring"><i></i></span><span>LABEL</span><span class="arr">→</span></a>`
  – the `.ring` span is required for the glowing border arc (follows cursor on desktop ≥960px, orbits on touch/narrow screens). Do not reintroduce `prefers-reduced-motion` kill-switches or `@property` animations – they broke the effect on phones.

## Tracking
Meta Pixel `1713339420211886` in `<head>`: `PageView` on load; `InitiateCheckout` (value 69, INR) on click of any `.js-cta`. Keep both when editing buttons.

## SEO / AEO
`<head>` has title, description, canonical, Open Graph/Twitter (`assets/og-image.jpg`), favicon set (`favicon.ico`, `assets/favicon-32.png`, `apple-touch-icon.png`, `icon-192/512.png`, `site.webmanifest`), and JSON-LD (`WebPage`, `Person`, `Course` with ₹69 offer + `startDate`, `FAQPage`). `robots.txt` + `sitemap.xml` at root.
All absolute URLs use `https://coach.divinehealhealth.com/`. If the domain changes, update canonical, og:url, og:image, twitter:image, JSON-LD URLs, robots.txt and sitemap.xml.
Keep the FAQPage JSON-LD in sync with the visible FAQ.

## Assets
| File | Used for |
|---|---|
| `assets/coach-hero.jpg` | Hero circle (square crop of maithili.png) |
| `assets/coach-guide.jpg` | Coach section photo |
| `assets/prana-report.jpg` | Report image (watermark removed, "Prana Shakti" fixed) |
| `assets/testimonial-1.mp4`, `testimonial-2.mp4` (+ `-poster.jpg`) | Success-story videos (compress new videos: `ffmpeg -crf 28 -preset veryfast -movflags +faststart`) |
| `assets/mamata.jpg` | Mrs Mamata Athalye written testimonial |
| `assets/og-image.jpg` | Social share preview 1200×630 |
New images: resize to ≤1400px and compress before committing (GitHub web upload limit 25 MB/file; keep the page light for mobile).
