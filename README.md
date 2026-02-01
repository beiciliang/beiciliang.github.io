# jekyll-theme-console

A minimal, console‑inspired Jekyll theme for hackers, developers and other cool kids.

[![Gem Version](https://img.shields.io/gem/v/jekyll-theme-console.svg?color=informational)](https://rubygems.org/gems/jekyll-theme-console)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE.txt)

<img src="https://raw.githubusercontent.com/b2a3e8/jekyll-theme-console/master/screenrec-dark.gif" width="550" alt="jekyll-theme-console demo animation">

## Demo

- [dark style demo](https://b2a3e8.github.io/jekyll-theme-console-demo-dark/) ([source code / template](https://github.com/b2a3e8/jekyll-theme-console-demo-dark))

  [<img src="https://raw.githubusercontent.com/b2a3e8/jekyll-theme-console/master/screenshot-dark.png" width="350" alt="Dark style screenshot">](https://b2a3e8.github.io/jekyll-theme-console-demo-dark/)
- [light style demo](https://b2a3e8.github.io/jekyll-theme-console-demo-light/) ([source code / template](https://github.com/b2a3e8/jekyll-theme-console-demo-light))

  [<img src="https://raw.githubusercontent.com/b2a3e8/jekyll-theme-console/master/screenshot-light.png" width="350" alt="Light style screenshot">](https://b2a3e8.github.io/jekyll-theme-console-demo-light/)
- [hacker style demo](https://b2a3e8.github.io/jekyll-theme-console-demo-hacker/) ([source code / template](https://github.com/b2a3e8/jekyll-theme-console-demo-hacker))

  [<img src="https://raw.githubusercontent.com/b2a3e8/jekyll-theme-console/master/screenshot-hacker.png" width="350" alt="Hacker style screenshot">](https://b2a3e8.github.io/jekyll-theme-console-demo-hacker/)

Note: The theme also includes a Nord variant (`style: nord`).

## Features

- Four styles: `dark` (default), `light`, `hacker`, `nord`
- Optional auto light/dark via `prefers-color-scheme`
- Strict, extendable Content Security Policy
- Optional Google Fonts (disable for full self‑hosting)
- Generic analytics/tracker include (Matomo, Plausible, etc.)
- Simple header navigation via `header_pages`
- Works as a RubyGem theme or GitHub Pages remote theme

## Quickstart

If you are new to Jekyll, skim the official docs: https://jekyllrb.com/docs/

### GitHub Pages (remote_theme)

Add to your site's `_config.yml`:

```yaml
remote_theme: b2a3e8/jekyll-theme-console
# Optional but recommended
plugins:
  - jekyll-seo-tag
```

Tip: For full local builds with a remote theme, you may need the `jekyll-remote-theme` plugin.

### Gem-based installation

1) Add to your `Gemfile`:

```ruby
gem "jekyll-theme-console"
```

2) Install and enable the theme:

```bash
bundle
```

```yaml
# _config.yml
theme: jekyll-theme-console
plugins:
  - jekyll-seo-tag
```

To update later: `bundle update`.

## Configuration

Add these to `_config.yml` as needed:

- `header_pages`: list of page paths to show in the top menu
- `footer`: HTML string rendered in the footer
- `style`: `dark` (default), `light`, `hacker`, or `nord`
- `listen_for_clients_preferred_style`: `true` to auto‑switch using the OS preference
- `disable_google_fonts`: `true` to avoid requests to Google Fonts
- `tracking`: generic tracker configuration (see Security & CSP below)
- `csp_extra`: extra CSP directives to append to the built‑in policy

Example:

```yaml
header_pages:
  - index.md
  - about.md

style: dark # dark (default), light, hacker, or nord
listen_for_clients_preferred_style: true # false (default) or true

footer: 'follow us on <a href="https://twitter.com/xxx">twitter</a>'
disable_google_fonts: false

# Generic tracking (optional; loads only in production)
# tracking:
#   script_src:
#     - https://cdn.example.com/tracker.js
#   async: true   # default true
#   defer: false  # default false
#   # Optional inline init snippet (requires CSP allowance if used)
#   # init: |
#   #   window.myTracker=window.myTracker||function(){(window.myTracker.q=window.myTracker.q||[]).push(arguments)};
#   #   myTracker('init', { siteId: '12345' });
```

### Front matter

Additional page variables supported by the theme:

- `title`: page title
- `lang`: page language (defaults to `en`)
- `robots`: value for the robots meta tag (e.g., `NOINDEX`)

## Customization

Follow these steps to customize:

1. Fork this repository (use as a theme or directly as your site)
2. Edit templates in `_layouts` for HTML changes
3. Edit styles in `_sass` and `assets`
   - Global variables (font size, container width) live in `_sass/base.scss`
   - Style‑specific variables are in `_sass/_dark.scss`, `_sass/_light.scss`, `_sass/_hacker.scss`, `_sass/_nord.scss`
   - Fonts are loaded with `<link>` tags; set `disable_google_fonts: true` to avoid external font requests

Optional tweaks:

- Enable Sass compression in `_config.yml`:

  ```yaml
  sass:
    style: compressed
  ```

- Add `jekyll-feed` to generate an Atom/RSS feed.

### Security & CSP

The theme ships with a strict, practical Content Security Policy. By default it allows:

- self‑hosted content, plus images from `https:` and `data:` URIs
- Google Fonts (unless disabled)

Extend the policy as needed via `_config.yml`:

```yaml
csp_extra: "frame-src https:;"
```

Examples:

- Matomo at `https://analytics.example.com`:

  ```yaml
  tracking:
    script_src:
      - https://analytics.example.com/matomo.js
  # If you add an inline init snippet via `tracking.init`, also include 'unsafe-inline' in script-src.
  csp_extra: "script-src 'self' https://analytics.example.com 'unsafe-inline'; connect-src 'self' https://analytics.example.com; img-src 'self' https://analytics.example.com;"
  ```

- Plausible at `https://plausible.example.com`:

  ```yaml
  tracking:
    script_src:
      - https://plausible.example.com/js/plausible.js
  csp_extra: "script-src 'self' https://plausible.example.com; connect-src 'self' https://plausible.example.com;"
  ```

Tip: To remove the top border in the menu:

```css
.menu { border-top: none; }
```

## Development

This repository is a standard Jekyll site for local development of the theme.

### Docker (recommended)

```bash
docker compose up --build
```

Open `http://localhost:4000`.

### Local (Ruby/Bundler)

```bash
bundle install
bundle exec jekyll serve
```

Open `http://localhost:4000`.

When the theme is released, only files in `_layouts`, `_includes`, `_sass`, and `assets` tracked by Git are bundled. To include additional paths, edit the regexp in `jekyll-theme-console.gemspec`.

## License

Open source under the [MIT License](https://opensource.org/licenses/MIT).
