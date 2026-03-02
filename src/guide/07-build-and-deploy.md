# Build and Deploy

## Production build

Generate the static site:

```sh
mdbook build
```

The rendered HTML is written to the `book/` directory (or whatever `build-dir` is
set to in `book.toml`). You can serve this directory with any static file host.

## Deploy to GitHub Pages

### Repository setup

1. Push your project to a GitHub repository.
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, set the source to **GitHub Actions**.

### GitHub Actions workflow

Create `.github/workflows/mdbook.yaml` with the following content:

```yaml
name: Deploy mdBook to GitHub Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Install tools via mise
        uses: jdx/mise-action@v3

      - name: Build book
        run: mdbook build

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: ./book

  deploy:
    environment:
      name: github-pages
      url: ${{ github.event.deployment.payload.web_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### How it works

1. On every push to `main`, the workflow triggers.
2. **mise** installs the exact mdBook version **and all plugins** from `mise.toml`.
3. `mdbook build` renders the book to `book/` (preprocessors like mermaid, admonish,
   and katex run automatically).
4. The artifact is uploaded and deployed to GitHub Pages.

After the first successful run, your book is live at
`https://<username>.github.io/<repository>/`.
