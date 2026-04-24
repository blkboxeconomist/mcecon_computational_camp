---
theme: default
title: Week 7 — Collections
info: Computational Camp · Week 7
class: text-center
transition: slide-left
mdc: true
---

# Week 7

## Collections

---

# Four types, four trade-offs

| | ordered | mutable | unique | lookup |
|-|---------|---------|--------|--------|
| `list` | ✓ | ✓ | ✗ | index |
| `tuple` | ✓ | ✗ | ✗ | index |
| `set` | ✗ | ✓ | ✓ | membership |
| `dict` | ✓* | ✓ | keys | key |

---

# Lists

```python
gdp = [1000, 1050, 1103, 1158]
gdp[0]            # 1000
gdp[-1]           # 1158
gdp[1:3]          # [1050, 1103]
gdp.append(1210)
gdp.pop()
sorted(gdp)
sum(gdp)
```

---

# Iteration

```python
for v in gdp:
    ...

for i, v in enumerate(gdp):
    ...
```

---

# Tuples

```python
point = (3.0, 4.0)
x, y = point          # unpack
a, b = b, a           # swap
```

Use when the values are fixed and meaningful *together*.

---

# Dicts

```python
gdp = {"USA": 25_000, "CHN": 17_700}
gdp["USA"]
gdp.get("FRA", 0)
gdp["JPN"] = 4_300
del gdp["USA"]

for k, v in gdp.items():
    ...
```

---

# Sets

```python
s = {"USA", "CHN"}
s.add("DEU")
s | other    # union
s & other    # intersection
s - other
```

No duplicates. Fast membership.

---

# Comprehensions

```python
squares      = [n*n for n in range(10)]
even_squares = [n*n for n in range(10) if n % 2 == 0]
letters      = {c.lower() for c in "Economics" if c.isalpha()}
scaled       = {k: v/1000 for k, v in gdp.items()}
```

One expression. If the body grows, use a regular `for`.

---

# `zip`

```python
years = [2020, 2021]
gdp   = [1000, 1050]

for y, v in zip(years, gdp):
    ...

d = dict(zip(years, gdp))
```

---

# Choosing

- Look up by label → **dict**
- Uniqueness → **set**
- Fixed small group → **tuple**
- Ordered, growable → **list**

---
layout: center
class: text-center
---

# Homework 7

Data wrangling with collections.

See `assignments/homework_07.ipynb`.
