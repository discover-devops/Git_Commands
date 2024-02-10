Step-by-step guide on how to create, add, and commit a file in Git:

1. **Initialize a Git Repository (if not already initialized):**
   If you are starting a new project, navigate to your project directory in the terminal and run the following command:

   ```bash
   git init
   ```

   This initializes a new Git repository in your project directory.

2. **Create a New File:**
   Create a new file in your project directory using your preferred text editor. For example, if you are using the command line, you can use:

   ```bash
   touch filename.txt
   ```

   Replace `filename.txt` with the desired name of your file.

3. **Add Content to the File:**
   Open the file and add some content to it. You can use any text editor of your choice.

4. **Check the Status:**
   Run the following command to check the status of your Git repository:

   ```bash
   git status
   ```

   This will show you the status of your working directory, including any untracked files.

5. **Add the File to the Staging Area:**
   To stage your new file, run the following command:

   ```bash
   git add filename.txt
   ```

   Replace `filename.txt` with the actual name of your file.

6. **Check the Status Again:**
   Run `git status` again to verify that the file has been added to the staging area.

7. **Commit the Changes:**
   Now, commit the changes using the following command:

   ```bash
   git commit -m "Initial commit"
   ```

   The `-m` flag allows you to add a commit message directly in the command line. Replace "Initial commit" with a meaningful message describing the changes you made.

8. **View Commit History:**
   You can view the commit history using:

   ```bash
   git log
   ```

