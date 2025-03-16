# live-grep-cli

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
mkdir -p "${XDG_BIN_HOME:-$HOME/.local/bin}" && curl -fsSL https://raw.githubusercontent.com/ymat19/live-grep-cli/main/live-grep -o "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep" && chmod +x "${XDG_BIN_HOME:-$HOME/.local/bin}/live-grep"
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

# Search with line numbers in output
live-grep -n  # outputs like "file:80"
```

### Options

```bash
# Set number of context lines
live-grep -c 5
```

### Pipeline Usage

```bash
# Open selected file in Vim
live-grep | xargs vim

# Open file at specific line (with -n option)
live-grep -n | awk -F: '{print "+"$2" "$1}' | xargs vim
```

### VS Code Usage

```bash
# Open file in VS Code from integrated terminal
code --reuse-window -g $(live-grep -n)
```

### Key Bindings

- Type to search in real-time
- Navigate results with arrow keys
- Press Enter to output selected file path
- Press Ctrl-C to exit

## Options List

- `-d, --depth DEPTH`: Maximum search depth
- `-c, --context LINES`: Number of context lines in preview (default: 2)
- `-n, --line-number`: Output file path with line number
- `-h, --help`: Show help message
- `-v, --version`: Show version

## License

MIT License - See [LICENSE](LICENSE) for details
