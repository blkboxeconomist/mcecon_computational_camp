# Computational Camp

A 12-week summer camp for students entering Rice's computational economics
master's program. The camp covers foundations and tooling so that the four
follow-on courses can start from a shared baseline:

- **Data for Computational Economics** (pandas)
- **Math for Computational Economics** (numpy and the scientific stack)
- **Dynamics for Computational Economics** (dynamic programming, RL)
- **Machine Learning for Computational Economics** (PyTorch, JAX)

The camp itself does **not** teach numpy, pandas, or deep-learning libraries
— those are covered in depth by the follow-on courses.

## Weekly schedule

| Week | Topic | Folder |
|------|-------|--------|
| 1 | Getting set up: `uv`, Python, editor, Jupyter | [`lectures/L01_setup`](lectures/L01_setup) |
| 2 | Markdown + Jupyter notebooks | [`lectures/L02_markdown_notebooks`](lectures/L02_markdown_notebooks) |
| 3 | Command line, shells, terminal | [`lectures/L03_cli`](lectures/L03_cli) |
| 4 | Git + version control | [`lectures/L04_git`](lectures/L04_git) |
| 5 | Python basics | [`lectures/L05_python_basics`](lectures/L05_python_basics) |
| 6 | Control flow | [`lectures/L06_control_flow`](lectures/L06_control_flow) |
| 7 | Collections | [`lectures/L07_collections`](lectures/L07_collections) |
| 8 | Functions | [`lectures/L08_functions`](lectures/L08_functions) |
| 9 | AI-assisted coding + debugging + tiny OOP | [`lectures/L09_ai_debug_oop`](lectures/L09_ai_debug_oop) |
| 10 | LaTeX | [`lectures/L10_latex`](lectures/L10_latex) |
| 11 | Software engineering for economists | [`lectures/L11_swe`](lectures/L11_swe) |
| 12 | Guided project | [`lectures/L12_project`](lectures/L12_project) |

Weekly homework lives under [`assignments/`](assignments) as
`homework_XX.ipynb` (week 12 is a project directory).

## Getting started

Week 1 walks students through installing everything, but for the impatient:

```sh
# 1. Install uv (macOS / Linux)
curl -LsSf https://astral.sh/uv/install.sh | sh

# 2. Clone this repo
git clone https://github.com/<you>/computational_camp.git
cd computational_camp

# 3. Sync the environment
uv sync

# 4. Launch Jupyter
uv run jupyter lab
```

## Repository layout

```
computational_camp/
├── lectures/LXX_topic/
│   ├── README.md          learning objectives + outline
│   ├── <topic>.ipynb      walkthrough notebook
│   └── slides/            slidev deck for in-class delivery
├── assignments/           homework_01.ipynb … homework_11.ipynb + homework_12/
├── pyproject.toml         uv-managed Python environment
└── CLAUDE.md              guidance for AI collaborators on this repo
```

## Running a slidev deck

Each lecture ships its own slidev project:

```sh
cd lectures/L03_cli/slides
npm install           # first time only
npx slidev slides.md
```
