---
theme: default
title: Week 9 — AI coding, debug, OOP
info: Computational Camp · Week 9
class: text-center
transition: slide-left
mdc: true
---

# Week 9

## AI coding · Debugging · Tiny OOP

---
layout: section
---

# Part 1 — AI coding

---

# Three flavors

| Tool | What |
|------|------|
| Copilot | autocomplete |
| Cursor | IDE + chat + agent |
| Claude Code | terminal agent |

Pick one. Learn it deeply.

---

# Where it helps

- Boilerplate
- Unfamiliar libraries
- Explaining tracebacks
- Language translation (R → Python)

---

# Where it hurts

- Novel research code
- Numerical correctness
- Performance

**Always verify. Don't trust the math.**

---

# Prompting patterns

1. Tell it the goal, not the code
2. Give it the context (data shape, error msg, function)
3. Ask for tests
4. Push back when wrong
5. Don't trust the math

---

# Responsibly

- Understand before you submit
- Some assignments will say "no AI"
- Your grade is for what **you** know

---
layout: section
---

# Part 2 — Tracebacks

---

# Read from the bottom

At the bottom:

- **Exception class** (e.g. `ZeroDivisionError`)
- **Message** (e.g. `division by zero`)

Above: the call stack. File + line for each frame.

Walk up until you find your code.

---

# Common exceptions

| | |
|-|-|
| `NameError` | typo |
| `TypeError` | `"7" + 3` |
| `ValueError` | `int("abc")` |
| `KeyError` | missing dict key |
| `IndexError` | list out of range |
| `AttributeError` | no such method |
| `ImportError` | package not installed |
| `FileNotFoundError` | path doesn't exist |

---
layout: section
---

# Part 3 — `try` / `except`

---

# Catch specifically

```python
def safe_int(text):
    try:
        return int(text)
    except ValueError:
        return None
```

- **Specific** exception, not bare `except`
- Not for normal control flow
- `raise` to re-throw

---
layout: section
---

# Part 4 — `breakpoint()`

---

# Drop a pin

```python
def f(xs):
    total = 0
    for v in xs:
        breakpoint()
        total += v / 2
```

`pdb` commands:

`p x` print · `n` next · `s` step · `c` continue · `l` list · `q` quit

Also: descriptive `print` statements. Don't over-engineer.

---
layout: section
---

# Part 5 — Tiny OOP

---

# `@dataclass`

```python
from dataclasses import dataclass

@dataclass
class Student:
    name: str
    major: str
    gpa: float

alice = Student("Alice", "econ", 3.7)
```

Auto-generated `__init__`, `__repr__`, equality.

---

# Methods

```python
@dataclass
class Student:
    name: str
    gpa: float

    def honors(self) -> bool:
        return self.gpa >= 3.7
```

---

# Reading library code

```python
model = LinearRegression()
model.fit(X, y)
preds = model.predict(X_new)
```

- `LinearRegression` — class
- `model` — instance
- `.fit`, `.predict` — methods
- State lives inside the object

Enough to read; deep OOP in ML/dynamics courses.

---
layout: center
class: text-center
---

# Homework 9

Fix a broken notebook.

See `assignments/homework_09.ipynb`.
