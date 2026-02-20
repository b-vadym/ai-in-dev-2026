# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev          # Start dev server with live reload (opens browser)
npm run build        # Build for production to ./dist
npm run build:gh-pages  # Build for GitHub Pages (base: /ai-in-dev-2026/)
npm run export       # Export slides to PDF/PNG
npm run presenter    # Start in presenter/remote mode
```

## Architecture

This is a [Slidev](https://sli.dev) presentation — a Vue/Vite-based slide framework where the entire presentation lives in a single Markdown file.

**Key files:**
- `slides.md` — all slides in one file, separated by `---`. This is the main file to edit.
- `components/QrLink.vue` — custom Vue component wrapping `qrcode.vue`, usable directly in slides as `<QrLink value="..." />`
- `img/` — static images referenced in slides as `/img/filename.png`
- Images at the root level (`.webp`, `.jpg`) are also served as static assets

**Slidev slide syntax in `slides.md`:**
- Slides are separated by `---`
- Front matter (YAML) between `---` blocks sets layout, class, transitions per-slide
- `v-click` / `v-clicks` directives add click-to-reveal animations
- Mermaid diagrams are supported in fenced code blocks with ` ```mermaid `
- `mdc: true` is set globally, enabling MDC (Markdown Components) syntax
- Layouts used: `center`, `section`, `image-right`, default

**Global front matter** (top of `slides.md`):
- Theme: `@slidev/theme-seriph`
- Default transition: `slide-left`
- Drawings: disabled (`persist: false`)

**Deployment:** GitHub Actions deploys to GitHub Pages. The `build:gh-pages` script sets `--base /ai-in-dev-2026/` for correct asset paths.

**Content language:** Ukrainian (презентація для розробників та тестувальників).
