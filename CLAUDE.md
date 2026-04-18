# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development

No build system — this is a static site. Open `index.html` directly in a browser, or serve locally:

```bash
python -m http.server 8000
# or
npx http-server
```

## Git Flow Deployment

This project uses **Git Flow** for branch management and releases:
- **`main`** — Production releases only (protected, requires PR review)
- **`develop`** — Integration branch (protected, requires PR review)
- **Feature branches** — Branch off `develop` as `feature/description`
- **Release branches** — `release/vX.X.X` merge to both `main` and `develop`
- **Hotfix branches** — `hotfix/description` for emergency production fixes

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed workflow guidelines.

## Architecture

Everything lives in a single file: `index.html`. CSS is in `<style>` tags, JavaScript is in `<script>` tags at the bottom. There are no external stylesheets, scripts, or dependencies beyond Google Fonts loaded via CDN.

**Page sections (in DOM order):** Navigation → Hero → Three Swords Philosophy → Services (6 cards) → Stats → Why Three Swords → CTA Banner → Footer

**Design system via CSS custom properties:**
- `--bg`: `#08090D`, `--accent`: `#00AAFF`, `--text`: `#F0F4FF`, `--muted`: `#7A8499`, `--red`: `#CC2200`
- Fonts: `Syne` (headings/buttons), `DM Sans` (body), `JetBrains Mono` (labels/accents)
- Mobile breakpoint: `900px`

**Animation system:** `.fade-up` class + Intersection Observer triggers scroll-reveal. Elements get `opacity: 1; transform: translateY(0)` when entering the viewport, with cascading `transition-delay` for staggered effects.

**Logo:** Three diagonal swords drawn entirely with CSS (rotated `<div>`s with gradient).
