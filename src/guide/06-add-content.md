# Add Content

## The SUMMARY.md file

`src/SUMMARY.md` is the table of contents. mdBook uses it to determine the book
structure, chapter ordering, and navigation. Every chapter must be listed here.

Example:

```md
# Summary

[Introduction](./introduction.md)

# Part One

- [Getting Started](./part1/getting-started.md)
- [Core Concepts](./part1/core-concepts.md)

# Part Two

- [Advanced Topics](./part2/advanced.md)
```

- Lines starting with `#` create **part headings** (rendered as section dividers).
- Lines starting with `-` are **chapters** (linked Markdown files).
- Indented items become **sub-chapters**.

## Writing Markdown

mdBook supports standard Markdown plus a few extensions:

- **Code blocks** with syntax highlighting (specify the language after the opening
  triple backticks)
- **`{{#include}}`** — include external files or parts of files
- **`{{#playground}}`** — embed Rust playgrounds (useful for Rust documentation)

### Including files

You can include the contents of another file:

```text
\{{#include ../path/to/file.rs}}
```

Or include only specific lines:

```text
\{{#include ../path/to/file.rs:3:10}}
```

This is handy for keeping code examples in separate, testable files.

## Creating a new chapter

1. Add an entry to `SUMMARY.md`
2. Create the corresponding `.md` file
3. Write your content

If the development server is running (`mdbook serve`), the browser will
automatically reload with your changes.
