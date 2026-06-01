# Git Commands Cheatsheet

All the essential Git commands you need, categorized for quick reference.

---

## 1. SETUP & CONFIG

### Configure your identity
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Check configuration
```bash
git config --list --global
```

### Set default editor
```bash
git config --global core.editor "code --wait"
```

---

## 2. START & CLONE

### Initialize a new repository
```bash
git init
```

### Clone a repository
```bash
git clone <repository-url>
```

### Clone with a specific branch
```bash
git clone -b <branch> <repo-url>
```

### Clone shallow (last 1 commit)
```bash
git clone --depth 1 <repo-url>
```

---

## 3. DAILY WORKFLOW

### Check status
```bash
git status
```

### Stage changes
```bash
git add <file>
git add .          # & all changes
```

### Commit changes
```bash
git commit -m "Your message"
```

### Push changes
```bash
git push origin <branch>
```

---

## 4. BRANCHING & MERGING

### List branches
```bash
git branch
git branch -a      # all branches
```

### Create a new branch
```bash
git branch <branch-name>
```

### Switch branch
```bash
git checkout <branch-name>
```

### Create & switch to new branch
```bash
git checkout -b <branch-name>
```

### Merge branch into current branch
```bash
git merge <branch-name>
```

### Delete a branch
```bash
git branch -d <branch-name>
git branch -D <branch-name>    # force
```

---

## 5. UPDATE & SYNC

### Fetch changes from remote
```bash
git fetch origin
```

### Pull changes
```bash
git pull origin <branch>
```

### Pull with rebase
```bash
git pull --rebase origin <branch>
```

### Push changes
```bash
git push origin <branch>
```

### Push new branch & set upstream
```bash
git push -u origin <branch>
```

### Sync (fetch + pull --rebase)
```bash
git pull --rebase
```

---

## 6. VIEW & INSPECT

### View commit history
```bash
git log
```

### View commit history (graph)
```bash
git log --oneline --graph --all
```

### Show changes
```bash
git diff
```

### Show staged changes
```bash
git diff --staged
```

### Show commit details
```bash
git show <commit-hash>
```

### Show file history
```bash
git blame <file>
```

---

## 7. UNDO & REVERT

### Unstage a file
```bash
git reset <file>
```

### Discard changes in working directory
```bash
git checkout -- <file>
```

### Discard all local changes
```bash
git reset --hard HEAD
```

### Revert a commit (safe)
```bash
git revert <commit-hash>
```

### Amend last commit
```bash
git commit --amend
```

---

## 8. STASH

### Stash current changes
```bash
git stash
```

### Stash with message
```bash
git stash push -m "message"
```

### List stashes
```bash
git stash list
```

### Apply stash
```bash
git stash apply
```

### Apply & drop stash
```bash
git stash pop
```

### Drop stash
```bash
git stash drop
```

---

## 9. REMOTES

### List remotes
```bash
git remote -v
```

### Add remote
```bash
git remote add origin <repo-url>
```

### Remove remote
```bash
git remote remove origin
```

### Rename remote
```bash
git remote rename old-name new-name
```

### Set upstream branch
```bash
git branch --set-upstream-to=origin/<branch>
```

---

## POPULAR ALIASES

```bash
git config --global alias.co     checkout
git config --global alias.br     branch
git config --global alias.ci     commit
git config --global alias.st     status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last   'log -1 HEAD'
git config --global alias.visual 'gitk'
```

---

## BEST PRACTICES

* Commit small and meaningful changes
* Write clear and descriptive commit messages
* Pull before you push
* Use feature branches
* Review changes before committing
* Keep your main branch clean
* Use `.gitignore` wisely

---

## USEFUL TIPS

* `.` stands for all changes
* Use **Tab** for auto-completion
* Use `git status` frequently
* Use `git log --oneline` for quick history
* Use `git diff` to review before commit
* Use meaningful branch names
* Backup important work before major changes

---
*Source: CoderGallery (codergallery.com)*
