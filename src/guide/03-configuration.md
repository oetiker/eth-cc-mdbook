# Configuration

All configuration lives in `book.toml` at the project root. Here is a typical setup:

```toml
[book]
authors = ["Your Name"]
language = "en"
src = "src"
title = "My Awesome Book"

[build]
build-dir = "book"

[output.html]
git-repository-url = "https://github.com/youruser/yourrepo"
```

## Key sections

### `[book]`

| Key | Description |
|-----|-------------|
| `title` | Displayed in the browser tab and sidebar header |
| `authors` | List of author names |
| `language` | BCP 47 language tag (e.g. `en`, `de`) |
| `src` | Directory containing your Markdown source files |

### `[build]`

| Key | Description |
|-----|-------------|
| `build-dir` | Output directory for the rendered book (default `book`) |

### `[output.html]`

| Key | Description |
|-----|-------------|
| `git-repository-url` | Adds a link icon in the top-right corner pointing to your repo |
| `default-theme` | Set the default theme (`Light`, `Rust`, `Coal`, `Navy`, `Ayu`) |
| `preferred-dark-theme` | Theme used when the OS requests dark mode |

## Built-in search

mdBook ships with a **client-side search engine** that is enabled by default. It
builds a search index at compile time and bundles it into the output. Readers can
press `S` or click the magnifying-glass icon to search across the entire book — no
server required.

You can configure search in `book.toml`:

```toml
[output.html.search]
enable = true            # enabled by default
limit-results = 30       # max results shown
use-hierarchical-headings = true  # show parent headings in results
```

The search index adds some weight to the final output. If your book is very large and
you want to reduce the download size, you can set `enable = false`, but for most
books the convenience far outweighs the extra kilobytes.

## Further reading

See the [mdBook documentation](https://rust-lang.github.io/mdBook/format/configuration/index.html)
for the full list of options.
