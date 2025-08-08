# CLI Tools Presentation

A terminal-based presentation about essential command-line tools for developers, written in Spanish.

## Overview

This repository contains a comprehensive presentation showcasing modern CLI tools that enhance developer productivity. The presentation is designed to be viewed in a terminal using a markdown presentation tool.

## Contents

- **presentation.md** - The main presentation file covering various CLI tools including:
  - `zoxide` - Smart directory navigation
  - `eza` - Modern replacement for `ls`
  - `yazi` - Terminal file explorer
  - `fzf` - Fuzzy finder
  - `tmux` - Terminal multiplexer
  - `lazygit` - Git visual interface
  - `gh` - GitHub CLI
  - `gh copilot` - AI assistance in terminal
  - `neovim` - Modern text editor

- **theme.json** - Custom theme configuration for the presentation with terminal-friendly colors and formatting

## Usage

To view this presentation, you'll need [slides](https://github.com/maaslalani/slides) - a terminal-based markdown presentation tool that supports custom themes.

### Installation

```bash
# Install slides
go install github.com/maaslalani/slides@latest
```

### Running the presentation

```bash
slides presentation.md
```

The presentation is optimized for terminal display with:
- ASCII art headers
- Color-coded sections
- Code examples
- Interactive command demonstrations

## Author

Joaquin Vigna

## Purpose

This presentation aims to introduce developers to powerful CLI tools that can significantly improve their workflow and productivity when working in the terminal environment.