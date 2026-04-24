---
theme: default
title: Week 2 — Markdown and Jupyter
info: |
  Computational Camp · Week 2
class: text-center
transition: slide-left
mdc: true
---

# Week 2

## Markdown and Jupyter notebooks

---

# Why Markdown?

Shows up in two places constantly:

- Jupyter notebooks (prose cells)
- GitHub (READMEs, issues, PRs)

---

# Headings & emphasis

```md
# Title
## Section
### Subsection
```

*italic*, **bold**, `inline code`, fenced blocks with triple backticks.

---

# Lists

```md
- unordered
- item

1. ordered
2. item
```

Indent two spaces to nest.

---

# Links & images

```md
[Rice](https://www.rice.edu)
![alt](path/to/img.png)
```

Relative paths work inside a repo:

```md
[see L01](../L01_setup/setup.ipynb)
```

---

# Tables

```md
| Week | Topic |
|------|-------|
| 1 | Setup |
| 2 | Markdown |
```

Colons in the separator = alignment.

---

# Math

Inline: `$u'(c_t) = \beta (1+r) u'(c_{t+1})$`

Display:

```md
$$
V(k) = \max_{c,k'} u(c) + \beta V(k')
$$
```

Full LaTeX in week 10.

---

# Jupyter cells

Two kinds: **Markdown** and **code**.

Two modes:

- **Edit** (green border) — `Enter`
- **Command** (blue border) — `Esc`

---

# Must-know shortcuts

(command mode)

- `a` / `b` — insert cell above / below
- `dd` — delete cell
- `m` — to Markdown
- `y` — to code
- `Shift+Enter` — run, move down

---

# The kernel

- The Python process your cells run in
- **Holds state between cells**
- Can be **restarted** (wipes state)

---

# Hidden state — the #1 footgun

```
Cell A: x = 1
Cell B: x = x + 1
Cell C: print(x)
```

Run A, B, B, C → prints `3`. Run A, C → prints `1`.

A reader can't tell which happened from the outputs alone.

---

# The fix

- **Kernel → Restart Kernel and Run All** before sharing
- Write idempotent cells (avoid top-level `x = x + 1`)

---

# Shell escape and magics

```python
!ls /                 # shell command
files = !ls /         # capture output
```

```python
%%time                # cell magic: time this cell
%whos                 # line magic: list live variables
```

---

# Exporting

```sh
uv run jupyter nbconvert --to html your.ipynb
uv run jupyter nbconvert --to pdf  your.ipynb
```

Submit the `.ipynb` for homework.

---
layout: center
class: text-center
---

# Homework 2

Write a short markdown-and-math notebook.

See `assignments/homework_02.ipynb`.
