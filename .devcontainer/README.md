# BidFlow Analysis DevContainer

This directory contains the configuration files for the Visual Studio Code DevContainer used in the BidFlow Analysis project. The DevContainer provides a consistent development environment with all necessary tools pre-installed.

## What's Included

### Core Tools
- **Deno**: JavaScript/TypeScript runtime
- **Node.js and npm**: JavaScript runtime and package manager
- **PowerShell**: Cross-platform task automation and configuration management framework
- **Pandoc**: Universal document converter (for Markdown to Word conversion)
- **Python 3 and pip**: Python programming language and package manager
- **Git**: Version control system

### Utility Tools
- **jq**: Command-line JSON processor
- **curl**: Command-line tool for transferring data with URLs
- **wget**: Network utility for retrieving files from the web
- **unzip**: Extraction utility for zip archives

### VS Code Extensions
- **Deno**: Deno language support
- **Claude Dev**: Claude AI integration
- **PowerShell**: PowerShell language support
- **Markdown All in One**: Markdown editing and preview features
- **Markdown Preview GitHub Styles**: GitHub-styled Markdown preview
- **Code Spell Checker**: Spell checking for code and documentation
- **markdownlint**: Markdown linting and style checking
- **Python**: Python language support

## Custom Tools

### md2docx
A custom wrapper script around pandoc that provides the same interface as the md2docx CLI tool. This script is automatically installed in the container and available in the PATH.

Usage:
```bash
md2docx -i input.md                      # Basic usage
md2docx -i input.md -r reference.docx    # With reference document for styling
md2docx -i input.md -o output.docx       # With custom output filename
md2docx -i input.md -toc                 # Include table of contents
md2docx -i input.md -extraArgs "--number-sections"  # Pass additional pandoc arguments
```

The script provides the same interface as the original md2docx tool but uses pandoc as the underlying conversion engine, offering more features and better document conversion quality.

## Setup Instructions

1. Install [Visual Studio Code](https://code.visualstudio.com/)
2. Install the [Remote - Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers) extension
3. Clone the BidFlow Analysis repository
4. Open the repository in VS Code
5. When prompted, click "Reopen in Container" or use the command palette (F1) and select "Remote-Containers: Reopen in Container"
6. Wait for the container to build and start (this may take a few minutes the first time)

## Using the DevContainer

Once the DevContainer is running:

1. The terminal will default to PowerShell
2. All tools listed above are available in the PATH
3. VS Code extensions are pre-installed and configured

## Customizing the DevContainer

If you need to customize the DevContainer:

1. Edit `devcontainer.json` to change VS Code settings or extensions
2. Edit `Dockerfile` to add or modify installed packages
3. Rebuild the container using the command palette: "Remote-Containers: Rebuild Container"
