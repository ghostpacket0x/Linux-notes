# 25. Git basics

Git records the history of a set of files. Every change is saved as a **commit**, so you can see what changed, when, and why, and go back to an earlier version if you need to. This notes repo is tracked with Git, and so are most projects you'll work on.

## Setting up Git

```bash
git --version
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
git config --global init.defaultBranch main
git config --list --show-origin | grep user
```

Git attaches your name and email to every commit, so set them once. Use an email you're happy to make public if the repo is public.

## Starting and cloning a repo

| Command | What it does | Example |
|---|---|---|
| `git init` | Turns the current folder into a Git repo | `git init` |
| `git clone <url>` | Downloads a repo, with its full history | `git clone https://github.com/<user>/<repo>.git` |
| `git remote -v` | Shows where the repo's remote copy lives | `git remote -v` |

## The basic cycle

| Command | What it does | Example |
|---|---|---|
| `git status` | Shows which files changed and what is staged | `git status` |
| `git diff` | Shows the changes not yet staged | `git diff` |
| `git add <file>` | Stages a file for the next commit | `git add notes.txt` |
| `git add .` | Stages every change in the current folder | `git add .` |
| `git commit -m "<message>"` | Saves the staged changes as a commit | `git commit -m "Add firewall section"` |
| `git log --oneline` | Shows the commit history, one line each | `git log --oneline` |
| `git show <commit>` | Shows what one commit changed | `git show HEAD` |

Write commit messages in the present tense and say what changed, for example "Add cron section" rather than "stuff".

## Sharing with a remote

| Command | What it does | Example |
|---|---|---|
| `git push` | Sends your commits to the remote | `git push` |
| `git pull` | Gets new commits from the remote and merges them | `git pull` |
| `git fetch` | Downloads new commits without changing your files | `git fetch` |

## Branches

| Command | What it does | Example |
|---|---|---|
| `git branch` | Lists local branches | `git branch` |
| `git switch -c <name>` | Creates a branch and switches to it | `git switch -c fix-cron-example` |
| `git switch main` | Switches back to main | `git switch main` |
| `git merge <branch>` | Brings a finished branch into the current one | `git merge fix-cron-example` |
| `git branch -d <name>` | Deletes a branch that has been merged | `git branch -d fix-cron-example` |

## Ignoring files

A `.gitignore` file lists files Git should never track, such as temporary files or private keys:

```
*.tmp
.DS_Store
secrets.txt
```

Commit the `.gitignore` itself. If a file was already committed, adding it to `.gitignore` isn't enough: remove it from tracking with `git rm --cached <file>`.

## Undoing things

| Command | What it does | Example |
|---|---|---|
| `git restore <file>` | Discards unstaged changes to a file | `git restore notes.txt` |
| `git restore --staged <file>` | Unstages a file, keeping its changes | `git restore --staged notes.txt` |
| `git commit --amend` | Changes the last commit message or adds a forgotten file | `git commit --amend` |
| `git revert <commit>` | Creates a new commit that undoes an old one, safe to share | `git revert HEAD` |

> `git reset --hard` throws away uncommitted changes for good. Run `git status` first, and don't use it on work you haven't saved elsewhere.

## Notes

- Commit small, related changes, so each commit has one clear purpose.
- Pull before you push, so you don't overwrite someone else's work.
- Never commit passwords, private keys, or lab answers. If one slips in, remove it and rotate the secret, because it stays in the history.

## Practice

Try the hands-on lab for this section: [labs/27-git-practice.md](../labs/27-git-practice.md)
