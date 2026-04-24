---
theme: default
title: Week 8 — Functions
info: Computational Camp · Week 8
class: text-center
transition: slide-left
mdc: true
---

# Week 8

## Functions

---

# Why

1. **Naming** — abstract the surrounding code
2. **Reuse** — write once, call many
3. **Testing** — pure functions are easy to test

"Copy-pasted twice? Make a function."

---

# Shape

```python
def name(params):
    """Docstring."""
    body
    return value
```

No `return` → returns `None`.

---

# Return tuples

```python
def min_max(xs):
    return min(xs), max(xs)

lo, hi = min_max([3, 1, 4])
```

---

# Positional, keyword, default

```python
def wage(hours, rate=25.0):
    return hours * rate

wage(40)
wage(40, 30.0)
wage(rate=30.0, hours=40)
```

---

# Mutable-default trap

```python
def bad(item, bucket=[]):
    bucket.append(item)
    return bucket

bad(1)   # [1]
bad(2)   # [1, 2]   # same list!
```

Fix with `bucket=None`, then `if bucket is None: bucket = []`.

---

# `*args` and `**kwargs`

```python
def mean(*values):
    return sum(values) / len(values)

mean(1, 2, 3)

def config(**options):
    for k, v in options.items(): ...

config(alpha=0.5, n=100)
```

---

# Type hints

```python
def wage(hours: float, rate: float) -> float:
    return hours * rate
```

Common:

```python
list[float], dict[str, float], int | None
```

Editor + `ruff`/`mypy` see them. Runtime doesn't enforce them.

---

# Scope (LEGB)

**L**ocal → **E**nclosing → **G**lobal → **B**uilt-in.

Local variables don't leak. Don't assign to globals inside a function.

---

# Pure vs side-effecting

**Pure**: same inputs → same output, no mutation.

Favor pure. Isolate side effects to small functions.

---

# Compose small functions

```python
def mean(xs): ...
def demean(xs): ...
def variance(xs): ...
```

One thing each. Easy to test.

---

# Informal testing

```python
assert yoy_growth(100, 110) == 0.10
assert yoy_growth(200, 100) == -0.50
```

Week 11: `pytest`.

---
layout: center
class: text-center
---

# Homework 8

Write and test a small library of pure functions.

See `assignments/homework_08.ipynb`.
