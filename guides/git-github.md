---
layout: page
title: "Guide: Git and GitHub 101"
subtitle: "Version control basics"
permalink: /guides/git-github/
---

This guide teaches you the minimum git and GitHub you need for this course, including tracking changes to your notebooks, pushing your work to a repository (repo), and understanding what version control is actually doing. This is where to start if you've never touched git.

## What is git + why should you care

Git is a tool that tracks changes to your files over time. Every time you save a meaningful change (fixed a bug, added a new analysis, cleaned a dataset) you create a **commit**: a snapshot of your work at that moment, with a short message describing what changed.

Why this matters for analysts:

- **Undo mistakes.** You can always go back to a working version if something breaks.
- **Document your decisions.** Your commit history is a log of what you changed and why, which is useful when a stakeholder asks "what did you do to the data?"
- **Reproduce your work.** Anyone with your repository can see exactly what you did, in what order.
- **Collaborate.** When you work with others, git tracks who changed what and when.

**GitHub** is a website that hosts git repositories online. Think of git as the tool on your computer, and GitHub as the place you store and share your work.

## Setup (one time only)

### Install git

**Mac:** Open Terminal and type `git --version`. If it's not installed, macOS will prompt you to install it.

**Windows:** Download from [git-scm.com](https://git-scm.com/download/win). During installation, accept the defaults. After installing, use **Git Bash** (installed automatically) instead of Command Prompt.

### Configure your identity

Git tags every commit with your name and email. Set these once:

```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@du.edu"
```

### Create a GitHub account

Go to [github.com](https://github.com) and create a free account if you don't already have one. Use your DU email or a personal email, either is fine.

## The four commands you'll use most of the time

Almost everything you do with git uses these four commands:

```bash
git status      # What's changed since my last commit?
git add .       # Stage all changes (prepare them to be committed)
git commit -m "message"   # Save a snapshot with a description
git push        # Send my commits to GitHub
```

If you learn nothing else, learn these four!

## Your first repository (step by step)

### Option A: Start from scratch

```bash
# 1. Create a folder for your project
mkdir info4340-work
cd info4340-work

# 2. Initialize git in this folder
git init

# 3. Create a file
echo "# INFO 4340 Work" > README.md

# 4. Stage the file
git add .

# 5. Commit it
git commit -m "initial commit"
```

Now go to GitHub, click **New repository**, name it `info4340-work`, and follow the instructions under "push an existing repository":

```bash
git remote add origin https://github.com/YOUR-USERNAME/info4340-work.git
git branch -M main
git push -u origin main
```

### Option B: Clone an existing repository

If a repo already exists on GitHub:

```bash
git clone https://github.com/username/repo-name.git
cd repo-name
```

Now you have a local copy. Make changes, commit, and push.

## A typical session

Here's what a typical work session looks like:

```bash
# Start of session: check status
git status

# Do your work (edit files, run notebooks, etc.)
# ...

# When you reach a meaningful stopping point:
git add .
git commit -m "clean week 3 data, fix date parsing"

# Push to GitHub when you're done for the day:
git push
```

**How often should you commit?** Every time you finish a logical unit of work. Not every 5 minutes, and not once a week. A good rhythm is committing after each cleaning step, each analysis section, each bug fix.

## Writing good commit messages

Your commit messages are a changelog for your project. Future you (and others) will read them.

**Good messages describe what changed and why:**

```
fix: filter out returned orders before revenue calculation
add: week 5 segmentation with holdout validation
clean: standardize customer segment casing
docs: add methods section to week 3 report
```

**Bad messages describe nothing useful:**

```
update
fixed stuff
asdf
final version (v3) (ACTUAL final)
```

A helpful pattern: start with a verb (`fix`, `add`, `clean`, `update`, `remove`).

## Checking your history

```bash
# See your commit log
git log --oneline

# Output looks like:
# a3b2c1d clean: standardize customer segment casing
# f4e5d6c add: week 3 data dictionary
# 7g8h9i0 initial commit
```

Each line is a commit with a unique ID and your message. This is your project's history.

## The .gitignore file

Some files shouldn't be tracked, including large datasets, API keys, temp files. Create a file called `.gitignore` in your project root:

```
# Don't track these
.env
__pycache__/
*.pyc
.DS_Store
.ipynb_checkpoints/
*.csv       # if your datasets are large; remove this line if you want to track them
```

Add and commit the `.gitignore` itself:

```bash
git add .gitignore
git commit -m "add gitignore"
```

## Common situations + what to do

### "I want to see what I changed before committing"

```bash
git diff
```

Shows line-by-line changes since your last commit. Press `q` to exit.

### "I committed something I didn't mean to"

```bash
# Undo the last commit but keep your changes
git reset --soft HEAD~1
```

Your files are unchanged and the commit is just removed from history.

### "I want to go back and look at an old version"

```bash
# See your history
git log --oneline

# Check out an old commit (read-only)
git checkout abc1234

# Come back to the latest
git checkout main
```

### "Git says I have merge conflicts"

This happens when you edited a file on GitHub (or another computer) and also edited it locally. Git doesn't know which version to keep.

For this course, the simplest fix:

```bash
# Save your local changes somewhere safe, then:
git stash
git pull
git stash pop
```

If that doesn't work, ask for help. Merge conflicts, though very frustrating, are normal.

### "I accidentally put my API key in a file"

Remove it from the file, add the file to `.gitignore`, then:

```bash
git add .
git commit -m "remove API key, add to gitignore"
git push
```

Important: the key is still in your git history. For a course project this is fine, but in professional work you'd need to rotate the key and clean the history.

## GitHub basics

### Viewing your repository

Go to `github.com/YOUR-USERNAME/YOUR-REPO`. You can see your files, commit history, and README.

### Editing files on GitHub

You can edit files directly on GitHub by clicking the pencil icon. This creates a commit on GitHub. Next time you work locally, run `git pull` first to get those changes.

### Downloading someone else's repository

```bash
git clone https://github.com/someone/their-repo.git
```

This copies their entire repo to your computer.

## What you don't need for this course

You don't need to learn any of this right now:

- **Branches** - useful for team projects, not necessary for individual coursework
- **Pull requests** - used for code review in teams
- **Rebasing** - an advanced way to rewrite history
- **CI/CD** - automated testing and deployment
- **Git GUIs** - VS Code has git built in (the Source Control panel), which you can use instead of the command line once you're comfortable with the concepts

## Quick reference

| What you want to do | Command |
|---|---|
| Check what's changed | `git status` |
| Stage all changes | `git add .` |
| Commit with a message | `git commit -m "your message"` |
| Push to GitHub | `git push` |
| Pull from GitHub | `git pull` |
| See commit history | `git log --oneline` |
| See line-by-line changes | `git diff` |
| Undo last commit (keep files) | `git reset --soft HEAD~1` |
| Clone a repository | `git clone URL` |
| Initialize a new repo | `git init` |

## Where you'll see it in INFO 4340

- **Week 4:** You'll learn about versioning as a debugging practice. Git is the most powerful option, but change logs and before/after screenshots work too.
- **Final project:** Your reproducible notebook should be in a git repo. Your commit history shows how the project evolved.
- **Professional practice:** Nearly every analytics team uses git. Learning it now is an investment that pays off immediately.
