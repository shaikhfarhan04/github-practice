Since you're practicing on an **AWS EC2 Amazon Linux** instance, here's a **hands-on GitHub lab** that covers all the commands and concepts from your assignment. Complete it in order without skipping steps.

---

# GitHub Practice Lab (Amazon Linux EC2)

## Objective

By the end of this lab you will learn:

* Initialize Git
* Create GitHub Repository
* Push code
* Update code
* Pull code
* Create README
* Add LICENSE
* Use .gitignore
* Create Branch
* Push Branch
* Delete Branch
* View Remote Repository
* Practice Git Commands

---

# Task 1 - Verify Software

```bash
git --version
python3 --version
pwd
whoami
ls
```

---

# Task 2 - Create Project Folder

```bash
mkdir github-practice
cd github-practice
```

Verify

```bash
pwd
ls
```

---

# Task 3 - Initialize Git

```bash
git init
```

Check

```bash
git status
```

Expected

```
On branch master/main
No commits yet
```

---

# Task 4 - Create README.md

```bash
nano README.md
```

Write

```markdown
# GitHub Practice

This project is created for Git practice.

Author: Your Name

Technology:
- Git
- GitHub
- Python
- AWS EC2
```

Save

```
CTRL + O
Enter
CTRL + X
```

Verify

```bash
cat README.md
```

---

# Task 5 - Create Python File

```bash
nano helloworld.py
```

Write

```python
print("Hello GitHub")
```

Run

```bash
python3 helloworld.py
```

Output

```
Hello GitHub
```

---

# Task 6 - Create License

```bash
nano LICENSE.txt
```

Write

```
MIT License
```

---

# Task 7 - Create .gitignore

```bash
nano .gitignore
```

Add

```text
*.log
*.pyc
__pycache__/
terraform.tfstate
terraform.tfstate.backup
.terraform/
bin/
obj/
target/
node_modules/
```

Save

---

# Task 8 - Create Ignored File

```bash
touch terraform.tfstate
```

Check

```bash
git status
```

Notice

```
terraform.tfstate
```

should **NOT** appear because of `.gitignore`.

---

# Task 9 - First Commit

Check

```bash
git status
```

Add files

```bash
git add .
```

Check

```bash
git status
```

Commit

```bash
git commit -m "Initial project setup"
```

---

# Task 10 - Create GitHub Repository

On GitHub create

```
Repository Name:
github-practice

Visibility:
Public
```

Do **NOT** initialize with README.

---

# Task 11 - Connect Local Repo

Example

```bash
git remote add origin https://github.com/<username>/github-practice.git
```

Verify

```bash
git remote -v
```

Expected

```
origin https://github.com/...
```

---

# Task 12 - Push Code

```bash
git branch -M main
```

Push

```bash
git push -u origin main
```

(Use your GitHub username and Personal Access Token when prompted.)

---

# Task 13 - Check Remote Repository

Open GitHub.

Verify

```
README.md
LICENSE.txt
helloworld.py
.gitignore
```

exist.

---

# Task 14 - Modify Code

Open

```bash
nano helloworld.py
```

Change

```python
print("Hello GitHub")

print("Learning Git")

print("AWS EC2 Practice")
```

Save

Check

```bash
git status
```

Commit

```bash
git add helloworld.py

git commit -m "Updated python program"

git push
```

---

# Task 15 - Create Another File

```bash
touch c.txt
```

Verify

```bash
ls
```

Commit

```bash
git add .

git commit -m "Added c.txt"

git push
```

---

# Task 16 - Remote Changes

Go to GitHub.

Edit README.md

Add

```markdown
## Updated from GitHub
```

Commit the change on GitHub.

---

# Task 17 - Pull Latest Code

Back on EC2

```bash
git pull
```

Verify

```bash
cat README.md
```

You should see the remote changes.

---

# Task 18 - Branch Practice

Create

```bash
git branch new
```

Check

```bash
git branch
```

Switch

```bash
git checkout new
```

Verify

```bash
git branch
```

Current branch should have `* new`.

---

# Task 19 - Work on Branch

```bash
touch new.txt
```

Commit

```bash
git add .

git commit -m "Added new branch file"
```

Push

```bash
git push origin new
```

---

# Task 20 - View Branches

Local

```bash
git branch
```

Remote

```bash
git branch -a
```

---

# Task 21 - Merge Branch

Switch

```bash
git checkout main
```

Merge

```bash
git merge new
```

Push

```bash
git push
```

---

# Task 22 - Delete Branch

Delete locally

```bash
git branch -d new
```

Delete remotely

```bash
git push origin --delete new
```

Check

```bash
git branch -a
```

---

# Task 23 - Repository Information

```bash
git remote -v
git log --oneline
git status
git branch
```

---

# Task 24 - Create a Private Repository

Create another repository on GitHub:

```
private-demo
```

Make it **Private**.

Push a simple project to it using the same steps you practiced above.

---

# Task 25 - Practice Markdown

Update `README.md` with the following:

````markdown
# GitHub Practice

## Description
Learning Git and GitHub using AWS EC2.

## Technologies
- Git
- GitHub
- Python
- AWS EC2

## Project Structure

```
README.md
LICENSE.txt
helloworld.py
.gitignore
```

## Author

Your Name
````

Commit and push the changes.

---

# Final Challenge (No Notes)

Try completing these tasks from memory:

1. Create a new GitHub repository.
2. Clone it to your EC2 instance.
3. Add a Python file.
4. Create a README.md.
5. Add a LICENSE.txt.
6. Create a `.gitignore`.
7. Commit and push the code.
8. Edit a file locally and push again.
9. Edit the README on GitHub and pull the changes.
10. Create a branch named `feature/login`.
11. Add a file `login.py` and push the branch.
12. Merge `feature/login` into `main`.
13. Delete the branch locally and on GitHub.
14. Verify the commit history with `git log --oneline`.
15. Confirm the working tree is clean with `git status`.

If you can complete the final challenge without referring to the steps, you'll have covered the essential Git and GitHub workflow used in most DevOps projects.
