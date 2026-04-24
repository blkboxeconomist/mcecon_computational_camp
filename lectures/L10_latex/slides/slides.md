---
theme: default
title: Week 10 — LaTeX
info: Computational Camp · Week 10
class: text-center
transition: slide-left
mdc: true
---

# Week 10

## LaTeX

---

# Why

- Economics papers are typeset in LaTeX
- Content vs layout: swap document class, not words
- Huge ecosystem of templates + packages

---

# Install

- `tectonic` — single binary, auto-downloads packages
- Overleaf — web-based, no install
- TeX Live + `latexmk` — heavier; fine if already installed

---

# Minimal document

```tex
\documentclass[11pt]{article}
\usepackage{amsmath}

\begin{document}
Hello, world.

$E = mc^2$
\end{document}
```

Compile: `tectonic hello.tex` → `hello.pdf`.

---

# Usual preamble

```tex
\documentclass[11pt]{article}
\usepackage[a4paper, margin=1in]{geometry}
\usepackage{amsmath, amssymb}
\usepackage{graphicx}
\usepackage{booktabs}
\usepackage[style=authoryear]{biblatex}
\addbibresource{refs.bib}
\usepackage{hyperref}
```

---

# Math: inline and display

```tex
Inline: $c + s = y$.

\[
V(k) = \max_{c,k'}\; u(c) + \beta V(k')
\]
```

Numbered:

```tex
\begin{equation}
  \label{eq:bellman}
  V(k) = ...
\end{equation}

Equation~\eqref{eq:bellman} ...
```

---

# Aligned math

```tex
\begin{align}
  u'(c_t) &= \beta (1+r) u'(c_{t+1}) \\
  c_t + s_t &= y_t + (1+r) s_{t-1}
\end{align}
```

`&` = align point. `\\` = new line.

---

# Tables (booktabs)

```tex
\begin{tabular}{lrr}
  \toprule
  Country & 2022 & 2023 \\
  \midrule
  USA     & 2.1  & 2.5 \\
  China   & 3.0  & 5.2 \\
  \bottomrule
\end{tabular}
```

No vertical rules.

---

# Figures

```tex
\begin{figure}[h]
  \centering
  \includegraphics[width=0.7\linewidth]{plot.pdf}
  \caption{...}
  \label{fig:gdp}
\end{figure}
```

`matplotlib` can `savefig("plot.pdf")`.

---

# Bibliography

```bibtex
% refs.bib
@article{acemoglu2001,
  author = {...},
  title  = {...},
  year   = {2001},
}
```

```tex
\parencite{acemoglu2001}
\textcite{acemoglu2001}
\printbibliography
```

---

# Special characters

`\%`  `\&`  `\$`  `\#`  `\_`

`~` non-breaking space: `Figure~1`, `Prof.~Smith`.

`--` en-dash (pages). `---` em-dash.

---

# Debugging

- Scroll to the **first** error
- `Undefined control sequence` → typo or missing `\usepackage`
- `Missing $ inserted` → unescaped `%`, `&`, `#`, `_`
- Refs often need **two** compilations

---
layout: center
class: text-center
---

# Homework 10

Write a one-page econ-style document.

See `assignments/homework_10.ipynb`.
