Yes, you can restore multiple files in a single `git restore` command by specifying the files you want to restore or by using patterns. Here are several ways to do this:

### 1. Restore Specific Files

To restore specific files, list each file name separated by spaces:
```bash
git restore file1.txt file2.txt file3.txt
```
This command will discard the changes in `file1.txt`, `file2.txt`, and `file3.txt` in your working directory.

### 2. Restore All Files in a Directory

If you want to restore all files in a specific directory, specify the directory name:
```bash
git restore path/to/directory/
```
This will restore all modified files within the `path/to/directory/` back to their last committed state.

### 3. Restore All Modified Files

To restore all modified files in your working directory, use a period (`.`) to represent all files:
```bash
git restore .
```
This will revert all files in the repository to their last committed state.

### 4. Restore All Staged Files (Unstage Multiple Files)

If you want to unstage multiple files that have been staged, use the `--staged` flag:
```bash
git restore --staged file1.txt file2.txt
```
Or, to unstage all staged files at once:
```bash
git restore --staged .
```

### 5. Restore Multiple Files to a Specific Commit

If you want to restore multiple files to a specific commit, specify the `--source` option with the commit hash:
```bash
git restore --source=<commit-hash> file1.txt file2.txt
```
This will restore `file1.txt` and `file2.txt` to their state in the specified commit.

### Summary

- **Specify files**: `git restore file1.txt file2.txt`
- **Restore all files in a directory**: `git restore path/to/directory/`
- **Restore all files**: `git restore .`
- **Unstage multiple files**: `git restore --staged file1.txt file2.txt` or `git restore --staged .`
- **Restore multiple files to a specific commit**: `git restore --source=<commit-hash> file1.txt file2.txt`

These commands allow you to efficiently manage multiple files in a single restore operation.
