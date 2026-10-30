---
tags: [learning, git, github]
topic: Git and GitHub
category: Developer Tools
---

# 🔀 Git and GitHub

## What Is It?

**Git** is a version control system — it tracks every change you make to your code, so you can go back to any previous version if something breaks. Think of it as an "undo" system on steroids.

**GitHub** is a website that hosts your Git repositories online, so you can share code, collaborate with others, and showcase your projects to the world.

## Why Is It Important?

- **Every developer uses Git** — it's a non-negotiable skill
- **Saves your code** — never lose work again
- **Collaboration** — work with teammates without overwriting each other's code
- **Portfolio** — your GitHub profile shows recruiters your real projects
- **Required for jobs** — you will use Git every single day as a software engineer

## Syntax / Concepts

### Essential Commands
```bash
# Setup
git init                          # Initialize a new repository
git clone <url>                   # Download a remote repository

# Daily workflow
git status                        # See what files changed
git add .                         # Stage all changes
git add <file>                    # Stage specific file
git commit -m "description"       # Save changes with a message
git push                          # Upload to GitHub
git pull                          # Download latest changes

# Branching
git branch                        # List branches
git branch <name>                 # Create new branch
git checkout <name>               # Switch to branch
git checkout -b <name>            # Create and switch
git merge <branch>                # Merge branch into current

# History
git log --oneline                 # View commit history
git diff                          # See unstaged changes
```

### Good Commit Messages
```
✅ Good:
git commit -m "Add user registration form with validation"
git commit -m "Fix: messages disappearing before sending"
git commit -m "Update donation listing API to use pagination"

❌ Bad:
git commit -m "fix stuff"
git commit -m "update"
git commit -m "asdfgh"
```

### .gitignore
```
# Common entries for your projects
node_modules/
__pycache__/
.env
*.pyc
.DS_Store
venv/
```

## Example

```bash
# Typical workflow for your projects
# 1. Start working on a new feature
git checkout -b feature/messaging

# 2. Make changes to your code
# ... edit files ...

# 3. Check what changed
git status

# 4. Stage and commit
git add .
git commit -m "Add messaging component with send functionality"

# 5. Push to GitHub
git push origin feature/messaging

# 6. When feature is complete, merge into main
git checkout main
git pull
git merge feature/messaging
git push
```

## How It Works

1. **Working Directory** — where you edit files
2. **Staging Area** — `git add` puts files here (ready to save)
3. **Repository** — `git commit` saves a snapshot of staged files
4. **Remote** — `git push` uploads to GitHub

```
Edit files → git add → git commit → git push
             (stage)    (save)       (upload)
```

## Common Mistakes

1. **Committing `.env` files** — NEVER push secrets to GitHub. Use `.gitignore`
2. **Huge commits** — commit small, focused changes, not entire features at once
3. **Not pulling before pushing** — always `git pull` first to avoid conflicts
4. **Working on main branch** — use feature branches for new work
5. **Vague commit messages** — write clear, descriptive messages

## Debugging Tips

- **`git log --oneline`** — see recent commits to find when a bug was introduced
- **`git diff`** — see exactly what changed
- **`git stash`** — temporarily save changes if you need to switch branches
- **`git reset HEAD~1`** — undo the last commit (keeps changes)

## Practice

- [ ] Create a new repository on GitHub and clone it locally
- [ ] Practice the add → commit → push workflow
- [ ] Create a branch, make changes, and merge it back to main
- [ ] Write 5 descriptive commit messages for imaginary changes
- [ ] Create a proper `.gitignore` for a React + Flask project

## My Understanding

> Write your own explanation here after studying.

## Related Notes

- [[Software Engineering]]
- [[Bayanihan Hub]]
- [[Incident Monitoring System]]
