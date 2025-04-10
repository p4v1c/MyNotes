---
title: Vim
description: ""
summary: ""
date: 2023-09-07T16:06:50+02:00
lastmod: 2023-09-07T16:06:50+02:00
draft: false
weight: 800
toc: true
sidebar:
  collapsed: true
seo:
  title: ""
  description: ""
  canonical: ""
  robots: ""
  noindex: false
---
# Vim

## 🚀 BASIC MOVEMENT

| Command    | What it does                                 |
| ---------- | -------------------------------------------- |
| `h` / `l`  | Left / right                                 |
| `j` / `k`  | Down / up                                    |
| `w` / `b`  | Next word / previous word                    |
| `0` / `^`  | Start of line (0 = column 0, ^ = first char) |
| `$`        | End of line                                  |
| `gg` / `G` | Top / bottom of file                         |
| `ctrl-d/u` | Half-page down / up                          |
| `zz`       | Center cursor                                |

## 🧹 EDITING FAST

| Command   | What it does                      |
| --------- | --------------------------------- |
| `i` / `I` | Insert / Insert at start of line  |
| `a` / `A` | Append / Append at end of line    |
| `o` / `O` | Open new line below / above       |
| `r<char>` | Replace one character             |
| `R`       | Replace mode (overwrite)          |
| `x` / `X` | Delete char under / before cursor |
| `u`       | Undo                              |
| `ctrl-r`  | Redo                              |
| `.`       | Repeat last change                |

## ✂️ COPY / PASTE / DELETE (YANK / PUT)

| Command      | What it does                 |
| ------------ | ---------------------------- |
| `yy` / `Y`   | Yank (copy) line             |
| `dd`         | Delete (cut) line            |
| `p` / `P`    | Paste after / before cursor  |
| `yw` / `dw`  | Yank / Delete word           |
| `d$` / `y$`  | Delete / Yank to end of line |
| `:registers` | Show copy/paste registers    |

## 🎯 NAVIGATING BETWEEN FILES / BUFFERS / TABS

| Command             | What it does           |
| ------------------- | ---------------------- |
| `:e file`           | Open file              |
| `:w` / `:wq`        | Save / Save & quit     |
| `:q!`               | Quit without saving    |
| `:bn` / `:bp`       | Next / Previous buffer |
| `:ls` or `:buffers` | List open buffers      |
| `:tabnew file`      | Open file in new tab   |
| `gt` / `gT`         | Next / Previous tab    |
## 🔍 FIND & REPLACE

| Command           | What it does                    |
| ----------------- | ------------------------------- |
| `/word` / `?word` | Search forward / backward       |
| `n` / `N`         | Repeat search (next / previous) |
| `:%s/foo/bar/g`   | Replace all "foo" with "bar"    |
| `:%s/foo/bar/gc`  | Replace with confirmation       |
## 🧠 POWER MOVES

| Command              | What it does                         |
| -------------------- | ------------------------------------ |
| `ciw`                | Change inside word                   |
| `ci"` / `ci'`        | Change inside quotes                 |
| `ci(` / `ci{`        | Change inside parens/braces          |
| `v` / `V` / `ctrl-v` | Visual (char/line/block) mode        |
| `>` / `<` in visual  | Indent / Unindent                    |
| `:!command`          | Run shell command (e.g. `:!ls`)      |
| `:w !sudo tee %`     | Save with sudo when access is denied |

## 💠 Multiline Editing

| Mode / Shortcut   | What it does                                   |
| ----------------- | ---------------------------------------------- |
| `Ctrl + v`        | Enter **visual block** mode (column selection) |
| `j / k`           | Move up/down to expand selection vertically    |
| `I` (uppercase i) | Insert text at **start** of all selected lines |
| `A`               | Append text at **end** of all selected lines   |
| `x`               | Delete selected **columns**                    |
| `d`               | Delete selected **block**                      |
| `r<char>`         | Replace block with a single character          |

- Substitution :
```sh
Ctrl+v
:%s/:.*//
```
Don't forget to press `Esc`

**`:%s`** → applies the substitution to **all lines** in the file.
**`:`** → matches the literal colon character.
**`.*`** → matches **everything that comes after** the colon.
**`//`** → replaces the matched text with nothing (i.e., deletes it).

- Config file :

```sh
set number              " Line numbers
set relativenumber      " Relative lines
set clipboard=unnamed   " Use system clipboard
set tabstop=4           " Tabs = 4 spaces
set shiftwidth=4
set expandtab
syntax on               " Highlight code
set hlsearch incsearch  " Highlight + incremental search
```

# NeoVim

- Resource config file :
https://github.com/ntk148v/neovim-config/tree/master?tab=readme-ov-file#2-installation