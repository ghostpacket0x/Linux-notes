# Lab 26: Git basics

**Goal:** make a local repo, commit changes, create a branch, merge it, and ignore a file. This lab stays local and doesn't push anywhere.

**Linked section:** [25 Git basics](../sections/25-git-basics.md)

## Steps

Create a practice repo and set your identity if you haven't yet:

```bash
mkdir git-lab && cd git-lab
git init
git config user.name "Your Name"
git config user.email "you@example.com"
echo "first line" > notes.txt
git add notes.txt
git commit -m "Add notes"
```

Make a change on a branch and merge it back:

```bash
git switch -c add-second-line
echo "second line" >> notes.txt
git commit -am "Add second line"
git switch main
git merge add-second-line
git branch -d add-second-line
git log --oneline
```

Ignore a temporary file:

```bash
echo "*.tmp" > .gitignore
echo "scratch" > work.tmp
git add .gitignore
git commit -m "Ignore temporary files"
git status
```

## What to check

- After the merge, `git log --oneline` should show two commits: `Add second line` and `Add notes`. The merge is a fast-forward, so Git doesn't create an extra merge commit.
- After the ignore step, `git status` should be clean, and `work.tmp` should not appear in it.
- `git branch` should list only `main` after `git branch -d add-second-line`.

## Clean up

```bash
cd ~ && rm -rf git-lab
```
