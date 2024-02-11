**Git Rebasing: A Step-by-Step Example**

Git rebasing is a process of combining or modifying a sequence of commits to create a cleaner and more linear project history. It involves moving, combining, or modifying commits to produce a more organized and cohesive branch.

### Scenario:
Let's consider a scenario where you have a feature branch, and changes have been made in the main branch since you started working on your feature. You want to incorporate those changes into your feature branch without creating unnecessary merge commits.

### Step 1: Create a Feature Branch

```bash
# Create and switch to a new feature branch
$ git checkout -b feature-branch
```

### Step 2: Make Changes in Feature Branch

Make some changes in your feature branch:

```bash
$ touch feature_file.txt
$ git add feature_file.txt
$ git commit -m "Add a new feature"
```

### Step 3: Changes in the Main Branch

While you were working on your feature, changes were made in the main branch:

```bash
# Switch to the main branch
$ git checkout main

# Make some changes in the main branch
$ echo "Update main branch" >> main_file.txt
$ git add main_file.txt
$ git commit -m "Update main branch"
```

### Step 4: Rebase Feature Branch onto Main

Rebase the feature branch onto the main branch:

```bash
# Switch back to the feature branch
$ git checkout feature-branch

# Rebase feature branch onto main
$ git rebase main
```

### Step 5: Resolve Conflicts (if any)

If there are conflicts during the rebase, Git will pause and ask you to resolve them. After resolving conflicts:

```bash
# Continue the rebase
$ git rebase --continue
```

### Step 6: Complete the Rebase

Once the rebase is complete:

```bash
# Switch back to the main branch
$ git checkout main
```

### Step 7: Merge or Continue Working

Now, you have a clean feature branch that incorporates the latest changes from the main branch. You can choose to merge the feature branch into the main branch or continue working on the feature branch.

### Conclusion:

Git rebasing helps maintain a linear project history by incorporating changes from one branch into another. It avoids unnecessary merge commits and results in a cleaner and more readable history. However, it's essential to be cautious when rebasing, especially when working in a shared repository, as it rewrites commit history.
