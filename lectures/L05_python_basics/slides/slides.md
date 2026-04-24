---
theme: default
title: Week 5 — Python basics
info: Computational Camp · Week 5
class: text-center
transition: slide-left
mdc: true
---

# Week 5

## Python basics

---

# Variables

```python
x = 42
name = "Chase"
tuition = 62346.0
a, b = 1, 2
```

No type declaration.

---

# Core types

| Type | Examples |
|------|----------|
| `int` | `1`, `-17`, `1_000_000` |
| `float` | `3.14`, `2e-3` |
| `str` | `"hello"` |
| `bool` | `True`, `False` |

`type(x)` tells you what you have.

---

# Arithmetic

```
+   -   *
/    true division (float)
//   floor division
%    remainder
**   power
```

`0.1 + 0.2 != 0.3`. Compare floats with a tolerance.

---

# Strings: f-strings

```python
name = "Chase"
tuition = 62346.0
print(f"Hi {name}, tuition is ${tuition:,.2f}")
# Hi Chase, tuition is $62,346.00
```

Formats: `{x:.2f}`, `{x:,.2f}`, `{x:>10}`, `{x:<10}`, `{x:^10}`.

---

# String methods

```python
s.strip()
s.lower() / s.upper()
s.replace(a, b)
s.split(sep)
",".join([...])
s.startswith(p) / s.endswith(p)
p in s
```

---

# Slicing

```python
s = "economics"
s[0]      # 'e'
s[-1]     # 's'
s[0:3]    # 'eco'
s[::-1]   # reversed
```

`s[start:stop:step]`. **`stop` is exclusive.**

---

# Comparisons & booleans

```
== != < <= > >=
and  or  not
```

Chain:

```python
18 <= age < 65
```

---

# Truthiness

Falsy: `False`, `None`, `0`, `0.0`, `""`, `[]`, `{}`, `set()`.

Everything else is truthy.

---

# `==` vs `is`

- `==` — same value
- `is` — same object

Use `is None`. Otherwise use `==`.

```python
x is None
```

---

# I/O

```python
print("a", "b", "c")
print("a", "b", sep="|")
print("no newline", end="")

name = input("name? ")
age  = int(input("age? "))
```

`input()` returns a string. Convert if needed.

---

# Conversions

```python
int("42")
float("3.14")
str(42)
bool(0)   # False
```

Watch out: `"7" + 3` is a TypeError.

---
layout: center
class: text-center
---

# Homework 5

Small problems with basics only.

See `assignments/homework_05.ipynb`.
