# Git Command Reference Guide

A practical guide to Git commands, workflows, and troubleshooting for software development teams.

---

# Table of Contents

1. Git Basics
2. Repository Setup
3. Branch Management
4. Pulling and Pushing Changes
5. Merging Branches
6. Resolving Merge Conflicts
7. Undoing Changes
8. Viewing History
9. Stashing Work
10. Remote Repository Management
11. Tags and Releases
12. Common Team Workflows
13. Troubleshooting Guide

---

# 1. Git Basics

## Check Git Version

```bash
git --version
```

Used to verify Git is installed.

---

## Configure Git Username

```bash
git config --global user.name "Your Name"
```

Example:

```bash
git config --global user.name "Joshua Sutherland"
```

---

## Configure Git Email

```bash
git config --global user.email "you@example.com"
```

---

## View Current Configuration

```bash
git config --list
```

---

# 2. Repository Setup

## Clone Existing Repository

```bash
git clone https://github.com/company/project.git
```

Downloads a repository from GitHub.

---

## Initialize New Repository

```bash
git init
```

Creates a new Git repository.

---

## Check Repository Status

```bash
git status
```

Shows:

* Modified files
* New files
* Deleted files
* Current branch

This should be your most frequently used Git command.

---

# 3. Branch Management

## View Branches

```bash
git branch
```

Example:

```bash
* Josh_API
  Release
  master
```

The asterisk (*) indicates the current branch.

---

## View Local and Remote Branches

```bash
git branch -a
```

---

## Create New Branch

```bash
git branch FeatureBranch
```

---

## Create and Switch to Branch

```bash
git checkout -b FeatureBranch
```

or

```bash
git switch -c FeatureBranch
```

---

## Switch Branches

```bash
git checkout BranchName
```

or

```bash
git switch BranchName
```

Example:

```bash
git switch Josh_API
```

---

## Delete Branch

```bash
git branch -d BranchName
```

Force delete:

```bash
git branch -D BranchName
```

---

# 4. Pulling and Pushing Changes

## Fetch Latest Changes

```bash
git fetch
```

Downloads changes without merging.

---

## Pull Latest Changes

```bash
git pull
```

Downloads and merges changes.

---

## Pull Specific Branch

```bash
git pull origin master
```

---

## Push Current Branch

```bash
git push
```

---

## Push Branch to Remote

```bash
git push origin BranchName
```

Example:

```bash
git push origin Josh_API
```

---

# 5. Merging Branches

## Understanding Merge Direction

You merge FROM a source branch INTO your current branch.

Syntax:

```bash
git checkout TargetBranch
git merge SourceBranch
```

---

## Example: Merge Master into Josh_API

### Step 1

Update master

```bash
git checkout master
git pull origin master
```

### Step 2

Switch back

```bash
git checkout Josh_API
```

### Step 3

Merge

```bash
git merge master
```

Result:

All changes from master are brought into Josh_API.

---

## Example: Merge Release into Josh_API

```bash
git checkout Josh_API
git merge Release
```

---

## Fast Forward Merge

```bash
git merge feature
```

Git simply moves branch pointer forward.

No merge commit created.

---

## Merge with Commit

```bash
git merge --no-ff feature
```

Always creates merge history.

Useful for team projects.

---

# 6. Resolving Merge Conflicts

## Identify Conflicts

```bash
git status
```

Example:

```text
both modified: API.js
```

---

## Open Conflicted File

Git will mark conflicts:

```text
<<<<<<< HEAD
Current branch code
=======
Incoming branch code
>>>>>>> master
```

Choose the desired code.

---

## Mark Conflict Resolved

```bash
git add .
```

---

## Complete Merge

```bash
git commit
```

---

# 7. Undoing Changes

## Unstage File

```bash
git restore --staged filename
```

---

## Discard Local Changes

```bash
git restore filename
```

---

## Discard All Local Changes

```bash
git restore .
```

---

## Revert Commit

Safest option.

```bash
git revert CommitHash
```

Creates a new commit that reverses changes.

---

## Reset Last Commit (Keep Files)

```bash
git reset --soft HEAD~1
```

---

## Reset Last Commit (Remove Changes)

```bash
git reset --hard HEAD~1
```

Warning:
This permanently removes changes.

---

# 8. Viewing History

## Commit History

```bash
git log
```

---

## Condensed History

```bash
git log --oneline
```

Example:

```text
a4c72b Updated API endpoint
f1c983 Added README
```

---

## Graph View

```bash
git log --graph --oneline --all
```

Useful for understanding merges.

---

## View Specific Commit

```bash
git show CommitHash
```

---

# 9. Stashing Work

## Save Current Work

```bash
git stash
```

Stores unfinished changes.

---

## View Stashes

```bash
git stash list
```

---

## Restore Latest Stash

```bash
git stash pop
```

---

## Restore Without Removing

```bash
git stash apply
```

---

# 10. Remote Repository Management

## View Remotes

```bash
git remote -v
```

---

## Add Remote

```bash
git remote add origin https://github.com/company/project.git
```

---

## Change Remote URL

```bash
git remote set-url origin NEW_URL
```

---

# 11. Tags and Releases

## Create Tag

```bash
git tag v1.0.0
```

---

## Push Tag

```bash
git push origin v1.0.0
```

---

## View Tags

```bash
git tag
```

---

# 12. Common Team Workflows

## Daily Workflow

### Update Local Branch

```bash
git checkout master
git pull origin master
```

### Switch to Working Branch

```bash
git checkout Josh_API
```

### Merge Latest Changes

```bash
git merge master
```

### Make Changes

Edit files.

### Stage Files

```bash
git add .
```

### Commit

```bash
git commit -m "Implemented API service layer"
```

### Push

```bash
git push origin Josh_API
```

---

## Creating a New Feature

```bash
git checkout master
git pull origin master
git checkout -b NewFeature
```

Work normally.

```bash
git add .
git commit -m "Added new feature"
git push origin NewFeature
```

---

# 13. Troubleshooting Guide

## Which Branch Am I On?

```bash
git branch
```

Current branch has *

---

## What Changed?

```bash
git status
```

---

## What Did I Change?

```bash
git diff
```

---

## Compare Branches

```bash
git diff master..Josh_API
```

---

## Fetch Everything

```bash
git fetch --all
```

---

## Remove Untracked Files

```bash
git clean -fd
```

Warning:
Deletes untracked files permanently.

---

# Most Common Commands

```bash
git status

git branch -a

git checkout BranchName

git pull origin master

git merge master

git add .

git commit -m "message"

git push origin BranchName

git log --oneline

git diff
```

If you only remember ten Git commands, make them these.
