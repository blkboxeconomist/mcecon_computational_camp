---
theme: default
title: Week 6 — Control flow
info: Computational Camp · Week 6
class: text-center
transition: slide-left
mdc: true
---

# Week 6

## Control flow

---

# Indentation = blocks

4 spaces. Not tabs. Your editor should handle it.

---

# `if` / `elif` / `else`

```python
if x < 0:
    print("negative")
elif x == 0:
    print("zero")
elif x < 10:
    print("small")
else:
    print("large")
```

---

# Ternary

```python
y = a if cond else b
```

```python
status = "adult" if age >= 18 else "minor"
```

---

# `while`

```python
n = 5
while n > 0:
    print(n)
    n -= 1
```

Your job to make the condition become false. Else: infinite loop.

---

# `for` + `range`

```python
for i in range(5):         # 0..4
for i in range(2, 5):      # 2..4
for i in range(0, 10, 2):  # 0,2,4,6,8
for i in range(5, 0, -1):  # 5..1
```

Stop is **exclusive**.

---

# Accumulator pattern

```python
total = 0
for i in range(1, 101):
    total += i
print(total)   # 5050
```

```python
result = 1
for i in range(1, 11):
    result *= i
```

---

# `break` / `continue`

```python
for i in range(100):
    if i > 50 and i % 7 == 0:
        print(i)
        break
```

```python
for i in range(10):
    if i % 2 == 0:
        continue
    print(i)
```

---

# `enumerate`

```python
for i, letter in enumerate("camp", start=1):
    print(i, letter)
```

Use when you need **both** index and value.

---

# Nesting

```python
for i in range(3):
    for j in range(3):
        print(i, j)
```

Each outer iter → full inner loop.

---

# FizzBuzz

```python
for n in range(1, 21):
    if n % 15 == 0:
        print("FizzBuzz")
    elif n % 3 == 0:
        print("Fizz")
    elif n % 5 == 0:
        print("Buzz")
    else:
        print(n)
```

Check `% 15` **first**. Order matters.

---

# `while` vs `for`

- `for` — known count or known iterable
- `while` — condition-driven, unknown count

---
layout: center
class: text-center
---

# Homework 6

Loop and branch problems.

See `assignments/homework_06.ipynb`.
