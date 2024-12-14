A **three-way merge** in Git is a merge method used when two branches have diverged from a common ancestor. In this type of merge, Git uses three points of comparison:

1. **The common ancestor commit** – the last commit both branches share.
2. **The head of the current branch** – the latest commit on the branch you are on.
3. **The head of the branch being merged** – the latest commit on the branch you are merging in.

When Git performs a three-way merge, it compares the changes made in both branches from their common ancestor and tries to reconcile those changes. If there are conflicting changes, Git will flag them as a conflict for you to resolve manually.

Here's a step-by-step tutorial to perform a three-way merge in Git.

### Step 1: Set Up a Test Repository

1. Create a new directory and initialize a Git repository:
   ```bash
   mkdir git-3-way-merge-demo
   cd git-3-way-merge-demo
   git init
   ```

2. Create an initial file in the main branch and commit it:
   ```bash
   echo "Hello, World!" > example.txt
   git add example.txt
   git commit -m "Initial commit with example.txt"
   ```

### Step 2: Create a New Branch

Create a new branch from `main` and switch to it:
   ```bash
   git checkout -b feature-branch
   ```

### Step 3: Make Changes in Both Branches

1. **On the `feature-branch`:** Make changes to `example.txt` and commit them:
   ```bash
   echo "This is a change in the feature branch." >> example.txt
   git add example.txt
   git commit -m "Update example.txt in feature branch"
   ```

2. **On the `main` branch:** Switch back to `main`, make a different change, and commit it:
   ```bash
   git checkout main
   echo "This is a change in the main branch." >> example.txt
   git add example.txt
   git commit -m "Update example.txt in main branch"
   ```

### Step 4: Attempt the Merge

1. Attempt to merge `feature-branch` into `main`:
   ```bash
   git merge feature-branch
   ```

2. Since both branches modified the same lines in `example.txt`, Git will be unable to automatically reconcile the changes and will produce a conflict.

### Step 5: Resolve the Conflict

1. Open `example.txt` in a text editor. You’ll see conflict markers that Git has inserted to show the differences:
   ```text
   <<<<<<< HEAD
   This is a change in the main branch.
   =======
   This is a change in the feature branch.
   >>>>>>> feature-branch
   ```

2. Manually edit the file to resolve the conflict, choosing what changes to keep. For example:
   ```text
   Hello, World!
   This is a change in the main branch.
   This is a change in the feature branch.
   ```

3. Save the file and mark the conflict as resolved:
   ```bash
   git add example.txt
   ```

### Step 6: Complete the Merge

1. Commit the merge with a merge message:
   ```bash
   git commit -m "Merged feature-branch into main with conflict resolution"
   ```

2. Now, `main` has the changes from both branches, and the three-way merge is complete.

### Step 7: Verify the Merge

1. Use `git log` to view the commit history and ensure the merge was successful:
   ```bash
   git log --oneline --graph
   ```

This will show a merge commit, which indicates a successful three-way merge. You can also inspect the file’s history using `git show` to verify that changes from both branches are present.

### Key Points to Remember

- **Three-way merges** are used when branches diverge from a common ancestor.
- **Conflicts** may occur if both branches have modified the same lines, requiring manual resolution.
- **Merge commits** reflect the merge operation and keep track of the branch history. 

This tutorial demonstrates a basic Git three-way merge and how to resolve conflicts to integrate changes from two branches.
