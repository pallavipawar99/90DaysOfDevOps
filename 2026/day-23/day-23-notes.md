# Day 23 – Git Branching & Working with GitHub
---

## Challenge Tasks

### Task 1: Understanding Branches

# Day 23 Notes – Git Branching

## 1. What is a branch in Git?

A branch in Git is a separate line of development.  
It lets you work on new features or fixes without affecting the main code.

Each branch has its own commits and history from the point it was created.

---

## 2. Why do we use branches instead of committing everything to main?

We use branches to:
- Develop features safely
- Fix bugs without breaking main code
- Work on multiple tasks at the same time
- Test changes before merging

If everything is committed to main, it can become unstable and messy.

---

## 3. What is HEAD in Git?

HEAD is a pointer that tells Git:
- Which branch you are on
- Which commit is currently checked out

Usually HEAD points to the latest commit of the current branch.

---

## 4. What happens to your files when you switch branches?

When you switch branches:
- Git changes your working directory to match that branch
- Files may appear, disappear, or change
- Each branch shows its own version of files

Uncommitted changes may block switching if they conflict.

---

## Difference between origin and upstream

origin:
- Default name for your remote repository
- Usually your own GitHub repo
- Where you push your code

upstream:
- Refers to the original repository you forked from
- Used to pull updates from the main source project

Simple meaning:
origin = your repo
upstream = original repo

---

## Difference between git fetch and git pull

git fetch:
- Downloads changes from remote
- Does NOT merge them
- Safe to review changes first

git pull:
- Downloads AND merges changes
- Updates your working directory

Simple meaning:
fetch = download only
pull = download + apply changes

---

## Clone vs Fork

Difference between clone and fork:

Clone:
- Copies a repo to your local machine
- Linked to the original repo
- Used to work locally

Fork:
- Creates a copy of a repo in your GitHub account
- Used when you don’t have write access
- Common in open-source contributions

---

## When to use clone vs fork

Use clone:
- When you are a collaborator
- When you just need a local copy

Use fork:
- When contributing to others' projects
- When you don’t have push access
- In open-source work

---

## Keeping a fork in sync

Add original repo as upstream:

git remote add upstream https://github.com/original-owner/repo.git
Fetch updates:
git fetch upstream
Merge updates:
git merge upstream/main
This keeps your fork updated.

