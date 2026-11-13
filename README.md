# Lesson 0 · Setup & first steps

**From zero to your first Python program.** Install the tools, write real code, save it to the cloud. No experience needed.

Part of [The AI Learning Hub](https://github.com/the-ai-learning-hub).

## 📖 The slides

**[Open the Lesson 0 slides](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html)**. All the explanations are there. Use ← → to move between slides.

This page is your **workbook**: the commands to copy, the challenges and the fixes for when something goes wrong. Each section links to its slides.

> In the slides, commands start with `>`; here they appear without it. Never copy the `>` or the prompt before it (e.g. `PS C:\Users\ana>`).

## By the end of today

- [ ] **Python running**: installed with uv, in your own user account
- [ ] **VS Code ready**: with the official Python extension
- [ ] **A real project**: written and run by you, from an empty folder
- [ ] **A library**: colourful output using someone else's code
- [ ] **On GitHub**: saved with Git, online on your own account

## Contents

1. [The terminal and uv](#1-the-terminal-and-uv)
2. [VS Code](#2-vs-code)
3. [Your first Python project](#3-your-first-python-project) · Challenges 1 and 2, bonus
4. [Git & GitHub](#4-git--github) · Final Git challenge
5. [Homework: check your setup](#homework-check-your-setup)
6. [If something goes wrong](#if-something-goes-wrong)
7. [Cheat sheets](#cheat-sheets)
8. [When you're stuck](#when-youre-stuck)

---

## 1. The terminal and uv

📖 What Python is: [slides 4–7](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#4) · The terminal: [slides 9–11](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#9) · uv: [slides 12–15](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#12)

Open a terminal (**never** "Run as administrator"): on Windows, Windows key → `PowerShell`; on macOS, Cmd + Space → `Terminal`; on Linux, Ctrl + Alt + T. Your first command:

```
whoami
```

### Install uv

**Windows** (PowerShell):

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Blocked? Try instead:

```powershell
winget install --id=astral-sh.uv -e
```

**macOS / Linux** (Terminal):

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

No curl? Or using Homebrew?

```bash
wget -qO- https://astral.sh/uv/install.sh | sh
brew install uv
```

✅ `everything's installed!` **Then close the terminal (and VS Code) and open a new one.**

### Check it worked

```
uv --version
```

✅ Any version number. Optionally, get Python now (uv also does it by itself the first time a project needs it):

```
uv python install
```

---

## 2. VS Code

📖 [Slides 17–23](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#17)

1. Download from [code.visualstudio.com](https://code.visualstudio.com). Windows: User Installer, tick **Add to PATH**. macOS: drag it into Applications.
2. Extensions (`Ctrl+Shift+X`) → search **Python** → install the one by **Microsoft**.
3. Turn on **File → Auto Save**.

No installs allowed? Follow the class in [Google Colab](https://colab.research.google.com).

---

## 3. Your first Python project

📖 [Slides 25–36](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#25)

In **Documents**, create a folder `python-projects`, open it in VS Code (**File → Open Folder…**) and open the terminal (**Terminal → New Terminal**). Then:

```
uv init hello-world --no-package
```

Open the `hello-world` folder in VS Code (**File → Open Folder…**) and run it:

```
uv run main.py
```

✅ `Hello from hello-world!`

Then press `Ctrl+Shift+P` → **Python: Select Interpreter** → pick the one with `.venv`.

### Challenge 1 · Make your program talk to you

📖 [Slide 32](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#32). Replace everything in `main.py` with:

```python
def main():
    name = input("What's your name? ")
    print(f"Welcome to Python, {name}!")


if __name__ == "__main__":
    main()
```

### Challenge 2 · A colourful welcome with rich

📖 [Slides 33–34](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#33)

```
uv add rich
```

```python
from rich import print
from rich.panel import Panel


def main():
    name = input("What's your name? ")
    message = f"[bold magenta]Welcome, {name}![/] :snake:"
    print(Panel(message, title="Hello World"))


if __name__ == "__main__":
    main()
```

Try `green`, `italic`, `:rocket:` or `:tada:`.

### Bonus challenges

📖 [Slide 35](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#35)

<details>
<summary><b>Bonus A · Ask two questions</b></summary>

```python
def main():
    name = input("What's your name? ")
    food = input("Favourite food? ")
    print(f"{name} loves {food}!")
```

</details>

<details>
<summary><b>Bonus B · A talking cow</b></summary>

```
uv add cowsay
```

```python
import cowsay


def main():
    name = input("What's your name? ")
    cowsay.cow(f"Hello, {name}!")
```

</details>

---

## 4. Git & GitHub

📖 What Git and GitHub are: [slides 38–40](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#38) · Setup: [slides 41–43](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#41)

### Setup (once per computer)

1. Create a free account at [github.com/signup](https://github.com/signup).
2. Install Git.

**Windows:** download **Git for Windows/x64 Setup** from [git-scm.com](https://git-scm.com), or in PowerShell:

```powershell
winget install --id Git.Git -e
```

**macOS:**

```bash
xcode-select --install
```

**Linux:**

```bash
sudo apt install git      # Ubuntu / Debian
sudo dnf install git      # Fedora
```

3. In a **new** terminal, check it and tell Git who you are (use the email of your GitHub account):

```
git --version
git config --global user.name "Your Name"
git config --global user.email "the-email-of-your-github-account@example.com"
git config --global --list
```

### Your first repository

📖 [Slides 44–50](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#44)

1. On github.com: **+ → New repository** → name `my-first-repo`, **Public**, **Add README** on, **.gitignore: Python**, **License: MIT**. Then **Code ▾** → copy the HTTPS address.
2. Bring it to your computer:

```
cd ~/Documents/python-projects
git clone https://github.com/YOUR-USERNAME/my-first-repo.git
```

3. Open `my-first-repo` in VS Code, then in its terminal:

```
uv init --no-package
uv add rich cowsay
```

4. Replace `main.py` with:

```python
import cowsay
from rich import print
from rich.panel import Panel


def main():
    name = input("What's your name? ")
    message = f"[bold magenta]Welcome, {name}![/]"
    print(Panel(message, title="my-first-repo"))
    cowsay.cow(f"{name} just pushed to GitHub!")


if __name__ == "__main__":
    main()
```

Add a line to `README.md`, e.g. `Made by Ana in Lesson 0 🐍`.

5. Save it and send it to GitHub:

```
git status
git add .
git commit -m "My first Python project"
git push
```

A **"Connect to GitHub"** window? Choose **Sign in with your browser**, then **Authorize**.

6. The other direction: edit `README.md` on github.com (pencil → **Commit changes**), then:

```
git pull
```

**Every day from now on:** edit → `git add .` → `git commit -m "…"` → `git push`.

### 🏆 Final Git challenge · Get the class materials yourself

📖 [Slide 53](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#53)

1. Go to your **Documents** folder.
2. Clone this repository: `github.com/the-ai-learning-hub/00-environment-setup`
3. Go inside it and list the files.
4. Before every class, get the new materials.

<details>
<summary><b>Solution</b> (try it first!)</summary>

```
cd ~/Documents
git clone https://github.com/the-ai-learning-hub/00-environment-setup.git
cd 00-environment-setup
ls
```

Before every class:

```
git pull
```

</details>

⚠️ **Don't edit files in this folder.** Copy what you want to play with into `python-projects`, so `git pull` always works.

---

## Homework: check your setup

📖 [Slide 56](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#56)

**About 30 minutes, before the next class.** One project, alone, that tests your whole setup: every uv and Git command from today. If each step shows what it should, you're ready for Lesson 1.

| # | Part | You use |
|---|---|---|
| 1 | Do it again, alone | `git clone` · `uv init` · `uv run` |
| 2 | Make it yours | `uv add` · `uv remove` |
| 3 | Save it forever | `git status` · `git add` · `git commit` · `git push` · `git diff` · `uv sync` |
| 4 | Stay up to date | `git pull` · `git log` |

📣 Share your **`my-first-repo`** link in the class chat (it's public, so we can open it): that's how we'll know you're ready for Lesson 1. The private one stays yours.

### 0 · Check your tools

```
uv --version
git --version
git config --global --list
```

✅ Two version numbers, and your name and email.

### 1 · Do it again, alone: a private repository

1. On github.com: **+ → New repository**, name `my-private-repo`, **Visibility: Private**, **Add README** on, **.gitignore: Python**. Copy the HTTPS address.
2. Bring it to your computer:

```
cd ~/Documents/python-projects
git clone https://github.com/YOUR-USERNAME/my-private-repo.git
```

3. Open `my-private-repo` in VS Code, then in its terminal:

```
uv init --no-package
uv run main.py
```

✅ `Hello from my-private-repo!`

A private repository always needs you signed in: if the **"Connect to GitHub"** window appears, choose **Sign in with your browser**.

### 2 · Make it yours: libraries in and out

```
uv add rich
uv add cowsay
```

✅ Open `pyproject.toml`: both appear under `dependencies`.

```
uv remove cowsay
```

✅ `pyproject.toml` lists only `rich`.

Write `main.py` yourself: ask **three questions** and print a little story with the answers, in a `rich` Panel. Look back at Challenge 2 and Bonus A. Run it with `uv run main.py` until it works.

### 3 · Save it forever: push, change, sync

```
git status
git add .
git commit -m "My story program"
git push
```

✅ Your files are on github.com. Open the address in a private/incognito window: GitHub shows **404**, because only you can see it.

Change something in `main.py`, then look at the change before saving:

```
git diff
```

✅ The old line in red, the new one in green (press `q` to exit). Then:

```
git add .
git commit -m "Change my story"
git push
```

Pretend you're on a new computer: clone it a second time and rebuild it from the shopping list.

```
cd ~/Documents/python-projects
git clone https://github.com/YOUR-USERNAME/my-private-repo.git my-private-repo-copy
cd my-private-repo-copy
uv sync
uv run main.py
```

✅ The copy has no `.venv` until `uv sync` creates it, and your story runs exactly like the original. That's why we push `pyproject.toml` and `uv.lock`, never `.venv`.

### 4 · Stay up to date: pull

1. On github.com, in `my-private-repo`, edit `README.md` (pencil → write one line → **Commit changes**).
2. Back in the original folder:

```
cd ~/Documents/python-projects/my-private-repo
git pull
git log --oneline
```

✅ The new line is in `README.md`, and `git log` shows all your save points (press `q` if needed).

3. Finally, get the new class materials:

```
cd ~/Documents/00-environment-setup
git pull
```

<details>
<summary><b>Stuck on the story program?</b> One possible solution</summary>

```python
from rich import print
from rich.panel import Panel


def main():
    name = input("What's your name? ")
    place = input("Where would you like to travel? ")
    food = input("Favourite food? ")
    story = f"[bold green]{name}[/] flew to [bold]{place}[/] and ate {food} every day. :airplane:"
    print(Panel(story, title="My story"))


if __name__ == "__main__":
    main()
```

</details>

---

## If something goes wrong

📖 [Slide 15](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#15)

### uv and Python

| You see… | Do this |
|---|---|
| `uv` is not recognized / command not found | Close all terminals and VS Code, then open them again. Last resort: restart the computer. |
| Running scripts is disabled | Copy the whole command, including `-ExecutionPolicy ByPass`. Or use `winget install --id=astral-sh.uv -e` |
| SSL or certificate error | You're on a company network. Set `UV_SYSTEM_CERTS=1` and retry (older uv: `UV_NATIVE_TLS`). |
| Access denied | You opened the terminal as administrator. Open a normal one. |
| Blocked by your company | Follow the class in [Google Colab](https://colab.research.google.com) and ask IT later. |
| No `main.py`, but a `src/` folder | You forgot `--no-package`. Delete the files uv created and run `uv init --no-package` again. |
| `UnicodeEncodeError` when printing an emoji (Windows) | Run `$env:PYTHONUTF8=1` in PowerShell (cmd: `set PYTHONUTF8=1`), then run your program again. Or remove the emoji. |
| `cd ~/Documents/...` says the folder doesn't exist (Windows) | Your Documents folder is probably inside OneDrive. Look at the path in VS Code's terminal prompt, e.g. `cd ~/OneDrive/Documents/python-projects`. |

### Git

| You see… | Do this |
|---|---|
| `not a git repository` | You're in the wrong folder. `cd` into your project and try again. |
| `rejected` … `fetch first` on `git push` | GitHub has changes you don't have (maybe you edited on github.com). Run `git pull`, then `git push` again. |
| `Authentication failed` or `Permission denied` | Run `git push` again and sign in through the **"Connect to GitHub"** window, with the browser. Check that the address has *your* username. |
| `Please tell me who you are` | Run the two `git config --global` lines from the Git setup. |
| `nothing to commit, working tree clean` | Not an error: everything is already saved. Change a file first. |

---

## Cheat sheets

📖 [Slide 36 (uv)](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#36) · [Slide 51 (Git)](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#51) · [Slide 11 (terminal)](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#11)

| uv | What it does |
|---|---|
| `uv init <project-name> --no-package` | Create a new project folder (with `main.py`) |
| `uv run <file.py>` | Run a file (sets everything up first) |
| `uv add <library>` | Add a library to the project |
| `uv remove <library>` | Remove a library from the project |
| `uv sync` | Install everything on the list (e.g. after downloading a project) |
| `uv python install` | Install the latest Python |
| `uv --help` | List every command |

| Git | What it does |
|---|---|
| `git status` | What changed since the last save point |
| `git add .` | Choose everything for the next save point |
| `git commit -m "<message>"` | Save a snapshot with a caption |
| `git push` | Send your save points to GitHub |
| `git pull` | Bring new save points from GitHub |
| `git clone <address>` | Download a repository to your computer |
| `git log --oneline` | The list of save points (press `q` to exit) |
| `git diff` | The exact lines you changed (press `q` to exit) |

Text in `< >` is a placeholder: replace it, without the brackets.

---

## When you're stuck

📖 [Slide 55](https://the-ai-learning-hub.github.io/00-environment-setup/lesson-0-python-setup.html#55)

- uv documentation: [docs.astral.sh/uv](https://docs.astral.sh/uv/)
- Python in VS Code: [code.visualstudio.com/docs/python](https://code.visualstudio.com/docs/python/python-tutorial)
- GitHub's getting-started guides: [docs.github.com/get-started](https://docs.github.com/en/get-started)

**How to ask for help well:** read the last lines of the error first, copy the error as text (not a phone photo), say what you typed and what you expected, then paste it into an AI assistant or the class chat.
