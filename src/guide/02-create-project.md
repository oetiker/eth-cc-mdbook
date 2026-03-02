# Create a Project

## Scaffold the book

Create a directory for your book, enter it, and set up mise:

```sh
mkdir mybook && cd mybook
git init
```

Create a `mise.toml` file to pin the mdBook version:

```toml
[tools]
"aqua:rust-lang/mdBook" = "0.5.2"
```

Let mise install the tool:

```sh
mise install
```

Verify the installation:

```sh
mdbook --version
```

Now initialise the book:

```sh
mdbook init
```

When prompted, accept the defaults. This creates the following structure:

```text
mybook/
├── book.toml
└── src/
    ├── SUMMARY.md
    └── chapter_1.md
```

| Path | Purpose |
|------|---------|
| `book.toml` | Book metadata and configuration |
| `src/SUMMARY.md` | Table of contents — defines the chapter structure |
| `src/chapter_1.md` | Your first chapter |

## Preview locally

Start the built-in development server:

```sh
mdbook serve --open
```

This builds the book, opens it in your browser, and **live-reloads** whenever you
save a file. The default address is <http://localhost:3000>.
