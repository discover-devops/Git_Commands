### What is Git Rebase?

Git rebase is a command that integrates changes from one branch into another. It works by moving or "re-basing" a sequence of commits to a new base commit. Rebase helps maintain a linear commit history, making it easier to understand and review.

### Use Cases for Git Rebase

1. **Cleaning Up History**: If you've been working on a feature branch and want to integrate it with the main branch, rebase can clean up your commit history by keeping it linear.

2. **Keeping a Branch Up-to-Date**: Rebase allows you to keep your feature branch updated with the latest changes from the main branch without merging, keeping your branch history clean.

3. **Interactive Rebase**: You can also use `git rebase -i` (interactive rebase) to edit, squash, or rearrange commits, which is helpful in scenarios where you want to revise commit messages or combine multiple commits.

---

### Step-by-Step Example of Git Rebase

#### Scenario:
You have a `main` branch and a `feature` branch. The `main` branch has new commits that the `feature` branch doesn’t have yet. You want to rebase `feature` on top of the latest `main` to bring it up to date.

#### Example Steps

1. **Initialize a Git Repository**

   ```bash
   mkdir rebase-example
   cd rebase-example
   git init
   ```

2. **Create the `main` Branch and Add Some Initial Commits**

   ```bash
   echo "Initial content" > file.txt
   git add file.txt
   git commit -m "Initial commit on main"
   ```

3. **Create a `feature` Branch**

   ```bash
   git checkout -b feature
   ```

4. **Make Some Commits in the `feature` Branch**

   ```bash
   echo "Feature content 1" >> file.txt
   git commit -am "Add feature content 1"

   echo "Feature content 2" >> file.txt
   git commit -am "Add feature content 2"
   ```

5. **Switch Back to `main` and Make New Commits**

   ```bash
   git checkout main
   echo "Main branch content 1" >> file.txt
   git commit -am "Add main branch content 1"
   ```

6. **Rebase the `feature` Branch onto `main`**

   - Switch back to the `feature` branch:
     ```bash
     git checkout feature
     ```
   - Start the rebase:
     ```bash
     git rebase main
     ```
   - Git will replay the commits from `feature` (i.e., `Add feature content 1` and `Add feature content 2`) on top of the latest `main` branch.

7. **Resolving Conflicts (If Any)**

   - If there are conflicts, Git will stop and show you the files that need resolution.
   - Open the conflicted file, resolve the conflicts, then stage the resolved files:
     ```bash
     git add file.txt
     ```
   - Continue the rebase:
     ```bash
     git rebase --continue
     ```

8. **Completing the Rebase**

   - Once all conflicts are resolved, Git will finish the rebase.
   - You now have a clean, linear history with `feature` commits based on the latest `main`.

9. **Push the Rebased Branch (if working with a remote repository)**

   - If you've rebased a branch that’s shared with others, you’ll need to use `--force` to push:
     ```bash
     git push --force origin feature
     ```

---

### Summary

Using rebase in this way creates a cleaner, linear history by putting `feature` commits on top of `main` rather than merging the branches, which would create a "merge commit." This makes the commit history easier to follow, especially in collaborative projects.

