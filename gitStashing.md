**Git Stashing: A Step-by-Step Example**

Git stashing is a feature that allows you to save changes in your working directory that are not ready to be committed. It's useful when you need to switch to another branch or address an urgent issue without committing incomplete changes. Here's a step-by-step example:

### Step 1: Initialize a Git Repository

If you haven't already, create a new directory and initialize a Git repository:

```bash
$ mkdir my_project
$ cd my_project
$ git init
```

### Step 2: Create and Modify Files

Create a few files and make some modifications:

```bash
$ touch file1.txt
$ echo "Content for file1" > file1.txt

$ touch file2.txt
$ echo "Content for file2" > file2.txt
```

### Step 3: Check the Status

Check the status of your working directory:

```bash
$ git status
```

### Step 4: Stash Changes

Stash the changes in your working directory:

```bash
$ git stash save "WIP: Work in progress"
```

The message `"WIP: Work in progress"` is just a description of what you are stashing. You can customize it.

### Step 5: Check the Status Again

Check the status after stashing to see that your working directory is clean:

```bash
$ git status
```

### Step 6: Switch Branch or Make Changes

Now, you can switch to another branch or make other changes without carrying the uncommitted changes from the previous branch.

### Step 7: List Stashes

List your stashes to see what you have stashed:

```bash
$ git stash list
```

### Step 8: Apply Stash

When you want to reapply your stashed changes, use `git stash apply`:

```bash
$ git stash apply
```

### Step 9: Check Status Again

Check the status to see that your changes have been reapplied:

```bash
$ git status
```

### Step 10: Commit Changes

Finally, commit the changes you reapplied:

```bash
$ git commit -m "Committing stashed changes"
```

### Conclusion:

Git stashing is a helpful feature for temporarily saving changes without committing them. It allows you to switch branches or address urgent issues without losing your work. Stashed changes can be reapplied when you are ready to continue working on them. Regularly checking the status and listing stashes helps you manage your work effectively.
