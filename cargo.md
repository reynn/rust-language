# Cargo Overview <!-- omit in toc -->

- [`build`](#build)
- [`test`](#test)
- [`doc`](#doc)
- [`install`](#install)
- [Plugins](#plugins)
  - [Plugin Suggestions](#plugin-suggestions)
    - [Cargo Add](#cargo-add)

## `build`

## `test`

## `doc`

## `install`

## Plugins

### Plugin Suggestions

These add extra commands to cargo that make it even more useful!

#### Cargo Add
- [`cargo-add`] - Add dependencies to your Cargo.toml without having to
  manually edit the file.

  ```console
  $ cargo install cargo-add --force
    Updating crates.io index
  Installing cargo-add v0.2.0
    ...
    Finished release [optimized] target(s) in 14.65s
   Replacing /Users/reynn/.cargo/bin/cargo-add
  $ cargo add clap
  $ cargo add clap --version '~2.3'
  ```
