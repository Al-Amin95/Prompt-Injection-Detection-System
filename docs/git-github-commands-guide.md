# Git & GitHub Command Guide

A personal reference of every Git/GitHub command used while building this project,
from setup to now. For each command: **what it is**, **what it does**, and
**where & when to use it**.

> Terminal note: on **Windows Command Prompt** you switch folders with `cd /d <path>`.
> On **PowerShell** (prompt starts with `PS`) you use `cd "<path>"` (no `/d`).
> Git commands only work *inside* your project folder (the one containing the hidden `.git`).

---

## 0. Terminal / folder commands (not Git, but used alongside it)

**`cd /d D:\Prompt-Injection-Detection-System`** (Command Prompt)
- Moves into your project folder, switching drive and folder in one step.
- Use at the start of any Command Prompt session before running Git.

**`cd "D:\Prompt-Injection-Detection-System"`** (PowerShell)
- Same as above but for PowerShell. Quotes handle spaces; no `/d`.
- Use at the start of any PowerShell session.

**`mkdir data\raw data\processed notebooks models src webapp results screenshots docs`**
- Creates several folders at once.
- Use when first building your project's folder structure.

**`tree`** / **`dir`**
- `tree` shows folders as a diagram; `dir` lists the current folder's contents.
- Use to confirm folders/files were created correctly.

**`echo some text > file.txt`**
- Creates a small text file containing that text.
- Use for quick test files (we used it during branch practice).

**`del file.txt`**
- Deletes a file.
- Use to remove unwanted/leftover files.

---

## 1. One-time Git setup (per computer)

**`git --version`**
- Prints the installed Git version.
- Use to check whether Git is installed. An error means you must install Git for Windows first.

**`git config --global user.name "Al-Amin95"`**
- Sets the name stamped on every commit you make.
- Run once after installing Git. `--global` = applies to all your projects.

**`git config --global user.email "alamin28.sylhet@gmail.com"`**
- Sets the email stamped on commits; links commits to your GitHub account.
- Run once after installing Git, using your GitHub email.

**`git config --global user.name`** (no value)
- Reads back the saved name (same for `user.email`).
- Use to confirm your identity settings are correct.

---

## 2. Starting a repository

**`git init`**
- Creates a hidden `.git` folder, turning the current folder into a Git repository (local only).
- Run **once**, inside your project folder, at the very start of the project.

**`git status`**
- Shows the current branch and which files are new (untracked), changed, or staged.
- Use constantly — before and after almost every action — to see what Git sees.

---

## 3. The everyday save cycle (stage → commit)

**`git add .`**
- Stages **all** changed/new files (the `.` means "everything here") for the next commit.
- Use when you want to include all your recent changes in the next snapshot.

**`git add README.md`**
- Stages **one specific** file.
- Use when you only want to commit selected files.

**`git commit -m "message"`**
- Saves a permanent snapshot of the staged files, with a descriptive message.
- Use after `git add`, whenever you reach a meaningful checkpoint. Write clear messages.

---

## 4. Connecting to GitHub & uploading

**`git branch -M main`**
- Renames the current branch to `main` (`-M` = force rename).
- Run once early, so your main line matches GitHub's default name.

**`git remote add origin https://github.com/Al-Amin95/Prompt-Injection-Detection-System.git`**
- Links your local repo to the GitHub repo, nicknamed `origin`.
- Run once, after creating the empty repo on GitHub.

**`git remote set-url origin <url>`**
- Changes the GitHub URL if `origin` was already set (or set wrongly).
- Use only if `git remote add` says "remote origin already exists".

**`git remote -v`**
- Lists the linked remotes (fetch + push URLs).
- Use to confirm your repo is correctly connected to GitHub.

**`git push -u origin main`**
- Uploads `main` to GitHub and remembers the link (`-u` = set upstream).
- Use the **first** time you push the `main` branch.

**`git push -u origin dataset-preparation`**
- Uploads a specific branch to GitHub for the first time and sets its upstream.
- Use the first time you push any new branch.

**`git push -u origin --all`**
- Uploads **all** local branches to GitHub at once.
- Use when you want every branch visible on GitHub in one go.

**`git push`**
- Uploads new commits on the current branch to GitHub.
- Use after committing, once the branch already has an upstream set.

---

## 5. Branches — create, switch, list

> Rule learned: a branch name **cannot** be both a branch and a folder.
> So you cannot have `dataset-preparation` AND `dataset-preparation/raw`.
> Use a **hyphen** for sub-branches (e.g. `data-raw`), not a slash.

**`git checkout -b dataset-preparation`**
- Creates a new branch **and** switches to it (`-b` = create new branch).
- Use when starting a new piece of work (a new phase or sub-task).

**`git checkout main`**
- Switches to an existing branch.
- Use to move between branches you've already created.

**`git branch`**
- Lists your **local** branches; `*` marks the one you're on.
- Use to see your branches and confirm which one is active.

**`git branch -a`**
- Lists **all** branches — local and remote (GitHub) ones.
- Use to see what exists both locally and on GitHub.

**`git branch -r`**
- Lists only the remote (GitHub) branches.
- Use to check which branches have been pushed to GitHub.

**`git branch -v`**
- Lists local branches with the last commit on each.
- Use to see where each branch currently points.

---

## 6. Merging (combine one branch into another)

> Your flow is always: **sub-branch → phase branch → main.**

**`git merge data-raw`**
- Brings the commits from `data-raw` into the branch you are **currently on**.
- First switch to the target branch (`git checkout dataset-preparation`), then run this.
- "Fast-forward" in the output means the target had no new commits of its own, so Git
  simply moved its pointer forward — the simplest kind of merge.

Typical full sequence (merge a sub-branch up to main):
```
git checkout dataset-preparation   # go to the phase branch
git merge data-raw                 # bring sub-branch work into it
git checkout main                  # go to main
git merge dataset-preparation      # bring the phase work into main
git push                           # upload main to GitHub
```

---

## 7. Deleting branches

**`git branch -d practice`**
- Deletes a branch (lowercase `-d` = safe delete; only works if it's already merged).
- Use to clean up a branch whose work is safely merged.

**`git branch -D practice`**
- Force-deletes a branch (capital `-D`), even if not merged.
- Use to throw away a branch you don't want (e.g. practice/experiments). Be sure first.

---

## 8. Undo / reset / cleanup

**`git reset --hard origin/main`**
- Discards local commits/changes and snaps the current branch back to match GitHub's `main`.
- Powerful — it **throws away** work. Use only when you intend to discard local changes
  (we used it to remove a throwaway practice commit).

---

## 9. Inspecting history

**`git log --oneline`**
- Shows commit history, one line per commit (short ID + message).
- Use to review your project's history and see where branches point.

**`git log --oneline --all`**
- Same, but shows commits across **all** branches.
- Use to see the full picture, including work on other branches.

---

## Quick mental model

- **Folders** (`data/`, `src/`, …) organize files by *type* — all exist together.
- **Branches** are parallel *versions* of the whole project — one active at a time.
- **Local vs GitHub:** commits and branches live on your computer until you **push** them.
- **Daily loop:** `git status` → edit files → `git add` → `git commit -m "..."` → `git push`.
