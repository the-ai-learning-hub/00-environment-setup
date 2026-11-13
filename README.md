# Lesson 0 · Setup & first steps

**From zero to your first Python program.** Part of [The AI Learning Hub](https://github.com/the-ai-learning-hub).

📖 **[Open the Lesson 0 slides](https://the-ai-learning-hub.github.io/00-environment-setup/)**. Everything is explained there. Use ← → to move between slides.

This page has two parts: **install the tools**, then **the challenge**.

> In the slides, commands start with `>`; here they appear without it. Never copy the `>` or the prompt before it (e.g. `PS C:\Users\ana>`).

---

## Step 1 · Install the tools

Open a terminal (**never** "Run as administrator"): on Windows, Windows key → `PowerShell`; on macOS, Cmd + Space → `Terminal`; on Linux, Ctrl + Alt + T.

### uv (runs Python for you) · 📖 [slides 12–15](https://the-ai-learning-hub.github.io/00-environment-setup/#12)

**Windows:**

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

**macOS / Linux:**

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Close the terminal, open a new one and check: `uv --version`

### VS Code (where you write code) · 📖 [slides 17–23](https://the-ai-learning-hub.github.io/00-environment-setup/#17)

1. Download from [code.visualstudio.com](https://code.visualstudio.com). Windows: User Installer, tick **Add to PATH**.
2. Extensions (`Ctrl+Shift+X`) → install **Python** by **Microsoft**.

### Git and GitHub (save your work online) · 📖 [slides 41–43](https://the-ai-learning-hub.github.io/00-environment-setup/#41)

1. Create a free account at [github.com/signup](https://github.com/signup).
2. Install Git: Windows from [git-scm.com](https://git-scm.com) · macOS `xcode-select --install` · Linux `sudo apt install git`.
3. In a **new** terminal, tell Git who you are (use the email of your GitHub account):

```
git config --global user.name "Your Name"
git config --global user.email "the-email-of-your-github-account@example.com"
```

✅ **Ready when** these show two version numbers, and your name and email:

```
uv --version
git --version
git config --global --list
```

Something not working? See [slide 15](https://the-ai-learning-hub.github.io/00-environment-setup/#15).

---

## Step 2 · The challenge: three programs in your own private repository

📖 You'll use what's on [slides 25–36](https://the-ai-learning-hub.github.io/00-environment-setup/#25) (uv and Python) and [slides 44–51](https://the-ai-learning-hub.github.io/00-environment-setup/#44) (Git).

### 🎯 The goal

When you finish, your repository on GitHub must look exactly like this:

```
my-private-repo/
├── .gitignore
├── .python-version
├── README.md
├── pyproject.toml        ← lists rich and cowsay
├── uv.lock
├── 1_questions.py        ← asks two questions
├── 2_rich_welcome.py     ← a colourful panel with rich
└── 3_talking_cow.py      ← a cow that says hello
```

There's also a `.venv` folder on your computer, but it must **not** go to GitHub (the `.gitignore` takes care of that). At the end you'll also have a second copy, `my-private-repo-copy`, next to the original.

### The steps

1. **Create the repository.** On github.com: **+ → New repository**, name `my-private-repo`, **Visibility: Private**, **Add README** on, **.gitignore: Python**. Copy the HTTPS address.
2. **Clone it** into `Documents/python-projects` (create that folder first if you don't have it). Use `git clone <address>`.
3. **Open it in VS Code** (**File → Open Folder…** → `my-private-repo`) and open its terminal (**Terminal → New Terminal**). **Turn it into a uv project** with `uv init` (don't forget `--no-package`).
4. **Add the two libraries** `rich` and `cowsay` with `uv add`.
5. **Delete `main.py`** (right-click it in VS Code's file list → **Delete**) and create the three files from the map (**File → New File…**, type the name exactly), each with a `main()` function:

| File | What it does | Look back at |
|---|---|---|
| `1_questions.py` | Asks your name and favourite food, then prints `Ana loves pizza!` | [slide 32](https://the-ai-learning-hub.github.io/00-environment-setup/#32) |
| `2_rich_welcome.py` | Asks your name and shows a colourful welcome inside a `rich` Panel | [slides 33–34](https://the-ai-learning-hub.github.io/00-environment-setup/#33) |
| `3_talking_cow.py` | Asks your name and makes a cow say hello with `cowsay` | [slide 35](https://the-ai-learning-hub.github.io/00-environment-setup/#35) |

6. **Run each one** with `uv run <file.py>` until all three work.
7. **Save and send it to GitHub** with the commit message `Add my three first programs` (`git status` → `git add .` → `git commit -m "…"` → `git push`).
8. **Pretend you have a second computer.** First go **back** to `python-projects` (`cd ..`): never clone inside `my-private-repo`. Then clone the repository again into a folder called `my-private-repo-copy`, by putting that name at the end:

   ```
   git clone https://github.com/YOUR-USERNAME/my-private-repo.git my-private-repo-copy
   ```

   Go inside it (`cd my-private-repo-copy`). It has no `.venv` (that never goes to GitHub), so rebuild it from the shopping list (`pyproject.toml` + `uv.lock`) with `uv sync`. Then run `3_talking_cow.py`.
9. **Change something on the "second computer".** Open **`my-private-repo-copy`** in VS Code (**File → Open Folder…**). Check the folder name at the top of the file list: it must say `MY-PRIVATE-REPO-COPY`. Change what the cow says in `3_talking_cow.py`, then save and send it with the commit message `Change the cow message`.
10. **Back on your "first computer".** Open the original **`my-private-repo`** in VS Code again. Its cow still says the old message: bring the change with `git pull`, run `3_talking_cow.py` again and look at your save points with `git log --oneline` (press `q` if needed).

✅ **Done when:**

- On github.com your repository matches the map above (and has no `.venv`).
- `git log --oneline` shows your two commits: `Add my three first programs` and `Change the cow message`.
- In the **original** folder, the cow says the new message.
- Opening the address in a private/incognito window shows **404**: only you can see it.

A private repository always needs you signed in: if the **"Connect to GitHub"** window appears, choose **Sign in with your browser**.

<details>
<summary><b>Stuck on the commands?</b> (try it first!)</summary>

```
cd ~/Documents/python-projects
git clone https://github.com/YOUR-USERNAME/my-private-repo.git
cd my-private-repo
uv init --no-package
uv add rich cowsay
```

After creating the three files and deleting `main.py`:

```
uv run 1_questions.py
uv run 2_rich_welcome.py
uv run 3_talking_cow.py
git status
git add .
git commit -m "Add my three first programs"
git push
```

The "second computer":

```
cd ~/Documents/python-projects
git clone https://github.com/YOUR-USERNAME/my-private-repo.git my-private-repo-copy
cd my-private-repo-copy
uv sync
uv run 3_talking_cow.py
```

After changing the cow's message in `my-private-repo-copy`:

```
git add .
git commit -m "Change the cow message"
git push
```

Back on the "first computer":

```
cd ~/Documents/python-projects/my-private-repo
git pull
uv run 3_talking_cow.py
git log --oneline
```

</details>

<details>
<summary><b>Stuck on the code?</b> One possible solution for each file</summary>

`1_questions.py`

```python
def main():
    name = input("What's your name? ")
    food = input("Favourite food? ")
    print(f"{name} loves {food}!")


if __name__ == "__main__":
    main()
```

`2_rich_welcome.py`

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

`3_talking_cow.py`

```python
import cowsay


def main():
    name = input("What's your name? ")
    cowsay.cow(f"Hello, {name}!")


if __name__ == "__main__":
    main()
```

</details>
