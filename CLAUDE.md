# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website for Beici Liang, built with Jekyll using the `jekyll-theme-console` theme (forked from `b2a3e8/jekyll-theme-console`). The theme provides a terminal/console aesthetic with dark/light mode support.

Live site: https://beiciliang.github.io

## Commands

```bash
# Install dependencies
bundle install

# Run local development server (http://localhost:4000)
bundle exec jekyll serve

# Build site for production
bundle exec jekyll build
```

## Architecture

### Theme Structure
- `_layouts/` - Page templates (default.html → home.html/page.html/post.html)
- `_includes/` - Reusable HTML components (header, footer, head, google-analytics)
- `_sass/` - SCSS styles:
  - `base.scss` - Global styles, variables (font-size, container-width)
  - `_dark.scss` / `_light.scss` - Theme-specific CSS variables
- `assets/` - Compiled SCSS entry points (main.scss, main-dark.scss, main-light.scss)

### Content
- `index.md` - Homepage with bilingual (EN/CN) bio
- `about.md` - Contact/social links page
- `_config.yml` - Jekyll configuration (style: dark, header_pages, footer, SEO)

### Key Configuration Options (_config.yml)
- `style: dark` or `light` - Theme color scheme
- `listen_for_clients_preferred_style: true` - Respect OS dark mode preference
- `header_pages` - Navigation menu items
- `footer` - Footer HTML content
