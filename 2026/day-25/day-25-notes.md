# Day 25 – Git Reset vs Revert & Branching Strategies
---

# 🔹 Git Reset

Git reset is used to move the branch pointer to a previous commit.

It can also change the staging area and working directory depending on the mode used.

---

## Difference between --soft, --mixed, and --hard

### git reset --soft

- Moves HEAD to previous commit
- Keeps changes staged
- Code is safe

Meaning:
Commit removed, changes still ready to commit

---

### git reset --mixed (default)

- Moves HEAD to previous commit
- Unstages changes
- Keeps changes in working directory

Meaning:
Commit removed, changes become unstaged

---

### git reset --hard

- Moves HEAD to previous commit
- Deletes staged changes
- Deletes working directory changes

Meaning:
Commit and code changes are lost

---

## Which one is destructive?

git reset --hard is destructive because it deletes changes permanently.

You cannot easily recover them.

---

## When to use each?

Use --soft:
- Fix last commit message
- Combine commits

Use --mixed:
- Unstage files
- Rework changes

Use --hard:
- Discard unwanted work
- Clean working directory

---

## Should you use reset on pushed commits?

No.

Reset rewrites history.  
If commits are already pushed:
- It breaks shared history
- Causes confusion for team members

Better use revert for pushed commits.

---

# 🔹 Git Revert

Git revert is used to undo a commit by creating a new commit that reverses the changes.

It does NOT delete history.

---

## What happens when you revert a commit?

- Git creates a new commit
- This new commit undoes the changes from the selected commit
- Original commit still exists in history

Example:
If commit Y added a line, revert will create a commit that removes that line.

---

## Is the reverted commit still in history?

Yes.

The original commit stays in history.  
Revert only adds a new “undo” commit.

History remains complete.

---

## How is git revert different from git reset?

git reset:
- Removes commits from history
- Rewrites history
- Can delete changes

git revert:
- Keeps history
- Adds a new commit to undo changes
- Safer for teams

Simple meaning:
reset = erase history  
revert = undo safely

---

## Why is revert safer for shared branches?

Because it does not rewrite history.

Other team members:
- Keep same commit history
- Don’t face conflicts from rewritten history

Safe for collaboration.

---

## When to use revert vs reset?

Use revert:
- On shared branches
- On pushed commits
- In team projects

Use reset:
- On local commits
- Before pushing
- When cleaning local history

---

# Reset vs Revert – Summary

|  | git reset | git revert |
|---|---|---|
| **What it does** | Moves branch pointer back and can modify staging/working directory | Creates a new commit that undoes a previous commit |
| **Removes commit from history?** | Yes | No |
| **Safe for shared/pushed branches?** | No | Yes |
| **When to use** | Cleaning up local commits, before pushing | Undoing changes on shared or pushed branches |

---
# Day 24 Notes – Branching Strategies

---

# 🔹 1. GitFlow

## How it works
GitFlow uses multiple long-lived branches:
- main (production)
- develop (integration)
- feature branches
- release branches
- hotfix branches

Work happens in feature branches → merged to develop → then release → then main.

---

## Simple Diagram

main ────────●────────●  
              \      /
develop ──●──●──●──●  
           \  
        feature

---

## When/Where Used
- Large teams
- Enterprise projects
- Scheduled releases

---

## Pros
+ Very organized  
+ Good for versioned releases  
+ Clear structure  

## Cons
- Complex  
- Slower delivery  
- Heavy process

---

# 🔹 2. GitHub Flow

## How it works
- Only one main branch
- Create feature branches from main
- Open pull request
- Review → merge → deploy

---

## Simple Diagram

main ──●────●────●  
        \  
      feature → merge → deploy

---

## When/Where Used
- Web apps
- CI/CD environments
- Continuous deployment
- Common on GitHub

---

## Pros
+ Simple  
+ Fast releases  
+ Easy to learn  

## Cons
- Less control for big releases  
- Not ideal for strict versioning

---

# 🔹 3. Trunk-Based Development

## How it works
- Everyone works on main (trunk)
- Short-lived branches only
- Frequent small commits
- Feature flags often used

---

## Simple Diagram

main ─●─●─●─●─● (many small commits)

---

## When/Where Used
- High-performing DevOps teams
- Continuous deployment
- Companies like Google-style workflows

---

## Pros
+ Very fast delivery  
+ Fewer merge conflicts  
+ Simple structure  

## Cons
- Needs strong testing/CI  
- Risky without discipline

---

# 🔹 Answers

## Which strategy for a startup shipping fast?
GitHub Flow or Trunk-Based Development  
(both support fast releases)

---

## Which for a large team with scheduled releases?
GitFlow  
(best for planned versioning and control)

---

## Which do open-source projects commonly use?
Many open-source projects on GitHub use GitHub Flow:
- feature branch
- pull request
- review
- merge to main
