# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website for Beici Liang, built with Jekyll using the `jekyll-theme-console` theme (forked from `b2a3e8/jekyll-theme-console`). The theme provides a terminal/console aesthetic with dark/light mode support and a language toggle (EN/中文).

Live site: https://beiciliang.github.io

## Local Development

```bash
# Install dependencies (first time or after Gemfile changes)
# Use BUNDLE_FORCE_RUBY_PLATFORM=1 if you encounter native extension issues
BUNDLE_FORCE_RUBY_PLATFORM=1 bundle install

# Start local development server
bundle exec jekyll serve

# Server runs at http://localhost:4000
# Auto-reloads on file changes

# Build site for production (outputs to _site/)
bundle exec jekyll build

# Stop the server
# Press Ctrl+C or: pkill -f "jekyll serve"
```

## Architecture

### Theme Structure
- `_layouts/` - Page templates (default.html → home.html/page.html/post.html)
- `_includes/` - Reusable HTML components (header with language toggle, footer, head)
- `_sass/` - SCSS styles:
  - `base.scss` - Global styles, animations, language toggle CSS
  - `_dark.scss` / `_light.scss` / `_hacker.scss` / `_nord.scss` - Theme color variables
- `assets/` - Compiled SCSS entry points (main.scss, main-dark.scss, etc.)

### Content
- `index.md` - Homepage with bilingual content (EN/CN), uses `markdown="1"` in divs for proper parsing
- `_config.yml` - Jekyll configuration (style, header_pages, footer, SEO)

### Language Toggle
- Toggle buttons in `_includes/header.html`
- JavaScript in `index.md` handles switching and localStorage persistence
- Content wrapped in `<div class="lang-content lang-en/cn" markdown="1">`

### Key Configuration Options (_config.yml)
- `style: dark` | `light` | `hacker` | `nord` - Theme color scheme
- `listen_for_clients_preferred_style: true` - Respect OS dark mode preference
- `header_pages` - Navigation menu items
- `footer` - Footer HTML content
