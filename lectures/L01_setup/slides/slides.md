---
theme: default
title: Week 1 — Getting set up
info: |
  Computational Camp · Week 1

  uv, Python, editor, Jupyter
class: text-center
transition: slide-left
mdc: true
---

# Week 1

## Getting set up

uv · Python · editor · Jupyter

Computational Camp

---
layout: default
---

# Why we spend a whole week on tooling

- Most "Python problems" for new researchers aren't Python problems
- They're environment problems
  - *"Which Python am I running?"*
  - *"My notebook worked yesterday and now it doesn't."*
  - *"You ran my code and got a different number."*
- A clean toolchain makes 80% of this disappear

---

# What we'll install today

| Tool | Role |
|------|------|
| `uv` | Manages Python versions, project envs, dependencies |
| Python | Installed *through* `uv` |
| VS Code *or* Zed | Text editor (pick one) |
| JupyterLab | Notebook interface |

---
layout: section
---

# Part 1

## Install `uv`

---

# Install `uv`

**macOS / Linux**

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```

**Windows (PowerShell)**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Then: close + reopen your terminal.

Verify:

```sh
uv --version
```

---
layout: section
---

# Part 2

## Install Python through `uv`

---

# Install a Python

```sh
uv python install 3.12
```

- Downloads a standalone Python 3.12
- Does **not** touch your system Python
- Each project can pin its own version

List what's installed:

```sh
uv python list --only-installed
```

---
layout: section
---

# Part 3

## Your first project

---

# `uv init`

```sh
mkdir ~/camp-sandbox
cd ~/camp-sandbox
uv init --python 3.12
```

Creates:

```
camp-sandbox/
├── .python-version
├── main.py
├── pyproject.toml
└── README.md
```

`pyproject.toml` = single source of truth.

---

# `uv run`

```sh
uv run main.py
```

First time: creates `.venv/`, installs Python, runs the command.

Every time after: instant.

**You never activate a virtualenv by hand.**

---

# Adding dependencies

```sh
uv add jupyterlab ipykernel
```

Two things happen:

- Package is installed into `.venv/`
- Requirement is written into `pyproject.toml`

A `uv.lock` file records exact versions. **Commit it.** `uv sync` on a
collaborator's machine reproduces your environment.

---
layout: section
---

# Part 4

## Editor

---

# Pick an editor: VS Code *or* Zed

Both are free, cross-platform, and fine for camp.

**[VS Code](https://code.visualstudio.com)** — the common default

- Huge extension ecosystem
- Integrates with every AI assistant
- What most classmates will use

**[Zed](https://zed.dev)** — leaner, faster

- Python + LSP support out of the box
- Native `.ipynb` notebook UI
- Built-in AI features

---

# Editor setup

**VS Code** — install these extensions:

- Python (Microsoft)
- Jupyter (Microsoft)
- Ruff (Astral)

**Zed** — mostly built-in:

- Python LSP (Pyright) shipped by default
- Add Ruff as formatter in `~/.config/zed/settings.json`
- `.ipynb` files open as notebooks natively

---

# Other editors you might hear about

- **Cursor** — VS Code + AI; week 9
- **PyCharm** — heavier IDE; fine if you already use it
- **Vim / Neovim / Helix** — steep learning curve; not for week 1

---
layout: section
---

# Part 5

## JupyterLab

---

# Launch it

From your project directory:

```sh
cd ~/camp-sandbox
uv run jupyter lab
```

Opens a browser. File → New → Notebook. Pick the Python 3 kernel.

Type a cell, press **Shift+Enter**.

---

# First cell

```python
import sys
print("Python:", sys.version.split()[0])
print("Hello, camp!")
```

---
layout: section
---

# Gotchas

---

# Gotchas

- *"`uv` command not found"* → new terminal; follow PATH hint
- *"Which Python?"* → inside a project, always `uv run python`
- *"Jupyter can't find my packages"* → `cd` into project, prefix `uv run`
- Conda/pyenv/pipx already installed? Leave them alone; use `uv` for camp

---

# Cheat sheet

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh

uv python install 3.12

uv init --python 3.12
uv add <package>
uv sync
uv run python
uv run jupyter lab
```

---
layout: center
class: text-center
---

# Homework 1

Verify your setup on your own machine.

See `assignments/homework_01.ipynb`.
