<h1 align="center" style="font-size: 55px">Helix</h1>
<p align="center" style="font-size: 30px">A kakoune / neovim inspired editor, written in Rust.</p>

<div align="center" style="display:inline">
      <img src="screenshot1.png" width="49%">
      <img src="screenshot2.png" width="49%">
</div>


[![Build status](https://github.com/helix-editor/helix/actions/workflows/build.yml/badge.svg)](https://github.com/helix-editor/helix/actions)
[![Matrix](https://img.shields.io/matrix/helix-community:matrix.org)](https://img.shields.io/matrix/helix-community:matrix.org)
[![License](https://img.shields.io/github/license/helix-editor/helix)](./LICENSE)

The editing model is very heavily based on kakoune; during development I found
myself agreeing with most of kakoune's design decisions. If you want to learn more about the design of helix; see our [vision](./docs/vision.md).

For more information, see the [website](https://helix-editor.com) or
[documentation](https://docs.helix-editor.com/).

All shortcuts/keymaps can be found [on the website](https://docs.helix-editor.com/keymap.html).


## ✨ Features

- Vim-like modal editing
- Multiple selections
- Built-in language server support
- Smart, incremental syntax highlighting and code editing via tree-sitter

It's a terminal-based editor first, but I'd like to explore a custom renderer
(similar to emacs) in wgpu or skulpin. See [#39](https://github.com/helix-editor/helix/issues/39) for more info.

## 📦 Installation

> Note: Installing from source requires extra configuration for syntax highlighting and themes to work. See [runtime](#runtime).

> Having trouble? Check out the [troubleshooting section.](https://github.com/helix-editor/helix/wiki/Troubleshooting)

#### Binary

Pre-build binaries are available in the [releases page](https://github.com/helix-editor/helix/releases). 

Packages are also available:

[![Packaging status](https://repology.org/badge/vertical-allrepos/helix.svg)](https://repology.org/project/helix/versions)

#### macOS

Helix can be installed on macOS through homebrew:

```
brew tap helix-editor/helix
brew install helix
```

#### From source

```
git clone --recurse-submodules --shallow-submodules -j8 https://github.com/helix-editor/helix
cd helix
cargo install --path helix-term
```

This will install the `hx` binary to `$HOME/.cargo/bin`.

#### Runtime

> Note: Installing runtime is not required for linux packages or binaries.

Helix requires extra files for syntax highlighting and themes. To install, symlink the `runtime/` folder to the directory below.

| OS            | Path                  |
|---------------|-----------------------|
| Linux & MacOS | ~/.config/helix/      |
| Windows       | Appdata/Roaming/Helix |

For example: `~/.config/helix/runtime`

#### Notes

The runtime directory can be overridden via the `HELIX_RUNTIME` environment variable.

Running via cargo also doesn't require setting explicit `HELIX_RUNTIME` path, it will automatically
detect the `runtime` directory in the project root.

Setting up runtime is not required for linux. Packages wrap the `hx` binary
with a wrapper that sets HELIX_RUNTIME to the install directory.

## 📚 Documentation

- [FAQ](https://github.com/helix-editor/helix/wiki/FAQ)
- [Themes](https://github.com/helix-editor/helix/wiki/Themes)
- [Helix Website](https://helix-editor.com/)
  - [Documentation](https://docs.helix-editor.com/)
  - [Basic Usage](https://docs.helix-editor.com/usage.html)
  - [Keymappings](https://docs.helix-editor.com/keymap.html)
  - [Configuration](https://docs.helix-editor.com/configuration.html)
  - [Custom Themes](https://docs.helix-editor.com/themes.html)
  - [Migrating from Vim](https://docs.helix-editor.com/from-vim.html)

## ❤️ Contributing ️

Contributors are very welcome! **No contribution is too small and all contributions are valued!**

Some suggestions to get started:

- You can look at the [good first issue](https://github.com/helix-editor/helix/labels/E-easy) label on the issue tracker.
- Help with packaging on various distributions needed!
- To use print debugging to the `~/.cache/helix/helix.log` file, you must:
  - Print using `log::info!`, `warn!`, or `error!`. (`log::info!("helix!")`)
  - Use the parameter (`hx -v <file>`) to increase log verbosity. Increase the `v's` for more info, `hx -vvv` being most verbose.
- If your preferred language is missing, integrating a tree-sitter grammar for
  it and defining syntax highlight queries for it is straight forward and
  doesn't require much knowledge of the internals.

We provide an [architecture.md](./docs/architecture.md) that should give you
a good overview of the internals.

## 🙋 Getting help

Discuss the project on the community [Matrix Space](https://matrix.to/#/#helix-community:matrix.org) (make sure to join `#helix-editor:matrix.org` if you're on a client that doesn't support Matrix Spaces yet).
