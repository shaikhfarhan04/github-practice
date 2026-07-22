Here's a complete **Git Project Maintenance Practice Assignment** based on Atul Kamble's topics. You can practice everything on **AWS EC2 (Amazon Linux)** or your local machine.

---

# Git Project Maintenance Practice

**Topics Covered**

1. Push existing local code to GitHub
2. Fork an existing GitHub project
3. Create a new repository
4. Clone a repository
5. Maintain the project using Git

---

# Task 1: Push Existing Local Code to GitHub

### Step 1: Create a project

```bash
mkdir git-project-maintain
cd git-project-maintain
```

Create a file

```bash
echo "Git Project Practice" > README.md
```

Initialize Git

```bash
git init
```

Check status

```bash
git status
```

Stage files

```bash
git add .
```

Commit

```bash
git commit -m "Initial project"
```

---

### Step 2: Create Repository on GitHub

Example

```
git-project-maintain
```

Do **NOT** initialize with README.

---

### Step 3: Connect Local Repository

```bash
git remote add origin https://github.com/<username>/git-project-maintain.git
```

Verify

```bash
git remote -v
```

---

### Step 4: Push

Rename branch if required

```bash
git branch -M main
```

Push

```bash
git push -u origin main
```

Verify on GitHub.

---

# Task 2: Fork an Existing GitHub Project

Choose any public repository.

Example

```
https://github.com/octocat/Hello-World
```

Click

```
Fork
```

GitHub creates

```
yourusername/Hello-World
```

---

### Clone Your Fork

```bash
git clone https://github.com/<username>/Hello-World.git
```

Move inside

```bash
cd Hello-World
```

Check remote

```bash
git remote -v
```

Output

```
origin
```

---

### Add Original Repository

```bash
git remote add upstream https://github.com/octocat/Hello-World.git
```

Verify

```bash
git remote -v
```

Expected

```
origin
upstream
```

---

### Fetch Latest Changes

```bash
git fetch upstream
```

Merge

```bash
git merge upstream/main
```

Push

```bash
git push origin main
```

---

# Task 3: Create a New Repository and Clone It

Create repository

```
practice-clone
```

Clone

```bash
git clone https://github.com/<username>/practice-clone.git
```

Go inside

```bash
cd practice-clone
```

Create files

```bash
touch app.py
touch README.md
```

Stage

```bash
git add .
```

Commit

```bash
git commit -m "Added project files"
```

Push

```bash
git push
```

---

# Task 4: Maintain the Project

## Modify README

```bash
echo "Version 2" >> README.md
```

Check

```bash
git status
```

Commit

```bash
git add .
git commit -m "Updated README"
```

Push

```bash
git push
```

---

## Create Branch

```bash
git branch feature/login
```

Switch

```bash
git checkout feature/login
```

Or

```bash
git switch feature/login
```

---

## Add Feature

```bash
echo "Login Feature" > login.txt
```

Commit

```bash
git add .
git commit -m "Added login feature"
```

Push

```bash
git push -u origin feature/login
```

---

## Merge into Main

Switch

```bash
git checkout main
```

Merge

```bash
git merge feature/login
```

Push

```bash
git push
```

---

## Delete Branch

Local

```bash
git branch -d feature/login
```

Remote

```bash
git push origin --delete feature/login
```

---

# Task 5: Clone Existing Repository Again

```bash
cd ..
```

Clone again

```bash
git clone https://github.com/<username>/git-project-maintain.git
```

Verify

```bash
ls
```

---

# Task 6: Pull Latest Changes

```bash
git pull
```

---

# Task 7: Check Commit History

```bash
git log --oneline
```

---

# Task 8: View Differences

```bash
git diff
```

---

# Task 9: Restore Changes

Discard one file

```bash
git restore README.md
```

Discard all staged changes

```bash
git restore --staged .
```

---

# Task 10: Remove a File

```bash
rm login.txt
```

Stage deletion

```bash
git add .
```

Commit

```bash
git commit -m "Removed login file"
```

Push

```bash
git push
```

---

# Task 11: Tag a Release

```bash
git tag v1.0
```

Push tag

```bash
git push origin v1.0
```

---

# Task 12: Stash Changes

Create a change

```bash
echo "Temporary work" >> README.md
```

Save

```bash
git stash
```

List stashes

```bash
git stash list
```

Restore

```bash
git stash pop
```

---

# Task 13: Verify Remotes

```bash
git remote -v
```

---

# Task 14: Inspect Repository

```bash
git status
git branch
git log --oneline --graph
git show
git reflog
```

---

# Expected Skills After Completing This Practice

* ✅ Initialize a Git repository
* ✅ Push existing local code to GitHub
* ✅ Create and clone repositories
* ✅ Fork and sync GitHub projects
* ✅ Manage remotes (`origin` and `upstream`)
* ✅ Create, switch, merge, and delete branches
* ✅ Commit and push changes
* ✅ Pull updates from remote
* ✅ Use `git log`, `git diff`, `git restore`, and `git reflog`
* ✅ Tag releases
* ✅ Use Git stash
* ✅ Maintain a project like a real developer

This exercise closely matches the "Git Project Maintain" assignment and covers the practical Git operations commonly expected in DevOps and software development interviews.
