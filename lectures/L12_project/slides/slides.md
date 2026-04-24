---
theme: default
title: Week 12 — Guided project
info: Computational Camp · Week 12
class: text-center
transition: slide-left
mdc: true
---

# Week 12

## Guided project

Two-state Markov chain, end-to-end.

---

# Why this, now

All the camp's tools, in one artifact.

- uv · Git · Python · pytest · LaTeX · (slidev stretch)

No single step is hard. The practice is integration.

---

# The math

```
P = [[p00, p01],
     [p10, p11]]
```

rows sum to 1.

Closed-form stationary:

`π₀ = p₁₀ / (p₀₁ + p₁₀)`
`π₁ = p₀₁ / (p₀₁ + p₁₀)`

Empirical frequency → π as T → ∞.

---

# Three functions

```python
simulate(P, T, seed=0) -> list[int]
empirical_frequency(path) -> dict[int, float]
stationary_distribution(P) -> dict[int, float]
```

Docstring + type hints on each.

---

# The layout

```
camp_project/
├── pyproject.toml
├── src/camp_project/markov.py
├── tests/test_markov.py
├── notebooks/analysis.ipynb
└── paper/main.tex
```

---

# The tests (≥6)

- rows sum to 1 enforced/checked
- symmetric P → π = {0:0.5, 1:0.5}
- `[[1,0],[0,1]]` gives a constant path
- simulate path length = T
- empirical frequencies sum to 1
- your own known-answer case

---

# The writeup (~1 page)

- Abstract / intro
- Math (stationary distribution)
- One figure from the notebook
- One bibliography entry

---

# Stretch goals

- CLI via `uv run camp-project ...`
- Generalize to k states
- Slidev deck
- GitHub Actions running `pytest`

---

# Suggested workflow

1. Scaffold + commit
2. `simulate` + test + commit
3. `empirical_frequency` + test + commit
4. `stationary_distribution` + test + commit
5. Lint + docstrings + commit
6. Branch: writeup · analysis · figure · main.tex
7. PR, self-review, merge

---

# Grading priorities

1. **It runs** on a fresh clone
2. **It's correct**
3. **It's readable**
4. **Tooling is clean** (ruff, commits, .gitignore)

Not graded: picturesque plots, impressive matrices.

---
layout: center
class: text-center
---

# Good luck.

Stay curious. Commit often.
