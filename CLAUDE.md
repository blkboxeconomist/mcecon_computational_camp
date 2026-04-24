# Guidance for AI collaborators on this repo

This is a 12-week computational camp for incoming Rice computational
economics master's students. Its role is to cover **foundations and tooling
only**. Four downstream courses own the heavy libraries:

- Data → pandas
- Math → numpy / scientific stack
- Dynamics → dynamic programming, RL
- ML → PyTorch, JAX

**Do not** introduce numpy, pandas, or PyTorch as first-class camp content.
If an example needs a quick visualization, matplotlib is acceptable, but do
not teach it as a topic.

## Conventions

- Lectures live under `lectures/LXX_topic/` and consist of a walkthrough
  notebook, a `README.md` with learning objectives, and a `slides/`
  subfolder containing a slidev deck.
- Slides are **slidev**, not reveal.js or Quarto. Each lecture is an
  independent slidev project (`slides/package.json`, `slides/slides.md`).
- Assignments live under `assignments/homework_XX.ipynb`. Week 12's
  capstone is a directory (`assignments/homework_12/`).
- Python environment is managed with `uv`. Use `uv add <pkg>` to add
  dependencies and `uv run jupyter lab` to work.

## Notebook style

Follow the rhythm of `~/teaching/Rice/S2026/ECON-434/lectures/L01_linear_models/linear_models.ipynb`:

- Markdown cells heavy on prose, LaTeX math via `$...$`.
- Short, single-purpose code cells — one idea per cell.
- Code cells that produce output rather than define helpers are preferred
  when showing a concept for the first time.
- Headings are concrete and topical, not "Section 3".

## Audience

Incoming master's students with a mixed background. Assume nothing — some
have never opened a terminal; others have written Python before. When in
doubt, explain the *why* alongside the *how*.
