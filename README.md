# IST356 Assignment 01 — Course Workflow Walkthrough

Welcome to your first assignment! This one is **more about *how* to complete an
assignment in this course than it is about Python programming.** Follow it
top-to-bottom: first you'll open the assignment in the course environment
(**Prep**), then you'll walk through the ten things you'll do in *every* assignment
(**Walkthrough**), and finally you'll complete a small graded task and a
reflection (**The Assignment**).

Take your time and don't skip steps — the whole point is to build the muscle
memory for the workflow.

## Meta

### Learning Objectives

By the end of this assignment you will be able to:

1. **Write and edit code** in the VS Code editor
2. **Debug** a program using the VS Code debugger (breakpoints, stepping, variables)
3. **Run automated tests** with pytest using the Testing panel
4. **Run a terminal app** (a plain Python program) and interact with it
5. **Run a notebook app** (a Jupyter `.ipynb` notebook)
6. **Run a Streamlit app** (a web app) in your browser
7. **Commit** your code changes in VS Code
8. **Push** your commits to GitHub
9. **See your code on GitHub** in the browser
10. **Submit your work for grading** using GraderThan

### Assignment Layout

Every assignment in this course shares the same layout:

- `code/` — **where you write code.** Only files in this folder are reviewed for grading.
  - `bill.py` — the **module**: the functions you write (checked by the unit tests)
  - `console.py` — the **console** interface that uses `bill.py`
  - `explore.ipynb` — the **notebook** interface that uses `bill.py`
  - `dashboard.py` — the **Streamlit** interface that uses `bill.py`
  - `reflection.txt` — **where you write your reflection** (graded)
- `tests/` — the automated tests that check your code
  - `test_unit.py` — **Unit Tests** for the functions in `bill.py`
  - `test_integration.py` — **Integration Tests** for the three interfaces
- `grader/` — the autograder used by GraderThan (you don't touch this)
- `.devcontainer/` — configures the pre-built course container (`mafudge/ist356:latest`)
- `.vscode/` — run / debug / test configurations for VS Code
- `.streamlit/` — configuration for the Streamlit app
- `README.md` — these instructions
- `reflection.md` — how to write a good reflection
- `rubric.json` / `requirements.txt` — grading rubric and Python dependencies

### Prerequisites

Before you start, complete the **one-time course setup**:
👉 https://mafudge.github.io/ist356/0-intro/0-0-setup.html

That setup gets your GitHub account ready (and, if you want to work locally, VS Code
and Docker). This assignment runs inside the pre-built course dev container
(`mafudge/ist356:latest`), which already has Python, pytest, Jupyter, and Streamlit
installed — **there is nothing to install manually.**

> **No computer setup? Use GitHub Codespaces** (Prep → Option A) to run everything in
> your browser — you only need a GitHub account.

---

## Prep — Open the assignment

You'll do this at the start of **every** assignment. First fork, then pick **one**
of two ways to open your fork in the course environment.

1. **Fork this repository.** At the top-right of this repo's GitHub page, click
   **Fork**. This makes your own personal copy under your GitHub account. You
   submit and are graded on *your fork*.

Now choose **Option A** (in the browser — nothing to install) **or** **Option B**
(on your own computer). Everything in the Walkthrough works the same either way.

### Option A — GitHub Codespaces (in the browser) ⭐ easiest

A Codespace runs the exact same course container **in the cloud** and opens VS Code
in your browser — there's nothing to install, so this works on a Chromebook, a lab
machine, or a locked-down laptop.

1. Go to **your fork's** page on GitHub. Click the green **Code** button, then the
   **Codespaces** tab.
2. Click **Create codespace on main**. The container builds (the first time takes a
   few minutes).
3. VS Code opens in your browser, already **inside the course container**, with your
   fork's code loaded and Git signed in. You can skip cloning — you're ready.

> Reopen an existing Codespace anytime from **https://github.com/codespaces** (or the
> **Code → Codespaces** tab on your fork). Codespaces have monthly free hours, so
> **stop** yours when you're done: `github.com/codespaces` → **⋯ → Stop codespace**.

### Option B — Your own computer (local dev container)

