Git stash to manage your changes:

### 1. **Understanding Git Stash**

   Git stash is a powerful Git feature that temporarily saves your changes in a stack, allowing you to work on a clean slate without committing those changes to the branch. You can apply these saved changes later, making it especially useful when you need to switch branches without losing progress.

### 2. **Stashing Changes**

   - Make some changes in your working directory.
   - To save (stash) these changes without committing, use:
     ```bash
     git stash
     ```
   - This command saves your current staged and unstaged changes and reverts your working directory to match the latest commit.

   **Optional Flags**:
   - `git stash -u`: Stashes untracked files as well.
   - `git stash -a`: Stashes all files, including ignored files.

### 3. **Viewing Stashed Changes**

   - To see all stashed changes in your repository, use:
     ```bash
     git stash list
     ```
   - Each stash is labeled, usually as `stash@{n}`, where `n` is the index number in the stash list.

### 4. **Applying a Stash**

   - To apply the latest stash:
     ```bash
     git stash apply
     ```
   - To apply a specific stash:
     ```bash
     git stash apply stash@{n}
     ```
   - After applying the stash, the changes will be returned to your working directory, but the stash entry remains in the stash list.

### 5. **Dropping a Stash**

   - To delete a specific stash entry:
     ```bash
     git stash drop stash@{n}
     ```
   - To remove the latest stash:
     ```bash
     git stash drop
     ```

### 6. **Popping a Stash**

   - If you want to apply a stash and remove it from the list at the same time:
     ```bash
     git stash pop
     ```
   - This command applies the latest stash and then removes it.

### 7. **Creating a Named Stash**

   - To make it easier to remember what each stash contains, you can add a message:
     ```bash
     git stash push -m "Message describing your changes"
     ```

### 8. **Stashing Only Staged Changes**

   - You may have only staged certain changes but want to stash only those staged changes:
     ```bash
     git stash push --staged
     ```

### 9. **Clearing All Stashes**

   - To remove all stash entries from your repository:
     ```bash
     git stash clear
     ```

### 10. **Applying Stashes Between Branches**

   - Switch to a different branch:
     ```bash
     git checkout <branch-name>
     ```
   - Apply the stash on the new branch using `git stash apply` or `git stash pop`.

### Example Workflow

1. **Make Changes**: Edit some files in your working directory.
2. **Stash Changes**: Use `git stash` to stash those changes.
3. **Switch Branches**: Use `git checkout <other-branch>` to switch branches.
4. **Apply Stash**: Apply the stash to the new branch using `git stash apply`.
5. **Remove Stash**: Use `git stash pop` if you want to apply and remove it.

