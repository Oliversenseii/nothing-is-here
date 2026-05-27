# 📘 Git Commands Cheat Sheet

A complete reference for all essential Git commands.

---

## 📦 Setup & Configuration

```bash
git config --global user.name "Your Name"        # Set your name
git config --global user.email "you@email.com"   # Set your email
git config --global core.editor "code"           # Set default editor (VS Code)
git config --list                                 # View all config settings
```

---

## 🚀 Initialize & Clone

```bash
git init                        # Initialize a new local repo
git init <folder-name>          # Init inside a specific folder
git clone <url>                 # Clone a remote repo
git clone <url> <folder-name>   # Clone into a specific folder name
```

---

## 📁 Staging & Snapshots

```bash
git status                      # Show working tree status
git add <file>                  # Stage a specific file
git add .                       # Stage all changes
git add -p                      # Interactively stage chunks
git reset <file>                # Unstage a file (keep changes)
git diff                        # Show unstaged changes
git diff --staged               # Show staged changes
git commit -m "message"         # Commit with a message
git commit -am "message"        # Stage tracked files + commit
git commit --amend              # Edit the last commit message
```

---

## 🌿 Branching

```bash
git branch                      # List local branches
git branch -a                   # List all branches (local + remote)
git branch <name>               # Create a new branch
git branch -d <name>            # Delete a branch (safe)
git branch -D <name>            # Force delete a branch
git branch -m <old> <new>       # Rename a branch
git checkout <branch>           # Switch to a branch
git checkout -b <branch>        # Create and switch to new branch
git switch <branch>             # Switch to a branch (modern)
git switch -c <branch>          # Create and switch (modern)
```

---

## 🔀 Merging & Rebasing

```bash
git merge <branch>              # Merge branch into current
git merge --no-ff <branch>      # Merge with a merge commit (no fast-forward)
git merge --abort               # Abort an ongoing merge
git rebase <branch>             # Rebase current branch onto another
git rebase -i HEAD~<n>          # Interactive rebase (last n commits)
git rebase --abort              # Abort an ongoing rebase
git rebase --continue           # Continue rebase after resolving conflicts
git cherry-pick <commit>        # Apply a specific commit to current branch
```

---

## 🌐 Remote Repositories

```bash
git remote -v                           # List remotes
git remote add origin <url>             # Add a remote
git remote remove <name>                # Remove a remote
git remote rename <old> <new>           # Rename a remote
git remote set-url origin <url>         # Change remote URL
git fetch                               # Fetch all remotes
git fetch <remote>                      # Fetch from specific remote
git pull                                # Fetch + merge
git pull --rebase                       # Fetch + rebase
git push                                # Push to remote
git push origin <branch>                # Push specific branch
git push -u origin <branch>             # Push and set upstream
git push --force                        # Force push (⚠️ overwrites remote)
git push --force-with-lease             # Safer force push
git push origin --delete <branch>       # Delete a remote branch
```

---

## 🕵️ Inspection & History

```bash
git log                         # Show commit history
git log --oneline               # Compact log (one line per commit)
git log --oneline --graph       # Visual branch graph
git log --author="Name"         # Filter by author
git log -n 5                    # Show last 5 commits
git log <file>                  # History of a specific file
git show <commit>               # Show a specific commit's details
git diff <branch1>..<branch2>   # Diff between two branches
git blame <file>                # Show who changed each line
git shortlog -sn                # Commit count per author
```

---

## ↩️ Undoing Changes

```bash
git restore <file>              # Discard unstaged changes
git restore --staged <file>     # Unstage a file
git revert <commit>             # Create a new commit that undoes a commit
git reset HEAD~1                # Undo last commit (keep changes staged)
git reset --soft HEAD~1         # Undo last commit (keep changes staged)
git reset --mixed HEAD~1        # Undo last commit (unstage changes)
git reset --hard HEAD~1         # Undo last commit (DELETE changes ⚠️)
git reset --hard origin/main    # Reset to match remote branch ⚠️
git clean -fd                   # Remove untracked files and folders
```

---

## 🗃️ Stashing

```bash
git stash                       # Stash current changes
git stash push -m "message"     # Stash with a description
git stash list                  # List all stashes
git stash pop                   # Apply latest stash and remove it
git stash apply stash@{n}       # Apply a specific stash (keep it)
git stash drop stash@{n}        # Delete a specific stash
git stash clear                 # Delete ALL stashes ⚠️
git stash branch <branch>       # Create branch from stash
```

---

## 🏷️ Tagging

```bash
git tag                         # List all tags
git tag <name>                  # Create a lightweight tag
git tag -a <name> -m "msg"      # Create an annotated tag
git tag -a <name> <commit>      # Tag a specific commit
git push origin <tag>           # Push a tag to remote
git push origin --tags          # Push all tags
git tag -d <name>               # Delete a local tag
git push origin --delete <tag>  # Delete a remote tag
```

---

## 🔍 Searching

```bash
git grep "keyword"              # Search working directory
git grep "keyword" <branch>     # Search in a specific branch
git log -S "keyword"            # Find commits that added/removed text
git log --all --grep="message"  # Search commit messages
git bisect start                # Start binary search for a bug
git bisect good <commit>        # Mark a commit as good
git bisect bad <commit>         # Mark a commit as bad
git bisect reset                # End bisect session
```

---

## 📂 File Operations

```bash
git rm <file>                   # Remove file from repo and disk
git rm --cached <file>          # Untrack file (keep on disk)
git mv <old> <new>              # Rename/move a file
```

---

## 🛠️ Advanced

```bash
git reflog                              # Show history of HEAD movements
git worktree add <path> <branch>        # Check out branch in new folder
git submodule add <url>                 # Add a submodule
git submodule update --init             # Initialize submodules
git archive --format=zip HEAD > out.zip # Export repo as zip
git gc                                  # Garbage collect / optimize repo
git count-objects -vH                   # Show repo size info
```

---

## 📝 .gitignore Tips

```bash
# Ignore a file
secret.env

# Ignore a folder
node_modules/

# Ignore by extension
*.log
*.DS_Store

# Force track an ignored file
!important.log
```

```bash
git check-ignore -v <file>      # Check why a file is ignored
git rm -r --cached .            # Remove all cached (re-apply .gitignore)
```

---

## 🔁 Common Workflows

### Start a new feature
```bash
git checkout -b feature/my-feature
# ... make changes ...
git add .
git commit -m "feat: add my feature"
git push -u origin feature/my-feature
```

### Undo last commit but keep changes
```bash
git reset --soft HEAD~1
```

### Sync fork with upstream
```bash
git remote add upstream <original-repo-url>
git fetch upstream
git merge upstream/main
```

### Squash last 3 commits
```bash
git rebase -i HEAD~3
# Change "pick" to "squash" on the commits you want to merge
```

---

> 💡 **Tip:** Use `git help <command>` or `git <command> --help` for detailed docs on any command.
