Perfect. Since you're practicing on **AWS EC2 (Amazon Linux)** and GitHub, here's a **real-world GitHub DevOps Practice Assignment** that covers **100% of the topics** from your instructor's notes.

---

# Git & GitHub Complete Practice Assignment

## Scenario

You have joined **ABC Cloud Solutions** as a DevOps Engineer.

Your task is to create a project repository, maintain documentation, collaborate using branches, ignore unnecessary files, stash work, rebase, merge, cherry-pick commits, and push everything to GitHub.

---

# Part 1 - Repository Creation

### Task 1

Create a GitHub repository.

Repository Name

```
devops-git-practice
```

Repository should be

* Public
* Add README
* Add MIT License
* Do NOT add .gitignore yet

---

### Verify

```
git --version
python --version
git status
```

---

# Part 2 - Clone Repository

Clone the repository inside your EC2.

```
git clone <repo-url>
```

Go inside

```
cd devops-git-practice
```

Verify

```
git branch --show-current
git remote -v
git status
```

---

# Part 3 - Documentation

Update README.md with

```
# DevOps Git Practice

This repository is created for learning Git and GitHub.

Topics Covered

- Git Basics
- Git Branching
- Git Merge
- Git Rebase
- Git Stash
- Git Cherry Pick
- Git Collaboration
```

Commit

```
git add README.md
git commit -m "Added project documentation"
git push origin main
```

---

# Part 4 - Create Project Files

Create

```
docs/

project/

src/
```

Create files

```
docs/README.md

project/README.md

src/helloworld.py

LICENSE.txt
```

Python code

```python
print("Hello GitHub")
```

Commit

```
git add .
git commit -m "Added project structure"
git push origin main
```

---

# Part 5 - Create .gitignore

Create

```
.gitignore
```

Add

```
*.log

*.tmp

terraform.tfstate

.terraform/

bin/

obj/

target/

__pycache__/

*.pyc

.vscode/

.idea/
```

Also add comments

```
# Terraform

# Python

# Java

# Dotnet
```

Commit

```
git add .
git commit -m "Added gitignore"
git push
```

---

# Part 6 - Test .gitignore

Create

```
touch terraform.tfstate

touch sample.log

touch temp.tmp
```

Run

```
git status
```

Expected

None of these files should appear.

---

# Part 7 - Update Python Code

Modify

```
helloworld.py
```

Add

```python
print("Git Practice")
print("AWS EC2")
```

Commit

```
git add src/helloworld.py

git commit -m "Updated python application"

git push
```

---

# Part 8 - Git Pull

Go to GitHub website

Edit README

Add

```
Repository updated remotely.
```

Now EC2

```
git pull
```

Verify

```
cat README.md
```

---

# Part 9 - Branch Practice

Create

```
feature-login
```

```
git checkout -b feature-login
```

Create

```
login.py
```

Commit

```
git add .

git commit -m "Added login feature"

git push origin feature-login
```

Verify branch

```
git branch

git branch -a

git branch --show-current
```

---

# Part 10 - Second Branch

Create

```
feature-dashboard
```

```
git checkout main

git checkout -b feature-dashboard
```

Create

```
dashboard.py
```

Commit

```
git add .

git commit -m "Added dashboard"

git push origin feature-dashboard
```

---

# Part 11 - Merge

Switch

```
git checkout main
```

Merge

```
git merge feature-login
```

Push

```
git push
```

---

# Part 12 - Rebase

Checkout

```
git checkout feature-dashboard
```

Rebase

```
git rebase main
```

Push

```
git push --force-with-lease
```

---

# Part 13 - Git Stash

Modify

```
helloworld.py
```

Do NOT commit.

Run

```
git status
```

Stash

```
git stash
```

Verify

```
git stash list
```

Restore

```
git stash apply
```

Drop

```
git stash drop
```

---

# Part 14 - Cherry Pick

Create

```
git checkout -b hotfix
```

Modify

```
helloworld.py
```

Commit

```
git add .

git commit -m "Fixed startup issue"
```

Find commit

```
git log --oneline
```

Copy commit ID.

Switch

```
git checkout main
```

Cherry pick

```
git cherry-pick <commit-id>
```

Push

```
git push
```

---

# Part 15 - Delete Branch

Delete local branch

```
git branch -d hotfix
```

Delete remote

```
git push origin --delete hotfix
```

---

# Part 16 - Collaboration Practice

Create another GitHub account (or collaborate with a friend).

Repository Owner

Invite collaborator.

Collaborator should

```
Clone repository

Create branch

Commit code

Push branch
```

Owner should

```
Review Pull Request

Merge Pull Request

Pull latest changes

Verify
```

---

# Part 17 - Final Verification

Run

```
git status

git branch

git branch -a

git remote -v

git log --oneline --graph --decorate --all
```

---

# Deliverables

By the end of this assignment, your repository should contain:

```
devops-git-practice/
│
├── README.md
├── LICENSE.txt
├── .gitignore
│
├── docs/
│   └── README.md
│
├── project/
│   └── README.md
│
├── src/
│   ├── helloworld.py
│   ├── login.py
│   └── dashboard.py
│
└── .git/
```

---

## Skills Checklist

| Topic                     | Covered |
| ------------------------- | :-----: |
| Create GitHub Repository  |    ✅    |
| Public/Private Repository |    ✅    |
| README.md                 |    ✅    |
| LICENSE.txt               |    ✅    |
| Project Documentation     |    ✅    |
| Git Clone                 |    ✅    |
| Git Status                |    ✅    |
| Git Add                   |    ✅    |
| Git Commit                |    ✅    |
| Git Push                  |    ✅    |
| Git Pull                  |    ✅    |
| .gitignore                |    ✅    |
| Remote Repository         |    ✅    |
| Git Branch                |    ✅    |
| Branch Creation           |    ✅    |
| Branch Deletion           |    ✅    |
| Git Merge                 |    ✅    |
| Git Rebase                |    ✅    |
| Git Stash                 |    ✅    |
| Git Stash Apply           |    ✅    |
| Git Stash Drop            |    ✅    |
| Git Log                   |    ✅    |
| Git Cherry-pick           |    ✅    |
| Collaboration             |    ✅    |
| Pull Request Workflow     |    ✅    |

This assignment closely mirrors a real DevOps Git workflow and exercises every command and concept listed in your course notes.
