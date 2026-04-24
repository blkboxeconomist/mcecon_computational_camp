---
theme: default
title: Week 11 — SWE for economists
info: Computational Camp · Week 11
class: text-center
transition: slide-left
mdc: true
---

# Week 11

## Software engineering for economists

---

# Three payoffs

1. Reproducibility — paper's results run years from now
2. Collaboration — co-authors `uv sync` and go
3. Your future self — no two days unbreaking last year's code

All the tools below set up in under 10 minutes.

---
layout: section
---

# Advanced uv

---

# Lockfiles

```sh
uv sync             # install exact env from lock
uv lock --upgrade   # bump versions within constraints
```

Commit `uv.lock`.

---

# Dependency groups

```toml
[project]
dependencies = ["numpy>=2.0"]

[dependency-groups]
dev = ["pytest>=8", "ruff>=0.8"]
```

```sh
uv sync                    # prod only
uv sync --group dev        # + tools
```

---

# Workspaces

```toml
[tool.uv.workspace]
members = ["core", "paper_ajr"]
```

One lock, coherent versions across packages.

Not needed in the camp.

---
layout: section
---

# Ruff

---

# Format + lint

```sh
uv run ruff format .
uv run ruff check .
uv run ruff check --fix .
```

Configure once:

```toml
[tool.ruff]
line-length = 100

[tool.ruff.lint]
select = ["E", "F", "I", "UP", "B", "SIM"]
ignore = ["E501"]
```

Format on save in your editor. Done.

---
layout: section
---

# pytest

---

# Layout

```
src/econtools/growth.py
tests/test_growth.py
```

---

# A test

```python
from econtools.growth import yoy_growth


def test_positive_growth():
    assert yoy_growth(100, 110) == 0.10


def test_zero_start_raises():
    import pytest
    with pytest.raises(ZeroDivisionError):
        yoy_growth(0, 100)
```

```sh
uv run pytest
uv run pytest -v
```

---

# Parametrize

```python
@pytest.mark.parametrize("prev,curr,expected", [
    (100, 110, 0.10),
    (200, 100, -0.50),
])
def test_growth(prev, curr, expected):
    assert yoy_growth(prev, curr) == pytest.approx(expected)
```

---

# What to test

- Core numerical routines
- Edge cases (zero, empty, off-by-one)
- Known-answer toy cases

Not 100% coverage. Coverage **where it matters**.

---

# Docstrings + doctests

```python
def yoy_growth(prev, curr):
    """YoY growth rate.

    Examples
    --------
    >>> yoy_growth(100, 110)
    0.09999999999999998
    """
    return (curr - prev) / prev
```

`pytest --doctest-modules`.

---

# Pre-commit

```yaml
repos:
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.8.0
    hooks:
      - id: ruff-format
      - id: ruff-check
```

`uv run pre-commit install`. Commit refused if bad.

---

# Project layout

```
my_paper/
├── pyproject.toml
├── uv.lock
├── src/my_paper/
├── tests/
├── notebooks/
├── paper/      (LaTeX)
└── data/raw/
```

Boring and consistent.

---
layout: center
class: text-center
---

# Homework 11

Turn a messy script into a package.

See `assignments/homework_11.ipynb`.
