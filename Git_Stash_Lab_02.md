Example of using Git stash with step-by-step instructions.

---

### Example: Using Git Stash to Manage Temporary Changes

1. **Initialize a New Git Repository (if needed)**

   - Open your terminal.
   - Create a new directory and initialize it as a Git repository:
     ```bash
     mkdir example-repo
     cd example-repo
     git init
     ```

2. **Create a Sample File and Make Initial Commit**

   - Create a new file, `file1.txt`:
     ```bash
     echo "Initial content" > file1.txt
     ```
   - Add and commit the file:
     ```bash
     git add file1.txt
     git commit -m "Initial commit of file1.txt"
     ```

3. **Make Changes to the File without Committing**

   - Modify `file1.txt`:
     ```bash
     echo "Uncommitted changes" >> file1.txt
     ```
   - Check the file’s status:
     ```bash
     git status
     ```
   - You should see that `file1.txt` has uncommitted changes.

4. **Stash the Changes**

   - To temporarily save your changes, use:
     ```bash
     git stash
     ```
   - Run `git status` again, and you’ll see a clean working directory.

5. **Verify the Stash**

   - To see the stashes, run:
     ```bash
     git stash list
     ```
   - You should see an entry, typically labeled as `stash@{0}`.

6. **Make a New Change in Another File**

   - Let’s say you want to switch to another task and make a change to a new file, `file2.txt`:
     ```bash
     echo "Content for a new feature" > file2.txt
     git add file2.txt
     git commit -m "Add new feature in file2.txt"
     ```

7. **Apply the Stashed Changes**

   - Now, you’re ready to bring back your previous changes in `file1.txt`.
   - Use `git stash apply` to apply the latest stash:
     ```bash
     git stash apply
     ```
   - Run `git status`, and you’ll see `file1.txt` with the previously stashed changes.

8. **Remove the Applied Stash**

   - The stash is still saved in your stash list even though you've applied it. To remove it, use:
     ```bash
     git stash drop stash@{0}
     ```

9. **Pop a Stash**

   - If you have more stashes, you could also use `git stash pop` to apply and remove the latest stash in one step:
     ```bash
     git stash pop
     ```

10. **Clear All Stashes (Optional)**

    - If you want to remove all stashed changes, use:
      ```bash
      git stash clear
      ```

---

### Summary

This step-by-step example shows how to save, apply, and manage stashes in Git, which is useful when you need to save your work temporarily and return to it later without committing to the branch. 

