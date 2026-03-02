# Prerequisites

Before getting started, you need **Git** and **mise** installed on your system.

## Git

Install Git if you do not already have it:

| OS | Command |
|----|---------|
| macOS | `xcode-select --install` |
| Debian/Ubuntu | `sudo apt install git` |
| Fedora | `sudo dnf install git` |

## mise

[mise](https://mise.jdx.dev/) is a polyglot tool-version manager. It lets you pin
exact tool versions per project so that every contributor uses the same setup.

Install mise:

```sh
curl https://mise.run | sh
```

Then activate it in your shell. Add one of the following to your shell configuration
file (`~/.bashrc`, `~/.zshrc`, etc.):

```sh
# Bash
eval "$(~/.local/bin/mise activate bash)"

# Zsh
eval "$(~/.local/bin/mise activate zsh)"

# Fish
~/.local/bin/mise activate fish | source
```

Restart your shell (or `source` the config file) and verify:

```sh
mise --version
```

## What mise will manage

In this guide mise installs and manages **mdBook** so you do not need Rust or Cargo
on your machine. The exact version is pinned in `mise.toml` at the project root.
