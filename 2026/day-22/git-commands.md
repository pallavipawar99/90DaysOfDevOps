# Git Commands Reference

## Setup & Config

### git --version
Check installed Git version  
Example:
git --version

### git config --global user.name "Your Name"
Set your Git username  
Example:
git config --global user.name "Rahul"

### git config --global user.email "you@example.com"
Set your Git email  
Example:
git config --global user.email "rahul@gmail.com"

### git config --list
View Git configuration  
Example:
git config --list

---

## Basic Workflow

### git init
Initialize a new repository  
Example:
git init

### git status
Show current repo status  
Example:
git status

### git add <file>
Stage a file  
Example:
git add git-commands.md

### git add .
Stage all files  
Example:
git add .

### git commit -m "message"
Commit staged changes  
Example:
git commit -m "Added git commands notes"

---

## Viewing Changes

### git log
Show commit history  
Example:
git log

### git log --oneline
Compact commit history  
Example:
git log --oneline

### git diff
Show changes not staged  
Example:
git diff

### git diff --staged
Show staged changes  
Example:
git diff --staged

## Branching Commands

### git branch
List branches  
Example:
git branch

### git branch <name>
Create new branch  
Example:
git branch feature-1

### git checkout <branch>
Switch branch  
Example:
git checkout feature-1

### git checkout -b <branch>
Create and switch  
Example:
git checkout -b feature-2

### git switch <branch>
Switch branch (modern way)  
Example:
git switch main

### git switch -c <branch>
Create + switch branch  
Example:
git switch -c feature-3

### git branch -d <branch>
Delete branch  
Example:
git branch -d feature-2

## Remote Commands

### git remote add origin <url>
Connect local repo to GitHub  
Example:
git remote add origin https://github.com/user/repo.git

### git remote -v
Show remote URLs  
Example:
git remote -v

### git push -u origin main
Push branch to GitHub  
Example:
git push -u origin main

### git push origin <branch>
Push specific branch  
Example:
git push origin feature-1

### git fetch
Download remote changes without merging  
Example:
git fetch origin

### git pull
Fetch and merge changes  
Example:
git pull origin main

### git clone <url>
Copy repo to local machine  
Example:
git clone https://github.com/user/repo.git

### git remote add upstream <url>
Link original repo to your fork  
Example:
git remote add upstream https://github.com/original/repo.git

### git fetch upstream
Get updates from original repo  
Example:
git fetch upstream

---

## 🔹 Merge Commands

### git merge <branch>
Merge a branch into current branch  
Example:
git merge feature-login

---

### git merge --abort
Cancel a merge during conflicts  
Example:
git merge --abort

---

### git log --oneline --graph
View history with branch graph  
Example:
git log --oneline --graph

---

### git log --oneline --graph --all
View all branches graph  
Example:
git log --oneline --graph --all

---

## 🔹 Rebase Commands

### git rebase <branch>
Rebase current branch onto another  
Example:
git rebase main

---

### git rebase --continue
Continue after resolving conflicts  
Example:
git rebase --continue

---

### git rebase --abort
Cancel rebase  
Example:
git rebase --abort

---

## 🔹 Squash Merge Commands

### git merge --squash <branch>
Combine all branch commits into one  
Example:
git merge --squash feature-profile

Then commit:
git commit -m "Add profile feature (squashed)"

---

## 🔹 Regular Merge

### git merge <branch>
Merge branch with full history  
Example:
git merge feature-settings

---

## 🔹 Git Stash Commands

### git stash
Save uncommitted changes  
Example:
git stash

---

### git stash pop
Apply and remove stash  
Example:
git stash pop

---

### git stash apply
Apply stash without removing  
Example:
git stash apply

---

### git stash list
Show all stashes  
Example:
git stash list

---

### git stash apply stash@{n}
Apply specific stash  
Example:
git stash apply stash@{1}

---

### git stash drop stash@{n}
Delete a specific stash  
Example:
git stash drop stash@{1}

---

### git stash clear
Delete all stashes  
Example:
git stash clear

---

## 🔹 Cherry-Pick Commands

### git cherry-pick <commit-hash>
Apply a specific commit to current branch  
Example:
git cherry-pick a1b2c3d

---

### git log --oneline
Find commit IDs for cherry-picking  
Example:
git log --oneline

---

### git cherry-pick --abort
Cancel cherry-pick during conflict  
Example:
git cherry-pick --abort

---

### git cherry-pick --continue
Continue after resolving conflicts  
Example:
git cherry-pick --continue
