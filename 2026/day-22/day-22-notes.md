# Day 22 – Introduction to Git: Your First Repository

## Task

## 1) Difference between `git add` and `git commit`

- `git add` → sends your changes to the staging area (prepares them)
- `git commit` → saves those staged changes permanently in Git history

Simple:
add = prepare  
commit = save

---

## 2) What does the staging area do?

The staging area is a **preview space** where you choose what to commit.

Why Git doesn’t commit directly:
- You may change many files but want to commit only some
- Helps avoid mistakes
- Lets you organize commits better

Example:
You edited 5 files but only want 2 in the next commit → staging helps.

---

## 3) What does `git log` show?

`git log` shows:
- Commit ID (hash)
- Author name
- Date & time
- Commit message

It helps track project history.

---

## 4) What is the `.git/` folder?

`.git/` is the **brain of Git**.

It stores:
- All commits
- Branches
- Configuration
- History

If you delete `.git/`:
- All history is lost
- Folder becomes a normal directory
- Git tracking stops

---

## 5) Working Directory vs Staging Area vs Repository

### Working Directory
Where you edit files normally.

### Staging Area
Where you prepare files for commit.

### Repository
Where commits are stored permanently.

Flow:
Working Directory → Staging Area → Repository
