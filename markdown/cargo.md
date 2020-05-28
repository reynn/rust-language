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

- [`cargo-edit`] - Add dependencies to your Cargo.toml without having to manually edit the file.

  ```console
  $ cargo install cargo-edit
    Updating crates.io index
  Installing cargo-add v0.2.0
    ...
    Finished release [optimized] target(s) in 14.65s
   Replacing /Users/reynn/.cargo/bin/cargo-add
  $ cargo add clap
  $ cargo rm serde_json
  ```

- [`cargo-generate`] - Kickstart a project by using an existing git repo as a template.
  a list of available templates is available on the [`cargo-generate GitHub`]

  ```console
  $ cargo install cargo-generate
      Updating crates.io index
    Installing cargo-generate v0.5.0
      ...
      Finished release [optimized] target(s) in 3m 40s
    Installing C:\Users\arasu\.cargo\bin\cargo-generate.exe
    Installed package `cargo-generate v0.5.0` (executable `cargo-generate.exe`)
  $ cargo generate --git https://github.com/mendelt/cmdr-template
    Project Name: test-project
    Creating project called `test-project`...
    Done! New project created ~/git/test-project
  ```

[`cargo-edit`]: https://github.com/killercup/cargo-edit
[`cargo-generate`]: https://github.com/ashleygwilliams/cargo-generate
[`cargo-generate github`]: https://github.com/ashleygwilliams/cargo-generate/blob/master/TEMPLATES.md
