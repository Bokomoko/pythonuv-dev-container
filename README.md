# Python UV Dev Container

A minimal Alpine-based development container for Python projects with `uv` and `ruff` pre-installed, designed for fast and efficient Python development.

## Overview

This development container provides a lightweight, production-ready Python environment built on Alpine Linux. It comes pre-configured with modern Python tooling including:

- **uv**: Ultra-fast Python package installer and resolver
- **ruff**: An extremely fast Python linter and code formatter
- Pre-configured VS Code extensions for Python development

## Features

### 🚀 Fast Package Management

- **uv** replaces pip with significantly faster package installation and dependency resolution
- Optimized for both development and production workflows

### 🔧 Code Quality Tools

- **ruff** provides lightning-fast linting and formatting
- Replaces multiple tools (flake8, black, isort, etc.) with a single, fast solution

### 🐧 Minimal Alpine Base

- Small image size for faster container startup
- Security-focused with minimal attack surface
- Alpine package manager for system dependencies

### 🔌 VS Code Integration

- Pre-configured with essential Python extensions
- Seamless integration with VS Code Dev Containers
- IntelliSense, debugging, and testing support

## Pre-installed VS Code Extensions

```vscode-extensions
ms-python.python,ms-python.vscode-pylance,charliermarsh.ruff,github.copilot,github.copilot-chat,donjayamanne.python-environment-manager
```

### Extension Details

- **Python** - Core Python language support
- **Pylance** - Advanced Python language server with IntelliSense
- **Ruff** - Fast Python linter and formatter
- **GitHub Copilot** - AI-powered code completion
- **GitHub Copilot Chat** - AI chat features for development
- **Python Environment Manager** - Manage Python environments and packages

## Getting Started

### Prerequisites

- Docker or Podman
- VS Code with Dev Containers extension

### Quick Start

1. **Clone or create your project:**

   ```bash
   git clone <your-repo>
   cd your-project
   ```

2. **Add dev container configuration:**
   Create `.devcontainer/devcontainer.json` with this container configuration.

3. **Open in Dev Container:**
   - Open VS Code
   - Run Command Palette (`Ctrl+Shift+P`)
   - Select "Dev Containers: Reopen in Container"

### Using uv for Package Management

#### Install dependencies

```bash
# Create a new project
uv init my-project
cd my-project

# Add dependencies
uv add requests fastapi

# Add development dependencies
uv add --dev pytest black mypy

# Install from requirements
uv pip install -r requirements.txt
```

#### Create virtual environment

```bash
# Create and activate virtual environment
uv venv
source .venv/bin/activate  # Linux/Mac
```

### Using ruff for Code Quality

#### Linting

```bash
# Lint your code
ruff check .

# Lint with auto-fix
ruff check --fix .

# Check specific files
ruff check src/
```

#### Formatting

```bash
# Format your code
ruff format .

# Check formatting without changes
ruff format --check .
```

#### Configuration

Create a `pyproject.toml` file for ruff configuration:

```toml
[tool.ruff]
line-length = 88
target-version = "py311"

[tool.ruff.lint]
select = ["E", "F", "I", "N", "W", "UP"]
ignore = ["E501"]

[tool.ruff.format]
quote-style = "double"
indent-style = "space"
```

## Container Specifications

### Base Image

- **Alpine Linux** - Latest stable version
- **Python** - Latest Python 3.11+
- **Package Manager** - uv for Python packages, apk for system packages

### Installed Tools

- `uv` - Python package installer and resolver
- `ruff` - Python linter and formatter
- `git` - Version control
- `curl` - HTTP client
- `bash` - Shell environment

### Environment Variables

- `PYTHONPATH` - Configured for project structure
- `UV_CACHE_DIR` - Optimized cache directory
- `PYTHONUNBUFFERED` - Ensures Python output is not buffered

## Development Workflow

### Recommended Project Structure

```text
your-project/
├── .devcontainer/
│   └── devcontainer.json
├── src/
│   └── your_package/
├── tests/
├── pyproject.toml
├── requirements.txt
└── README.md
```

### Common Commands

```bash
# Install project in development mode
uv pip install -e .

# Run tests
python -m pytest

# Lint and format
ruff check --fix .
ruff format .

# Type checking (if mypy is installed)
mypy src/
```

## Performance Benefits

### uv vs pip

- **10-100x faster** package installation
- **Faster dependency resolution**
- **Better caching** mechanisms
- **Compatible** with pip and requirements.txt

### ruff vs traditional tools

- **10-100x faster** than flake8
- **Replaces multiple tools**: black, isort, flake8, pyupgrade
- **Zero configuration** required for most projects
- **Consistent** with Black formatting

## Contributing

1. Fork the repository
2. Create your feature branch
3. Use ruff for code formatting: `ruff format .`
4. Run linting: `ruff check --fix .`
5. Commit your changes
6. Push to the branch
7. Create a Pull Request

## Troubleshooting

### Common Issues

**uv command not found:**

- Ensure the container is built properly
- Check if uv is in PATH: `which uv`

**Ruff not working:**

- Verify installation: `ruff --version`
- Check configuration in pyproject.toml

**VS Code extensions not loading:**

- Rebuild the container
- Check devcontainer.json configuration

### Performance Tips

1. **Use uv for all package operations**
2. **Enable ruff auto-fix in VS Code settings**
3. **Configure pre-commit hooks** with ruff
4. **Use .uvignore** for excluding files from uv operations

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Resources

- [uv Documentation](https://github.com/astral-sh/uv)
- [ruff Documentation](https://github.com/astral-sh/ruff)
- [VS Code Dev Containers](https://code.visualstudio.com/docs/devcontainers/containers)
- [Alpine Linux](https://alpinelinux.org/)
