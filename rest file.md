To unstage a file in Git, you can use the `git reset` command. Here are the steps:

1. **Check the Status:**
   First, use the following command to check the status of your working directory:

   ```bash
   git status
   ```

   This will show you the files that are currently in the staging area.

2. **Unstage the File:**
   If you want to unstage a specific file, use the following command:

   ```bash
   git reset filename.txt
   ```

   Replace `filename.txt` with the actual name of the file you want to unstage.

   If you want to unstage all files, you can use:

   ```bash
   git reset
   ```

   This will unstage all files currently in the staging area.

3. **Check the Status Again:**
   After running the `git reset` command, you can check the status again to ensure that the file is no longer in the staging area:

   ```bash
   git status
   ```

   The file should now appear as "untracked" or under the "Changes not staged for commit" section.
