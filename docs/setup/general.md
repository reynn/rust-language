# Setting up for Rust Development <!-- omit in toc -->

- [Install Rust and Cargo](#install-rust-and-cargo)
- [Setup your IDE of choice](#setup-your-ide-of-choice)

## Install Rust and Cargo

Best way to bootstrap your development is using [`Rustup`].

```shell
$ curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
info: downloading installer

Welcome to Rust!

This will download and install the official compiler for the Rust
programming language, and its package manager, Cargo.

...

   default host triple: x86_64-unknown-linux-gnu
     default toolchain: stable
               profile: default
  modify PATH variable: yes
1) Proceed with installation (default)
2) Customize installation
3) Cancel installation
```

Select 1 to proceed, customizing provides options to download nightly/beta releases amongst other things. We do not need those right now.
Once this completes and you are back at a prompt we will go ahead and get clippy and rustfmt installed.

```shell
# Launch a new shell or run `source $HOME/.cargo/env` to have cargo in our path
$ rustup component add rustfmt clippy
```

Thats it! You are now ready to write and execute Rust code.

## Setup your IDE of choice

| IDE                | Installation                                            | Rust Config               |
| ------------------ | ------------------------------------------------------- | ------------------------- |
| Visual Studio Code | [code.visualstudio.com](https://code.visualstudio.com/) | [Setup](/setup/vscode.md) |
| Vim                | [vim.org](https://vim.org/)                             | [Setup](/setup/vim.md)    |
| NeoVim             | [vim.org](https://neovim.io/)                           | [Setup](/setup/vim.md)    |

<!-- Links -->

[`rustup`]: https://rustup.rs/
[`visual studio code`]: /setup/vscode.md
[`vim or neovim`]: /setup/vim.md
