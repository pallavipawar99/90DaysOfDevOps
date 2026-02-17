# Day 24 Notes – Git Merge & Rebase

---

# 🔹 Git Merge

## What is a fast-forward merge?

A fast-forward merge happens when the main branch has no new commits since the feature branch was created.

Git simply moves the main pointer forward to the latest commit.  
No extra merge commit is created.

History looks like a straight line.

---

## When does Git create a merge commit?

Git creates a merge commit when:
- Both branches have new commits
- The histories have diverged

Git combines both histories and creates a special merge commit.

---

## What is a merge conflict?

A merge conflict happens when:
- Two branches modify the same file
- And the same line is changed differently

Git cannot decide which version to keep.  
You must edit the file and resolve it manually.

---

# 🔹 Git Rebase

## What does rebase actually do?

Rebase moves your branch to a new base commit.

It takes your commits and replays them on top of another branch (usually main).

This makes it look like your work started from the latest version of main.

---

## How is rebase history different from merge?

Merge:
- Keeps branch history
- Creates merge commits
- History looks like a tree

Rebase:
- Creates a clean, linear history
- No merge commits
- Looks like a straight line

---

## Why should you never rebase shared commits?

Because rebase rewrites commit history.

If commits are already pushed and shared:
- Other developers will have different history
- It causes confusion and conflicts

Rule:
Never rebase public/shared commits.

---

## When to use rebase vs merge?

Use rebase:
- For cleaning up local commits
- Before pushing your branch
- To keep history linear

Use merge:
- When working in teams
- When commits are already shared
- To preserve full history

---

# 🔹 Squash Merge

## What does squash merging do?

Squash merge combines all commits from a feature branch into ONE single commit before merging into main.

Even if the branch has 5 commits, main will receive only 1 commit.

This creates a cleaner history.

---

## What happens when using --squash?

- Git collects all changes from the branch
- Turns them into staged changes
- You create ONE new commit on main
- Branch history is not preserved

---

## How many commits appear on main after squash?

Only ONE commit appears on main, no matter how many commits were in the branch.

---

# 🔹 Regular Merge

Regular merge:
- Keeps all commits from the branch
- Preserves full history
- Often creates a merge commit

History shows all small commits.

---

## When to use squash merge vs regular merge?

Use squash merge:
- For small fixes or messy commits
- When you want clean history
- For typo/formatting commits
- In pull requests for cleanup

Use regular merge:
- For big features
- When commit history matters
- When working in teams
- When you want full traceability

---

## Trade-off of squashing

Pros:
- Clean history
- Easier to read logs

Cons:
- Lose detailed commit history
- Hard to see step-by-step progress

---

# 🔹 Git Stash

## What is git stash?

Git stash temporarily saves your uncommitted changes so you can switch branches without committing.

It acts like a clipboard for your work-in-progress.

Your changes are saved and your working directory becomes clean.

---

## What happens if you try to switch branches with uncommitted changes?

- Git may block the switch if changes conflict
- Or carry changes to the new branch
- This can create confusion

Stash helps avoid this problem.

---

## Difference between git stash pop and git stash apply

git stash pop:
- Applies the stash
- Removes it from stash list

git stash apply:
- Applies the stash
- Keeps it in stash list

Simple meaning:
pop = apply + delete  
apply = apply only

---

## When would you use stash in real workflow?

- Urgent bug fix while mid-work
- Switching tasks quickly
- Testing something on another branch
- Pulling latest changes without committing
- Saving incomplete work safely

Stash is useful for temporary work storage.

# Day 24 Notes – Git Cherry-Pick

---

# 🔹 Cherry-Picking

## What does cherry-pick do?

Cherry-pick lets you copy a specific commit from one branch and apply it to another branch.

Instead of merging the whole branch, you select only the commit you need.

---

## How cherry-pick works

- Each commit has a unique ID (hash)
- You pick a commit by its ID
- Git applies that exact change to your current branch

---

## When would you use cherry-pick?

- Applying an important bug fix to main
- Moving a hotfix without merging a full feature
- Reusing a specific change in another branch
- Backporting fixes to older versions

Example:
A bug is fixed in a feature branch but you need it in production immediately.

---

## What can go wrong with cherry-picking?

- Merge conflicts may occur
- Duplicate commits can appear in history
- Can create messy

