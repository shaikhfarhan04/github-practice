Since you're practicing **AWS + Git + GitHub + VS Code + GitHub Desktop** for DevOps interviews, here's a **real-world hands-on lab** that covers every topic you listed. The idea is to simulate working on a team project.

---

# Git Practice Lab 3

## Git + VS Code + GitHub Desktop Complete Hands-on Assignment

### Objective

Manage a Python project using:

* Git CLI
* GitHub
* GitHub Desktop
* VS Code

Practice:

* Clone Repository
* Existing Project
* Remote
* Commit
* Push
* Pull
* Fetch
* Branches
* Tags
* Stash
* Pull Request
* Merge

---

# Prerequisites

Install

* Git
* VS Code
* GitHub Desktop
* GitHub Account

---

# PART 1 — Create Repository on GitHub

Create repository

```
github-desktop-practice
```

Public repository

Do NOT initialize README.

---

# PART 2 — Existing Local Project

Create folder

```
github-desktop-practice
```

Inside create

```
README.md

app.py

requirements.txt

.gitignore
```

Example

```
app.py

print("GitHub Desktop Practice")
```

---

Initialize git

```
git init
```

Check

```
git status
```

---

# PART 3 — Connect Local Project to GitHub

Copy GitHub URL

```
https://github.com/<username>/github-desktop-practice.git
```

Add remote

```
git remote add origin https://github.com/<username>/github-desktop-practice.git
```

Verify

```
git remote -v
```

---

Commit

```
git add .

git commit -m "Initial project"
```

---

Push

```
git push -u origin main
```

---

# PART 4 — Clone Repository using GitHub Desktop

Open

```
GitHub Desktop
```

Choose

```
File

Clone Repository
```

Select

```
github-desktop-practice
```

Mention Local Path

Example

```
C:\Projects\github-desktop-practice
```

Clone

---

Open Repository

```
Repository

Open in VS Code
```

---

Also open from

```
Repository

Show in Explorer
```

---

# PART 5 — Work in VS Code

Add

```
calculator.py
```

```
def add(a,b):
    return a+b
```

Commit from GitHub Desktop

Summary

```
Added calculator module
```

Commit

Push Origin

---

# PART 6 — Fetch

From another PC (or GitHub website)

Edit README.

Commit directly on GitHub.

Now in GitHub Desktop

```
Fetch Origin
```

Observe

```
Incoming Changes
```

Then

```
Pull Origin
```

Verify README updated.

---

# PART 7 — Pull

Modify

```
requirements.txt
```

Commit

Push

Now on another system change README.

Come back

```
Pull Origin
```

Resolve if conflict.

---

# PART 8 — Branch Practice

Create branch

CLI

```
git checkout -b development
```

OR

GitHub Desktop

```
Branch

New Branch

development
```

Verify

```
git branch
```

---

Create file

```
feature.py
```

```
print("Development Branch")
```

Commit

Push

```
git push origin development
```

---

Switch

```
main
```

Observe

```
feature.py disappears
```

Switch back

```
development
```

Observe

```
feature.py returns
```

---

Delete branch

```
git checkout main

git branch -d development
```

Delete remote

```
git push origin --delete development
```

---

# PART 9 — Multiple Feature Branches

Create

```
feature/login
```

Add

```
login.py
```

Commit

Push

---

Create

```
feature/profile
```

Add

```
profile.py
```

Commit

Push

Switch branches frequently.

---

# PART 10 — Stash Practice

Modify

```
app.py
```

Don't commit.

Status

```
git status
```

Create stash

```
git stash
```

Verify

```
git status
```

Working tree clean.

List

```
git stash list
```

Apply

```
git stash apply
```

Delete stash

```
git stash drop
```

Create another stash

```
git stash
```

Delete all

```
git stash clear
```

---

# PART 11 — Tags

Create

```
git tag v1.0
```

Verify

```
git tag
```

Push

```
git push origin v1.0
```

Push all

```
git push origin --tags
```

Delete local

```
git tag -d v1.0
```

Delete remote

```
git push origin --delete v1.0
```

---

# PART 12 — Pull Request

Push

```
feature/login
```

Open GitHub

Compare

```
feature/login

↓

main
```

Create Pull Request

Title

```
Added Login Feature
```

Description

```
Implemented login functionality.
```

Create PR

Merge

Delete Branch

Pull latest

```
git pull
```

---

# PART 13 — Merge Practice (CLI)

Create

```
git checkout -b feature/dashboard
```

Create

```
dashboard.py
```

Commit

Switch

```
git checkout main
```

Merge

```
git merge feature/dashboard
```

Delete

```
git branch -d feature/dashboard
```

Push

---

# PART 14 — GitHub Desktop Practice

Perform the following only using GitHub Desktop:

* Commit changes
* Push Origin
* Fetch Origin
* Pull Origin
* Create Branch
* Switch Branch
* Merge Branch
* View History
* View Changes
* Open in VS Code
* Open in Explorer
* Delete Branch

---

# PART 15 — VS Code Source Control

Using VS Code:

* Open Source Control (`Ctrl + Shift + G`)
* Stage selected files
* Unstage files
* Commit
* Push
* Pull
* View file history (with Git extensions if installed)
* Switch branches
* Resolve merge conflicts using the Merge Editor

---

# Final Repository Structure

```
github-desktop-practice/
│
├── README.md
├── .gitignore
├── requirements.txt
├── app.py
├── calculator.py
├── login.py
├── profile.py
├── dashboard.py
└── docs/
    └── project-notes.md
```

---

# Commands Covered

| Topic          | Commands/Actions                                                                            |
| -------------- | ------------------------------------------------------------------------------------------- |
| Initialize     | `git init`                                                                                  |
| Remote         | `git remote add`, `git remote -v`                                                           |
| Clone          | `git clone`, GitHub Desktop Clone                                                           |
| Commit         | `git add`, `git commit`                                                                     |
| Push           | `git push`, `git push -u origin main`                                                       |
| Pull           | `git pull`                                                                                  |
| Fetch          | `git fetch` (or **Fetch Origin** in GitHub Desktop)                                         |
| Branch         | `git branch`, `git checkout -b`, `git switch`                                               |
| Merge          | `git merge`                                                                                 |
| Delete Branch  | `git branch -d`, `git push origin --delete <branch>`                                        |
| Tags           | `git tag`, `git push origin --tags`, `git tag -d`                                           |
| Stash          | `git stash`, `git stash list`, `git stash apply`, `git stash drop`, `git stash clear`       |
| Pull Request   | Create, review, merge, and delete branch on GitHub                                          |
| VS Code        | Source Control, stage/unstage, commit, push/pull, branch switching                          |
| GitHub Desktop | Clone, commit, fetch, pull, push, branch management, history, open in VS Code/File Explorer |

Completing this lab will give you practical experience with the day-to-day Git workflow used in most software and DevOps teams, and it aligns well with interview expectations.
