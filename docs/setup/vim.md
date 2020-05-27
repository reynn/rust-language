# Vim/NVim <!-- omit in toc -->

- [Conquer of Completion (CoC)](#conquer-of-completion-coc)
  - [Vim Plug](#vim-plug)
  - [CoC](#coc)
  - [CoC Extensions](#coc-extensions)
- [SpaceVim](#spacevim)
- [Other Vim plugin suggestions](#other-vim-plugin-suggestions)

## Conquer of Completion (CoC)

CoC is an autocomplete engine that uses Language Servers to provide completions for many languages.

### Vim Plug

First step is to install CoC using Vim Plug or any other plugin manager.

[VimPlug Setup](https://github.com/junegunn/vim-plug#installation)

```shell
$ curl -fLo ~/.vim/autoload/plug.vim --create-dirs https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```

Once vim-plug exists in the autoload directory it can start managing plugins.

### CoC

[CoC Setup](https://github.com/neoclide/coc.nvim#quick-start)

With Vim Plug installed it is just a matter of adding the CoC plugin and its keybindings.

```vim
" Specify a directory for plugins
" - For Neovim: stdpath('data') . '/plugged'
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')

" Use release branch (Recommend)
Plug 'neoclide/coc.nvim', {'branch': 'release'}

" Initialize plugin system
call plug#end()
```

Save this in your ~/.vimrc or init.vim file. In a new shell run the command `vim -c 'PlugInstall | qall`. This will install our plugins and quit. Now we can open a new vim instance and have CoC enabled.

I would suggest using the [example config](https://github.com/neoclide/coc.nvim#example-vim-configuration) to get started and customize as you need.

### CoC Extensions

[Extensions overview](https://github.com/neoclide/coc.nvim/wiki/Using-coc-extensions)

Extensions add functionality to CoC such as interacting with Language servers over LSP. I suggest adding any extensions you want to use to `g:coc_global_extensions` in your `.vimrc` or `init.vim` file.

```vim
let g:coc_global_extensions = ['coc-actions', 'coc-rust-analyzer', 'coc-json', 'coc-yank']
```

## SpaceVim

SpaceVim is a complete Vim configuration. Read through the documentation provided by spacevim for full overview of how to best use it.

[GitHub Page](https://github.com/SpaceVim/SpaceVim)
[Setup as Rust IDE](https://spacevim.org/use-vim-as-a-rust-ide/)

## Other Vim plugin suggestions

| Name                                                                    | Description                                               |
| ----------------------------------------------------------------------- | --------------------------------------------------------- |
| [Recover.vim](https://github.com/chrisbra/Recover.vim)                  | Show a diff of the swap file before loading               |
| [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim)                      | Fuzzy finding of files, buffers and more                  |
| [editorconfig-vim](https://github.com/editorconfig/editorconfig-vim)    | Use of .editorconfig files to set indentation etc         |
| [vim-easy-align](https://github.com/junegunn/vim-easy-align)            | Handle aligning text                                      |
| [vim-sayonara](https://github.com/mhinz/vim-sayonara)                   | Deletes the buffer and handles windows more intelligently |
| [vim-fugitive](https://github.com/tpope/vim-fugitive)                   | Extensive Git integration added to Vim                    |
| [vim-repeat](https://github.com/tpope/vim-repeat)                       | Beef up the default . repeater                            |
| [vim-rhubarb](https://github.com/tpope/vim-rhubarb)                     | Add fancy extras for GitHub to the vim-fugitive plugin    |
| [vim-which-key](https://github.com/liuchengxu/vim-which-key)            | Keybinding manager                                        |
| [nerdtree-git-plugin](https://github.com/Xuyuanp/nerdtree-git-plugin)   | Add git information to NerdTree                           |
| [vim-gitgutter](https://github.com/airblade/vim-gitgutter)              | Show git changes in margin of file buffer                 |
| [vim-matchup](https://github.com/andymass/vim-matchup)                  | Highlight, navigate and operate on sets of matching text  |
| [vim-rainbow](https://github.com/frazrepo/vim-rainbow)                  | Colorize tabs, parens to make them easier to see          |
| [lightline.vim](https://github.com/itchyny/lightline.vim)               | Adds a powerline like status bar at the bottom            |
| [vim-highlightedyank](https://github.com/machakann/vim-highlightedyank) | Highlights line after y is pressed                        |
| [tabman.vim](https://github.com/noscripter/tabman.vim)                  | Simple management of tabs in Vim                          |
| [nerdtree](https://github.com/preservim/nerdtree)                       | File Explorer tab                                         |
| [vim-session](https://github.com/xolox/vim-session)                     | Extended session management for Vim                       |
| [papercolor-theme](https://github.com/NLKNguyen/papercolor-theme)       | Light theme                                               |
| [gruvbox](https://github.com/morhetz/gruvbox)                           | Configurable dark mode theme                              |
| [dracula](https://github.com/dracula/vim)                               | Configurable dark mode theme                              |
| [fzf](https://github.com/junegunn/fzf)                                  | Fuzzy finding inside Vim/NVim                             |
| [fzf.vim](https://github.com/junegunn/fzf.vim)                          | Additional Vim setup for FZF                              |
| [vim-markdown-toc](https://github.com/mzlogin/vim-markdown-toc)         | Manage ToC sections for Markdown files                    |
| [vim-toml](https://github.com/cespare/vim-toml)                         | Add support for TOML files                                |
