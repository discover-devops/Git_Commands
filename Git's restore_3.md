Git's `restore` command is a helpful tool for undoing changes in your working directory or staging area. It allows you to "restore" files to a previous state without needing to use `reset`, making it safer and more focused. Here’s a step-by-step guide on how to use `git restore` for different scenarios.

### Prerequisites
1. **Initialize a New Git Repository**:
   ```bash
   mkdir git-restore-demo
   cd git-restore-demo
   git init
   ```

2. **Create and Commit a File**:
   ```bash
   echo "Hello, Git!" > example.txt
   git add example.txt
   git commit -m "Initial commit with example.txt"
   ```

3. **Make Some Changes to the File**:
   ```bash
   echo "This is a new line." >> example.txt
   ```

At this point, you have a new line added to `example.txt` but it’s not yet staged or committed. Now let’s explore `git restore` commands for different use cases.

---

### Step 1: Discard Unstaged Changes in the Working Directory

1. **View the Status**:
   ```bash
   git status
   ```
   You’ll see that `example.txt` has changes not yet staged.

2. **Restore Unstaged Changes**:
   To discard these changes, use:
   ```bash
   git restore example.txt
   ```

3. **Verify the Restoration**:
   ```bash
   git status
   ```
   This command should show that `example.txt` no longer has any changes, as `restore` has reverted it back to the last committed state.

   - **Use Case**: Useful if you want to undo changes in your working directory without affecting the staging area or commit history.

---

### Step 2: Discard Staged Changes (Unstage a File)

1. **Stage the File**:
   First, add changes to the staging area.
   ```bash
   echo "Another new line." >> example.txt
   git add example.txt
   ```

2. **View the Status**:
   ```bash
   git status
   ```
   You’ll see that `example.txt` is staged and ready for commit.

3. **Unstage the Changes Using `git restore --staged`**:
   To remove it from the staging area, run:
   ```bash
   git restore --staged example.txt
   ```

4. **Verify the Status**:
   ```bash
   git status
   ```
   Now, the file is no longer staged but the changes remain in the working directory.

   - **Use Case**: Helpful if you accidentally staged a file but don’t want it included in the next commit.

---

### Step 3: Restore a File to a Specific Commit

1. **View the Commit History**:
   ```bash
   git log --oneline
   ```
   Find the commit hash of the specific commit you want to restore.

2. **Restore the File to a Specific Commit**:
   Let’s say you want to restore `example.txt` to the state in a previous commit (using the first few characters of the commit hash for simplicity):
   ```bash
   git restore --source=<commit-hash> example.txt
   ```
   Replace `<commit-hash>` with the actual commit ID.

3. **Verify the Changes**:
   Check the file to see that it has reverted to its previous content from that commit.

   - **Use Case**: Useful if you want to revert a file to a specific version without affecting the rest of your project.

---

### Step 4: Restore All Files to the Last Commit

To discard all changes in the working directory and revert them to the last commit:
   ```bash
   git restore .
   ```

   - **Use Case**: Great for quickly discarding all modifications in your working directory if you want to start fresh from the latest commit.

---

### Step 5: Restore All Staged Changes (Unstage All Files)

1. **Stage Changes**:
   First, make and stage changes in multiple files:
   ```bash
   echo "New content" > another.txt
   git add example.txt another.txt
   ```

2. **Unstage All Changes Using `git restore --staged`**:
   To unstage all files:
   ```bash
   git restore --staged .
   ```

3. **Verify the Status**:
   ```bash
   git status
   ```
   All files will be removed from the staging area, though changes will still be present in the working directory.

   - **Use Case**: Useful for unstaging all files quickly if you need to re-evaluate what to include in the next commit.

---

### Additional Tips

- **Combining Options**: You can combine `--staged` and `--source` options to restore a file in the staging area to a specific commit.
- **Restore Help**: To see additional options, you can always run:
  ```bash
  git restore --help
  ```

### Summary

- `git restore <file>`: Discards changes in the working directory.
- `git restore --staged <file>`: Removes a file from the staging area without discarding the changes.
- `git restore --source=<commit-hash> <file>`: Restores a file to a specific commit.
- `git restore .`: Discards all unstaged changes.
- `git restore --staged .`: Unstages all files.

Using `git restore` allows you to selectively undo changes in a more targeted way without rewriting commit history, making it a safe choice for adjusting your working directory and staging area.
