The `git fetch` command downloads updates from a remote repository without merging them into your local branch. It’s useful when you want to see changes from the remote repository before merging or applying them. Here’s a step-by-step guide to using `git fetch`.

---

### Step 1: Set Up Your Repository

1. **Clone a Repository** (if you don’t already have one):
   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```
   Replace `<repository-url>` with the URL of your GitHub repository, and `<repository-name>` with the name of your repository.

2. **Verify Remote Repository**:
   Check if you have a remote repository set up (usually called `origin`):
   ```bash
   git remote -v
   ```
   If you cloned the repository, `origin` should be set up automatically. Otherwise, you can add it:
   ```bash
   git remote add origin <repository-url>
   ```

---

### Step 2: Run `git fetch`

1. **Basic `git fetch`**:
   To fetch updates from the remote repository without merging them, run:
   ```bash
   git fetch origin
   ```
   This command will retrieve all new commits, branches, and tags from the remote repository but won’t change your working directory or current branch.

2. **Check Remote Changes**:
   After fetching, you can check which branches or commits were downloaded:
   ```bash
   git log origin/main --oneline
   ```
   This command shows the commit history of the remote `main` branch, allowing you to see the latest commits without merging them into your local `main`.

---

### Step 3: Fetch Specific Branches (Optional)

You can fetch a specific branch from the remote repository if you don’t need all branches.

1. **Fetch a Specific Branch**:
   ```bash
   git fetch origin feature-branch
   ```
   This will fetch only the `feature-branch` from `origin` without affecting your local branch.

2. **View Remote Branches**:
   To see all remote branches and their latest commits:
   ```bash
   git branch -r
   ```

---

### Step 4: Check the Status After Fetching

To compare changes between your local and fetched branches:
   ```bash
   git status
   ```
   Git will display information about differences between your local branch and the remote branch, if any.

---

### Step 5: Merge Fetched Changes (Optional)

After fetching, you have two options to integrate the changes:

1. **Merge Changes**:
   If you’re ready to apply the remote changes to your local branch, you can merge them:
   ```bash
   git merge origin/main
   ```
   This command merges the fetched commits from `origin/main` into your current branch.

2. **Rebase Changes** (Alternative to Merge):
   You can rebase your branch to apply the fetched changes in a linear history:
   ```bash
   git rebase origin/main
   ```

---

### Step 6: Clean Up Fetched Data (Optional)

If there are remote branches that have been deleted, you can clean up your local references:
   ```bash
   git fetch --prune
   ```
This will remove any branches from your local repository that no longer exist on the remote repository.

---

### Summary

- `git fetch origin`: Fetch all updates from the remote without merging.
- `git fetch origin <branch>`: Fetch updates for a specific branch.
- `git merge origin/<branch>`: Merge fetched changes into your current branch.
- `git rebase origin/<branch>`: Rebase your changes on top of the fetched commits.
- `git fetch --prune`: Clean up any deleted branches on the remote.

Using `git fetch` allows you to review remote changes before merging them into your work, giving you greater control over updates from collaborators.
