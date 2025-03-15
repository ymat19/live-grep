# live-grep-bash

An interactive command-line tool that combines fzf, ripgrep, and bat for real-time file content search.

[日本語のREADME](README.ja.md)

## Features

- Real-time search results display
- Syntax-highlighted preview
- Easy file path extraction from search results

## Requirements

- fzf
- ripgrep (rg)
- bat
- bash 4.0+
- curl

## Installation

Install/Update:

```bash
mkdir -p "${XDG_BIN_HOME:-$HOME/.local/bin}" && curl -fsSL https://raw.githubusercontent.com/ymat19/live-grep-bash/main/live-grep -o "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep" && chmod +x "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep"
```

Uninstall:

```bash
rm "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep"
```

**Note**: Make sure the installation directory is in your PATH. If not, add the following to your ~/.bashrc or ~/.zshrc:

```bash
export PATH="${XDG_BIN_HOME:-$HOME/.local/bin}:$PATH"
```

## Usage

### Basic Usage

```bash
# Search in current directory
live-grep

# Search in specific directory
live-grep src/
```

### Options

```bash
# Search specific file extensions
live-grep -p "*.rs"

# Set number of context lines
live-grep -c 5

# Exclude specific directories
live-grep -e "node_modules/"
```

### Pipeline Usage

```bash
# Open selected file in Vim
live-grep | xargs vim

# Display selected file content
live-grep | xargs cat
```

### Key Bindings

- Type to search in real-time
- Navigate results with arrow keys
- Press Enter to output selected file path
- Press Ctrl-C to exit

## Options List

- `-p, --pattern PATTERN`: File pattern to search (e.g., "*.rs")
- `-d, --depth DEPTH`: Maximum search depth
- `-c, --context LINES`: Number of context lines in preview (default: 2)
- `-e, --exclude PATTERN`: Exclude pattern
- `-h, --help`: Show help message
- `-v, --version`: Show version

## License

MIT License - See [LICENSE](LICENSE) for details
