# Custom Styling

You do not need to replace the entire mdBook theme to tweak the look. A small
custom CSS file loaded via `additional-css` is often all you need.

## Setup

Create a `theme/` directory next to your `src/` folder and add a CSS file:

```sh
mkdir theme
touch theme/custom.css
```

Then reference it in `book.toml`:

```toml
[output.html]
additional-css = ["./theme/custom.css"]
```

## Example customisations

Here is a small `theme/custom.css` that makes a few tasteful tweaks without
fighting the default theme:

```css
/* Slightly wider content area */
:root {
    --content-max-width: 850px;
}

/* Softer sidebar font size */
.sidebar {
    font-size: 0.9em;
}

/* Accent underline on h1 headings */
.content main h1 {
    border-bottom: 2px solid var(--sidebar-active);
    padding-bottom: 0.3em;
}

/* Rounded code blocks */
.content main pre {
    border-radius: 6px;
}

/* Make inline code stand out */
.content main code {
    padding: 0.1em 0.35em;
    border-radius: 3px;
}
```

## Useful CSS variables

mdBook exposes CSS custom properties you can override. A few handy ones:

| Variable | Description |
|----------|-------------|
| `--content-max-width` | Maximum width of the main content area |
| `--sidebar-width` | Width of the navigation sidebar |
| `--sidebar-bg` | Sidebar background colour |
| `--sidebar-active` | Colour of the active sidebar link |
| `--links` | Colour of hyperlinks |
| `--inline-code-color` | Colour of inline `code` spans |

These variables change per theme (Light, Rust, Coal, Navy, Ayu), so your
overrides automatically adapt to the reader's chosen theme.

## Going further

If CSS overrides are not enough, you can replace individual template files. Copy
them from the mdBook source into your `theme/` directory:

```sh
mdbook init --theme   # dumps all default theme files into theme/
```

You can then edit `theme/index.hbs` (the page template), `theme/header.hbs`,
or any of the CSS files. mdBook will use your local copies instead of the
built-in ones.

> **Tip:** Only copy the files you actually want to change. Keeping the rest at
> their defaults means you automatically benefit from upstream improvements when
> you upgrade mdBook.
