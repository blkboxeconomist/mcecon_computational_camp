---
theme: default
title: Week 4 — Git
info: |
  Computational Camp · Week 4
class: text-center
transition: slide-left
mdc: true
---

# Week 4

## Git and version control

---

# The problem

```
paper_final.tex
paper_final_v2.tex
paper_final_v2_chase.tex
paper_final_v2_chase_ACTUAL_FINAL.tex
```

Add a co-author, six months, a codebase. Miserable.

---

# What Git gives you

- Every saved state tracked
- Every state has a *why* (message)
- Any state can be restored
- Two people can work in parallel and merge

---

# Vocabulary

- **Repo** — directory with a `.git/` history
- **Commit** — snapshot + message + parent
- **Branch** — moveable pointer to a commit
- **Remote** — another copy (usually GitHub)

---

# One-time config

```sh
git config --global user.name  "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --global core.editor "code --wait"
```

---

# Start a repo

```sh
mkdir project && cd project
git init
echo "# project" > README.md
git add README.md
git commit -m "initial commit"
git log
```

Three ideas: **untracked → staged → committed**.

---

# Day-to-day

```sh
git status              # always
git diff                # unstaged changes
git diff --staged       # staged changes
git add <file>
git commit -m "msg"
git log --oneline
```

---

# Branches

```sh
git switch -c feature/intro
# edit, add, commit
git switch main
git merge feature/intro
git branch -d feature/intro
```

Why: PR workflow + keep `main` clean.

---

# Merge conflicts

```
<<<<<<< HEAD
flat
=======
round
>>>>>>> feature
```

Edit to the correct state, remove markers, `git add`, `git commit`.

---

# Remotes

```sh
git remote add origin git@github.com:you/repo.git
git push -u origin main

# elsewhere
git clone git@github.com:you/repo.git

# after that
git push
git pull
```

---

# PR workflow

1. `git switch -c fix/typo`
2. Edit, commit
3. `git push -u origin fix/typo`
4. GitHub → open PR → `main`
5. Review, more commits, approve, merge

---

# `.gitignore`

```
__pycache__/
.venv/
.ipynb_checkpoints/
*.pdf
.DS_Store
```

Commit source. Ignore generated output.

---

# Notebooks + large data

- `.ipynb` diffs are ugly. Options: `nbstripout`, `jupytext`, or live with it
- Large data: `git-lfs` or keep out of Git entirely

---

# Cheat sheet

```sh
git status
git add <file>
git commit -m "..."
git push
git switch -c branch
git merge branch
git clone <url>
```

---
layout: center
class: text-center
---

# Homework 4

Make a branch, commit, push, open a PR.

See `assignments/homework_04.ipynb`.
