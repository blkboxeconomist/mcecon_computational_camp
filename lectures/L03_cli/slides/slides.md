---
theme: default
title: Week 3 — Command line
info: |
  Computational Camp · Week 3
class: text-center
transition: slide-left
mdc: true
---

# Week 3

## Command line, shells, terminal

---

# Terminal vs. shell vs. prompt

- **Terminal** = the app (draws text)
- **Shell** = the program inside (interprets commands)
- **Prompt** = what the shell prints before your input

We'll use **zsh** (macOS) / **bash** (Linux). Windows: WSL or Git Bash.

---

# Navigation

```sh
pwd               # where am I
ls                # what's here
ls -la            # long format, including dot-files
cd ~              # home
cd /tmp           # absolute
cd ../other       # relative
cd -              # back
```

`~` = home, `.` = here, `..` = parent.

---

# Reading files

```sh
cat  file.txt        # whole file
less file.txt        # pager (q to quit)
head -n 5 file.txt
tail -n 5 file.txt
tail -f log.txt      # follow
```

---

# Pipes

```sh
ls | wc -l
```

Output of `ls` → input of `wc -l`.

The single most important shell idea.

---

# `grep`

```sh
grep TODO main.py
grep -n TODO main.py          # with line numbers
grep -i error log.txt          # case-insensitive
grep -r "def foo" src/         # recursive
```

Extra-useful in pipes:

```sh
ls /usr/bin | grep -i python
```

---

# Redirection

```sh
echo hello >  out.txt   # write
echo world >> out.txt   # append
wc -l      <  out.txt   # read

cmd > out.log 2> err.log   # split streams
cmd > all.log 2>&1         # merge
```

---

# Wildcards

| Glob | Matches |
|------|---------|
| `*.py` | any `.py` file |
| `L??_*` | `L` + 2 chars + `_` + anything |
| `**/*.ipynb` | all `.ipynb`, any depth |

Expanded by the shell *before* the command runs.

---

# Environment variables

```sh
env                 # list all
echo "$HOME"

EDITOR=nano cmd     # just for one command
export EDITOR=code  # rest of session
```

Persist in `~/.zshrc` / `~/.bashrc`.

---

# Shell config

```sh
# ~/.zshrc
alias ll='ls -la'
alias gs='git status'
export EDITOR=code
export PATH="$HOME/.local/bin:$PATH"
```

`source ~/.zshrc` to reload.

---

# A real pipeline

```sh
cat file.txt | tr ' ' '\n' | sort | uniq -c | sort -rn | head
```

Top 10 words in a file. Small tools, chained.

---

# `ssh` preview

```sh
ssh netid@server.rice.edu
scp local.py netid@server:~/project/
rsync -av results/ netid@server:~/project/results/
```

Once you're in, it's just a shell — everything above still works.

---
layout: center
class: text-center
---

# Homework 3

Shell tasks on a provided sample tree.

See `assignments/homework_03.ipynb`.
