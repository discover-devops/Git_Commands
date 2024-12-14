Git’s `reset` command is powerful for undoing changes in your working directory and repository. It can be used in different ways depending on the “mode” you choose: `--soft`, `--mixed`, or `--hard`. Here’s a step-by-step guide to using `git reset` with each mode, explaining when to use each one.

### Prerequisites
1. **Initialize a Git Repository**:
   ```bash
   mkdir git-reset-demo
   cd git-reset-demo
   git init
   ```

2. **Create and Commit a File**:
   ```bash
   echo "Initial content" > example.txt
   git add example.txt
   git commit -m "Initial commit"
   ```

3. **Make Some Changes**:
   Add new changes to `example.txt` so we can see how `reset` affects them.
   ```bash
   echo "Some new content" >> example.txt
   git add example.txt
   git commit -m "Added some new content"
   ```

   At this point, you have two commits. Now we’ll use `git reset` to understand how it can revert or reset your changes.

---

### Step 1: Understanding `git reset` Modes

1. **`--soft` Mode**: Moves the commit pointer but keeps changes in the staging area.
2. **`--mixed` Mode** (default): Moves the commit pointer and removes changes from the staging area but keeps them in the working directory.
3. **`--hard` Mode**: Moves the commit pointer and deletes changes from both the staging area and working directory.

---

### Step 2: `git reset --soft` Example

1. **Make Another Commit**:
   ```bash
   echo "Additional content" >> example.txt
   git add example.txt
   git commit -m "Added additional content"
   ```

2. **View Commit History**:
   ```bash
   git log --oneline
   ```
   You’ll see three commits in the log.

3. **Reset with `--soft`**:
   Move back to the previous commit, keeping changes staged:
   ```bash
   git reset --soft HEAD~1
   ```

4. **Check Status**:
   ```bash
   git status
   ```
   Output shows that the changes from the last commit are now staged, ready for commit.

   - **Use Case**: `--soft` is helpful if you want to edit the previous commit or re-commit it with a different message.

---

### Step 3: `git reset --mixed` Example

1. **Add Another Commit**:
   ```bash
   echo "More content here" >> example.txt
   git add example.txt
   git commit -m "More content added"
   ```

2. **Reset with `--mixed`**:
   Move back to the previous commit, removing changes from the staging area:
   ```bash
   git reset --mixed HEAD~1
   ```

3. **Check Status**:
   ```bash
   git status
   ```
   Output shows that the changes are now in the working directory, but **not staged**.

   - **Use Case**: `--mixed` is useful if you want to keep changes in your working directory but decide not to stage or commit them.

---

### Step 4: `git reset --hard` Example

1. **Add Another Commit**:
   ```bash
   echo "Final content" >> example.txt
   git add example.txt
   git commit -m "Final content added"
   ```

2. **Reset with `--hard`**:
   Move back to the previous commit, removing all changes:
   ```bash
   git reset --hard HEAD~1
   ```

3. **Check Status**:
   ```bash
   git status
   ```
   Output shows a clean working directory; all changes from the last commit are removed.

   - **Use Case**: `--hard` is best used when you want to discard all changes and reset your project to a previous commit.

---

### Additional Tips

1. **Reset to a Specific Commit**:
   You can also reset to a specific commit hash instead of using `HEAD~1`. For example:
   ```bash
   git reset --soft <commit-hash>
   ```

2. **Undo a `--hard` Reset**:
   If you accidentally reset using `--hard`, you might be able to recover the changes using `git reflog` to find the commit and then `git reset` back to it.

### Summary

- `git reset --soft`: Moves the HEAD pointer, keeps changes staged.
- `git reset --mixed`: Moves the HEAD pointer, removes changes from staging but keeps them in the working directory.
- `git reset --hard`: Moves the HEAD pointer and discards changes from both staging and working directory.

This approach to using `git reset` allows you to manage your commits and changes efficiently. Use each mode carefully based on your needs.