Requires Docker Desktop and VS Code from the [course setup](https://mafudge.github.io/ist356/0-intro/0-0-setup.html).

1. **Clone your fork.** On your fork's page, click the green **Code** button and copy
   the HTTPS URL, then clone it. Easiest way: in VS Code press `Ctrl+Shift+P` →
   **Git: Clone**, paste the URL, and pick a folder. Or from a terminal:

   ```sh
   git clone https://github.com/YOUR-GITHUB-USERNAME/assignment_01.git
   ```

   > Make sure the URL has **your** username in it, not `ist356`. You cloned the
   > wrong repo if it doesn't.

2. **Open the folder and reopen in the container.** Choose **File → Open Folder** and
   select the cloned `assignment_01` folder. VS Code detects the dev container and
   pops up a notification — click **Reopen in Container**. (If you miss it:
   `Ctrl+Shift+P` → **Dev Containers: Reopen in Container**.) The first build takes a
   few minutes; after that you're working *inside* the course environment.

You're ready. Everything below happens inside VS Code in the course container —
whether that's in your browser (Codespaces) or on your desktop.

---

## Walkthrough — How to do things

These are the ten core tasks. Do each one now so you know how it works.

> **Using GitHub Codespaces (Prep → Option A)?** Every step below works exactly the
> same — it's the same VS Code and the same course container, just in your browser.
> Only two steps differ, and each is flagged inline with a 🌐 **In Codespaces** note:
> **running a web app** (step 6 — use the **PORTS** panel instead of `localhost`) and
> **pushing to GitHub** (step 8 — you're already signed in). Menus, panels, and
> keyboard shortcuts are identical.

### 1. Write / edit code

In the **Explorer** (top icon in the Activity Bar on the left, or **View → Explorer**),
open `code/bill.py`. Read the docstrings in the file. Click into the editor, make a
change, and **save** with `Ctrl+S`. That's it — you write and edit all of your code
right here.

### 2. Use the VS Code debugger

The debugger lets you pause a running program and inspect it line-by-line — great
for understanding what your code is actually doing. Here's the mechanic:

1. Open `code/console.py`.
2. **Set a breakpoint:** click just to the **left of a line number** — a red dot
   appears. The program will pause *before* running that line.
3. Start debugging: **Run → Start Debugging** (or press `F5`). Choose
   **Python Debugger: Current File** if prompted.
4. When the program asks for input, type a value in the **TERMINAL** panel and
   press Enter. Execution pauses at your breakpoint.
5. Look at the **VARIABLES** panel (left side) to see the current value of each
   variable.
6. **Step** one line at a time with `F10` (**Run → Step Over**). Watch how the
   variables change.
7. When you're done, **Run → Stop Debugging** (`Shift+F5`).

> You can't edit code while the program is paused — stop debugging first, then edit.

### 3. Run automated tests

Tests tell you whether your code does what it's supposed to.

1. Open the **Testing** panel: **View → Testing** (the beaker/flask icon in the
   Activity Bar).
2. Expand the tree until you can see the individual tests inside
   `tests/test_unit.py` (the **Unit Tests**) and `tests/test_integration.py` (the
   **Integration Tests**).
3. Click the **▶ (play)** button next to a test to run it.
4. A green **✓** means it passed; a red **✗** means it failed. Click a failed test
   to read the **error message** — that's how you learn *what* went wrong.

Run the tests now. They pass once you've finished *The Assignment* — the unit tests
check your `bill.py` functions, and the integration tests check that the console,
notebook, and Streamlit interfaces work.

### 4. Run a terminal app

A "terminal app" is a plain Python program that reads input and prints output in
the terminal.

1. Open `code/console.py`.
2. **Run → Run Without Debugging** (`Ctrl+F5`). Choose **Python Debugger: Current File**
   if asked.
3. The program runs in the **TERMINAL** panel at the bottom. Answer each prompt —
   e.g. `Bill subtotal:` `50`, `Tip percent:` `20`, `Number of people:` `4` — and
   press Enter to see the split.

### 5. Run a notebook app

A Jupyter notebook mixes text and runnable code in "cells."

1. Open `code/explore.ipynb`. It opens in the notebook editor.
2. The first time, click **Select Kernel** (top-right of the notebook) and choose
   the Python interpreter at `/usr/local/bin/python`.
3. Run a single cell with **Shift+Enter**, or click **Run All** at the top to run
   every cell in order.
4. Each code cell's output appears directly beneath it. Follow along with the
   notes inside the notebook.

### 6. Run a Streamlit app

Streamlit turns a Python file into an interactive web app.

1. Open `code/dashboard.py`.
2. Open **Run and Debug** (**View → Run**, the play-with-a-bug icon).
3. From the dropdown at the top, choose **Streamlit Run: Current File**, then press
   the green **▶** button.
4. Open the app in your browser:
   - **On your computer (Option B):** go to **http://localhost:28502** — VS Code
     usually also pops up an **Open in Browser** button on a port notification.
   - 🌐 **In Codespaces (Option A):** `localhost` won't work. Open the **PORTS** tab
     (next to TERMINAL), find port **28502**, and click the 🌐 globe icon (or the
     **Open in Browser** popup) to open the forwarded URL.

   Interact with the tip slider and the number inputs to re-split the bill.
5. Stop it with **Run → Stop Debugging** (`Shift+F5`) when you're done.

### 7. Commit code changes in VS Code

A *commit* is a saved snapshot of your work in git.

1. Open **Source Control**: **View → Source Control** (the branch icon in the
   Activity Bar). You'll see your changed files listed.
2. Hover a file and click **+** to **stage** it (or click **+** on "Changes" to
   stage everything).
3. Type a short **commit message** describing what you did (e.g.
   `Implement bill.py functions`).
4. Click the **✓ Commit** button.

### 8. Push your code

Committing saves the snapshot *locally*. **Pushing** sends it to your fork on
GitHub.

- In the **Source Control** panel, click **Sync Changes** (or the **⋯** menu →
  **Push**). If asked to sign in to GitHub, follow the prompts.

  > 🌐 **In Codespaces:** you're already signed in to GitHub, so **Sync Changes**
  > pushes straight to your fork — no sign-in prompt.

### 9. See your code on GitHub

- In your browser, go to your fork: `https://github.com/YOUR-GITHUB-USERNAME/assignment_01`
  and **refresh**. You should see your latest commit message and your changed
  files. If it's there, your work is safely on GitHub. **This is the copy
  GraderThan reads.**

### 10. Submit code for grading using GraderThan

GraderThan runs the autograder against your fork and gives you feedback and a score.

1. Go to **https://graderthan.cent-su.org** and log in with your SU Microsoft account.
2. Click this assignment on your dashboard.
3. Paste your **fork's GitHub URL**
   (e.g. `https://github.com/YOUR-GITHUB-USERNAME/assignment_01`).
4. (Optional) check **"Email me when feedback is ready."**
5. Click **Submit for Grading and Feedback.**

> Always **commit and push (steps 7–8) before you submit** — GraderThan only sees
> what's on GitHub.

---

## The Assignment — what to actually do

You're building a **Bill Splitter**. The pattern is the one you'll use all
semester: write the logic once as functions in a **module**, then reuse it from
several **interfaces**.

### 1. Write the module — `code/bill.py`

`bill.py` holds four small functions. Each has a docstring describing exactly what
it should return:

| function | what it returns |
| --- | --- |
| `tip_amount(subtotal, pct)` | the tip — `pct` percent of `subtotal`, rounded to cents |
| `grand_total(subtotal, pct)` | the subtotal plus the tip |
| `split_evenly(total, people)` | each person's share (and it raises `ValueError` if `people <= 0`) |
| `is_generous(pct)` | `True` when the tip is 20% or more |

Implement them so the **Unit Tests** (`tests/test_unit.py`, Walkthrough #3) all
pass. These functions do **no** `input()` or `print()` — they just take values in
and return a value out.

### 2. Check the interfaces work

Three interfaces already `import bill` and use your functions — the **Integration
Tests** (`tests/test_integration.py`) confirm each one works once `bill.py` is
correct:

- **`console.py`** — run it (Walkthrough #4) and split a bill in the terminal.
- **`explore.ipynb`** — run it (Walkthrough #5) to see the tips compared in a table.
- **`dashboard.py`** — run it (Walkthrough #6) and split a bill with sliders.

### 3. Reflection

Read `reflection.md`, then write your reflection in **`code/reflection.txt`**. A
good reflection is **specific**, **uses the terminology** from class, and is
**actionable**. This is graded — see `reflection.md` for what "good" looks like.

---

## How You're Graded

GraderThan scores this assignment out of **10 points** (see `rubric.json`):

| What | Points | Judged by |
| --- | --- | --- |
| **Unit Tests** — `test_unit.py` (the `bill.py` functions) | 3 | automated tests |
| **Integration Tests** — `test_integration.py` (the interfaces) | 3 | automated tests |
| Code style & readability | 2 | AI reviewer |
| Reflection quality | 2 | AI reviewer |

**Only files in the `code/` folder are graded.** Commit, push, and submit
(Walkthrough #7–10) to get your score and feedback.
