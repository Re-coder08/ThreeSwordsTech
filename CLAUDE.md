# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development

No build system — this is a static site. Open `index.html` directly in a browser, or serve locally:

```bash
python -m http.server 8000
# or
npx http-server
```

## Architecture

Everything lives in a single file: `index.html`. CSS is in `<style>` tags, JavaScript is in `<script>` tags at the bottom. There are no external stylesheets, scripts, or dependencies beyond Google Fonts loaded via CDN.

**Page sections (in DOM order):** Navigation → Hero → Three Swords Philosophy → Services (6 cards) → Stats → Why Three Swords → CTA Banner → Footer

**Design system via CSS custom properties:**
- `--bg`: `#08090D`, `--accent`: `#00AAFF`, `--text`: `#F0F4FF`, `--muted`: `#7A8499`, `--red`: `#CC2200`
- Fonts: `Syne` (headings/buttons), `DM Sans` (body), `JetBrains Mono` (labels/accents)
- Mobile breakpoint: `900px`

**Animation system:** `.fade-up` class + Intersection Observer triggers scroll-reveal. Elements get `opacity: 1; transform: translateY(0)` when entering the viewport, with cascading `transition-delay` for staggered effects.

**Logo:** Three diagonal swords drawn entirely with CSS (rotated `<div>`s with gradient).
