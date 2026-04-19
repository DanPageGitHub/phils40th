# Phil's 40th — Claude Code Context

## Project overview

Single-file static event website for Phil's Big Phat 40th Birthday, 2nd–4th October 2026 at Three Pools Permaculture Farm, Abergavenny, Wales.

Live URL: https://phils40th.co.uk

---

## Hosting & deployment

- Hosted on **GitHub Pages**, repo: `DanPageGitHub/phils40th`, branch: `main`
- Custom domain managed via **Names.co.uk** DNS (A records pointing to GitHub Pages IPs)
- `CNAME` file in repo root contains `phils40th.co.uk` — do not delete or modify this
- No Netlify, no build step, no CI config
- To deploy: commit and push to `main` — GitHub Pages rebuilds automatically

---

## File structure

The site is `index.html` plus an `images/` folder of JPEG files.

All CSS and JS live inside `index.html`. Images are external files in `images/` referenced via relative paths.

There is also a `.gitignore/` directory in the project root — this is intentionally kept local (not a git ignore file) and is excluded from the repo via `.git/info/exclude`. Do not delete it.

---

## Tech stack

- Pure HTML/CSS/JS, no frameworks
- Google Fonts (Bebas Neue, Barlow, Barlow Condensed) loaded via CDN — the only external dependency
- Images are JPEG files in `images/`, referenced with relative paths (no leading slash)

---

## Design system

| Token | Value |
|---|---|
| Background | `#0B0B0B` |
| Primary orange | `#FF5A00` |
| Accent orange | `#FF7A1A` |
| White | `#FFFFFF` |
| Spacing scale | `--s1` through `--s16` (CSS custom properties) |

- Headings: Bebas Neue
- Body: Barlow / Barlow Condensed
- Aesthetic: 90s rave

---

## Layout & sections

Page sections in order, with their anchor IDs:

- `#hero` — full-height hero with Phil's portrait, title, and key event info
- `#lineup` — Saturday band and rave lineup
- `#plan` — Friday/Saturday/Sunday schedule cards
- `#camping` — sleep/accommodation options
- `#food` — food and drink info
- `#location` — map, travel times, venue info
- `#tickets` — ticket types and booking

---

## Navigation

- Sticky nav, always visible on mobile, scroll-triggered on desktop
- Below **660px**: shorter link labels + pipe separators (`|`)
- Above **660px**: full labels + star separators (`★`)
- Separators use dual spans: `.nav-sep-star` and `.nav-sep-pipe`, toggled via CSS at the 660px breakpoint
- Nav labels: Lineup, Plan, Sleep, Food, Location/Map, Tickets

---

## CSS notes

- There are multiple `@media (max-width:768px)` blocks — consolidate into existing ones rather than adding new ones
- Phil's hero image (`.hero__phil-img`) has CSS rules across two separate mobile blocks that can conflict — treat with care
- The venue photo grid uses `grid-column:1/-1` for the full-width panoramic bottom row

---

## Images

- All photographic images live as JPEG files in the `images/` folder and are referenced from `index.html` via relative paths like `src="images/hero-phil.jpg"`
- Relative paths (no leading slash) are required so the site works both locally via `python -m http.server` and on GitHub Pages with the custom domain
- The favicon (inline SVG) and the body noise texture (inline SVG) remain as small `data:` URIs in `index.html`, do not extract these
- To replace an image: overwrite the JPEG file in `images/` keeping the same filename, or add a new file and update the `src` in `index.html`
- Always verify which image is in which slot before replacing, do not assume by alt text alone
- Never save a screenshot or annotated image as a venue photo

---

## Workflow

```
# Clone
git clone https://github.com/DanPageGitHub/phils40th.git

# Edit index.html directly

# Deploy
git add index.html
git commit -m "your message"
git push origin main
```

GitHub Pages will rebuild and the live site will update within a minute or two.

---

## Copy & wording

- Never change, rewrite, or "polish" any user-facing copy without explicit
  approval from the user first. This includes headings, body text, button
  labels, marquee text, meta tags, and nav labels.
- If a change requires new copy, propose the exact wording and wait for
  sign-off before editing index.html.
- Writing style rules (apply everywhere):
  - No em dashes. Use commas, colons, or a new sentence.
  - No full stops at the end of bullet points.
  - British English throughout.
  - Exclamation marks are fine on this site, use when appropriate.
  - No superlatives ("amazing", "incredible", "stunning", "world-class").
  - Don't promise things that aren't confirmed. Hedge with "TBC",
    "hoping to", "subject to availability".
  - Short sentences preferred.
  - Never use the "It's not just X, it's Y" construction.
- Voice: northern, plain-spoken, direct, warm, unpretentious. Facts over hype.
