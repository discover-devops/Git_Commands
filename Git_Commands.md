
```markdown
# Git Commands Cheatsheet

This cheatsheet provides a quick reference guide for common Git commands used in DevOps workflows.

## 1. Configuration

### Set User Information
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Check Configuration
```bash
git config --global --list
```

## 2. Repository Initialization

### Create a New Repository
```bash
git init
```

### Clone a Repository
```bash
git clone <repository_url>
```

## 3. Working with Branches

### Create a New Branch
```bash
git branch <branch_name>
```

### Switch to a Branch
```bash
git checkout <branch_name>
```
or
```bash
git switch <branch_name>
```

### Create and Switch to a New Branch
```bash
git checkout -b <new_branch_name>
```
or
```bash
git switch -c <new_branch_name>
```

### List Branches
```bash
git branch
```

### Merge Branches
```bash
git merge <branch_name>
```

### Delete a Branch
```bash
git branch -d <branch_name>
```

## 4. Staging and Committing

### Stage Changes
```bash
git add <file_name>
```

### Stage All Changes
```bash
git add .
```

### Commit Changes
```bash
git commit -m "Commit message"
```

### Amend the Last Commit
```bash
git commit --amend
```

## 5. Checking Status and History

### Check Status
```bash
git status
```

### View Commit History
```bash
git log
```

### View Branch History Graph
```bash
git log --graph --oneline --all
```

## 6. Remote Repositories

### Add a Remote Repository
```bash
git remote add <remote_name> <remote_url>
```

### Push to a Remote Repository
```bash
git push <remote_name> <branch_name>
```

### Pull from a Remote Repository
```bash
git pull <remote_name> <branch_name>
```

### Fetch from a Remote Repository
```bash
git fetch <remote_name>
```

## 7. Tagging

### Create a Tag
```bash
git tag <tag_name>
```

### Push Tags to Remote Repository
```bash
git push --tags
```

## 8. Undoing Changes

### Discard Unstaged Changes
```bash
git checkout -- <file_name>
```

### Discard Staged Changes
```bash
git reset <file_name>
```

### Revert a Commit
```bash
git revert <commit_hash>
```

### Reset to a Specific Commit
```bash
git reset --hard <commit_hash>
```

---

This cheatsheet covers some of the most commonly used Git commands. Refer to the [official Git documentation](https://git-scm.com/doc) for more in-depth information.
```

Feel free to customize or expand upon this Markdown file based on your specific needs. This is a basic template that you can build upon for your GitHub page.
