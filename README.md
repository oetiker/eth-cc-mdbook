# mdBook + mise + GitHub Pages Template

A ready-to-use template for publishing an [mdBook](https://rust-lang.github.io/mdBook/) site to GitHub Pages.

All tools are managed by [mise](https://mise.jdx.dev/) — no Rust toolchain required.

## What's included

- **mdBook 0.5** — static site generator for Markdown books
- **mdbook-mermaid** — diagrams (flowcharts, sequence diagrams, etc.) via [Mermaid.js](https://mermaid.js.org/)
- **Custom CSS** — example `theme/custom.css` with light styling tweaks
- **GitHub Actions** — automatic build and deploy to GitHub Pages on push to `main`
- **Built-in search** — client-side full-text search, enabled by default

## Quick start

### Use this template

Click **"Use this template"** above to create your own repository, then clone it.

### Local development

```sh
# Install mise if you don't have it
curl https://mise.run | sh

# Install mdBook and plugins
mise install

# Start the dev server with live-reload
mdbook serve --open
```

### Customize

1. Edit `book.toml` — set your title, authors, and repo URL
2. Edit `src/SUMMARY.md` — define your chapters
3. Write Markdown in `src/`
4. Push to `main` — GitHub Actions handles the rest

### Enable GitHub Pages

In your new repo go to **Settings > Pages** and set the source to **GitHub Actions**.

## Live demo

[oetiker.github.io/eth-cc-mdbook](https://oetiker.github.io/eth-cc-mdbook/)
