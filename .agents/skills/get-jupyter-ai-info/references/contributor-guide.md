# Contributor Guide

Source: https://github.com/jupyter-ai-contrib/jupyter-ai-devrepo

## Overview

The `jupyter-ai-devrepo` is a monorepo that provides an editable developer installation of all Jupyter AI subpackages. It uses git submodules — each subpackage is a submodule pointing to its own repo.

## Prerequisites

- `git`
- `uv` (Python package manager)
- `just` (command runner)

No dedicated Python environment needed — `uv` manages a local venv automatically.

Install on macOS:
```bash
brew install uv just
```

Or via conda:
```bash
conda activate base
conda install uv just
```

## Getting Started

```bash
git clone --recurse-submodules https://github.com/jupyter-ai-contrib/jupyter-ai-devrepo.git
cd jupyter-ai-devrepo/
just pull-all       # Switch all submodules to main and pull
just install-all    # Editable install of all packages
just start          # Start JupyterLab
```

## Development Workflow

| After... | Run... |
|----------|--------|
| Editing frontend files in a submodule | `just build` (then refresh browser) |
| Editing backend files | Restart JupyterLab server |
| Editing `pyproject.toml` in a submodule | `just reinstall` + restart server |
| Before opening a PR | `just lint` and `just pytest` |

## Key Commands

### Global (anywhere under devrepo)
- `just start` — Start JupyterLab
- `just clean` — Remove `*.chat` and `*.ipynb` from top-level
- `just sync` — Run `uv sync` (refresh dependency cache)
- `just sync-all` — Install optional submodules too
- `just pull-all` — Update all submodules to latest main
- `just mainline <submodule>` — Update specific submodule(s)
- `just build-all` — Build all frontend assets
- `just install-all` / `just uninstall-all` / `just reinstall-all`

### Local (inside a submodule)
- `just build` — Build frontend assets for current submodule
- `just reinstall` — Re-install current submodule
- `just pytest` — Run tests
- `just lint` — Run linters

## Submodule Workflow

Each submodule is a normal git repo once entered:
```bash
cd jupyter-ai-acp-client/
git checkout -b my-feature
# make changes
git add . && git commit
git push origin my-feature
# open PR on the submodule's repo
```
