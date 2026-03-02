# Mermaid Diagrams

[mdbook-mermaid](https://github.com/badboy/mdbook-mermaid) integrates
[Mermaid.js](https://mermaid.js.org/) so you can write diagrams directly in
fenced code blocks.

## Installation

Add the plugin to `mise.toml` alongside mdBook:

```toml
[tools]
"aqua:rust-lang/mdBook" = "0.5.2"
"ubi:badboy/mdbook-mermaid" = "0.17.0"
```

Install:

```sh
mise install
```

Then run the one-time setup to copy the JavaScript files and update `book.toml`:

```sh
mdbook-mermaid install path/to/your/book
```

This adds `mermaid.min.js` and `mermaid-init.js` to your project root and
configures the preprocessor in `book.toml`:

```toml
[output.html]
additional-js = ["mermaid.min.js", "mermaid-init.js"]

[preprocessor.mermaid]
command = "mdbook-mermaid"
```

## Usage

Wrap your diagram code in a fenced block tagged `mermaid`:

````md
```mermaid
graph LR
    A[Write Markdown] --> B[mdBook Build]
    B --> C[Static HTML]
    C --> D[GitHub Pages]
```
````

Renders as:

```mermaid
graph LR
    A[Write Markdown] --> B[mdBook Build]
    B --> C[Static HTML]
    C --> D[GitHub Pages]
```

## More examples

### Sequence diagram

```mermaid
sequenceDiagram
    participant B as Browser
    participant S as Server
    B->>S: GET /index.html
    S-->>B: HTML + JS
    B->>B: Render book
```

### Flowchart

```mermaid
flowchart TD
    Start --> Install[mise install]
    Install --> Init[mdbook init]
    Init --> Write[Write content]
    Write --> Serve[mdbook serve]
    Serve --> Happy{Looks good?}
    Happy -- Yes --> Build[mdbook build]
    Happy -- No --> Write
    Build --> Deploy[Push to GitHub]
```

Mermaid supports many diagram types: flowcharts, sequence diagrams, Gantt charts,
class diagrams, state diagrams, ER diagrams, pie charts, and more. See the
[Mermaid documentation](https://mermaid.js.org/intro/) for the full list.
