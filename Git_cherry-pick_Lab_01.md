### What is Git Cherry-Pick?

Git `cherry-pick` is a command used to apply a specific commit (or commits) from one branch into another branch. Unlike `merge` or `rebase`, which operate on branch histories, `cherry-pick` is selective and only picks specific commits.

---

### Use Case for Git Cherry-Pick

1. **Selective Commit Transfer**: When you want to bring a specific feature, fix, or change from another branch without merging the entire branch.
2. **Hotfixes**: Applying a bug fix from a development branch directly to the production branch.
3. **Feature Isolation**: Moving individual commits between branches when multiple features are being developed simultaneously.

---

### When to Use Git Cherry-Pick?

- When you don’t want to merge an entire branch but need specific changes.
- When multiple features are being developed on a single branch, and you need only one feature for a hotfix or isolated testing.
- When you accidentally commit changes to the wrong branch and need to transfer them to the correct branch.

---

### Step-by-Step Lab: Git Cherry-Pick

#### Scenario:
You have a `dev` branch with multiple commits, and you want to apply one specific commit to the `main` branch.

---

#### 1. **Setup the Repository**

   ```bash
   mkdir cherry-pick-example
   cd cherry-pick-example
   git init
   ```

#### 2. **Create a `main` Branch and Add Initial Commit**

   ```bash
   echo "Main branch content" > file.txt
   git add file.txt
   git commit -m "Initial commit on main"
   ```

#### 3. **Create a `dev` Branch and Add Commits**

   ```bash
   git checkout -b dev
   echo "Dev branch feature 1" >> file.txt
   git commit -am "Add feature 1 to dev"

   echo "Dev branch feature 2" >> file.txt
   git commit -am "Add feature 2 to dev"
   ```

#### 4. **Identify the Commit to Cherry-Pick**

   - View the commit history of the `dev` branch:
     ```bash
     git log --oneline
     ```
   - You’ll see something like this:
     ```
     b123456 (HEAD -> dev) Add feature 2 to dev
     a987654 Add feature 1 to dev
     ```
   - Note the commit hash (e.g., `a987654`) of the commit you want to cherry-pick.

#### 5. **Switch to the `main` Branch**

   ```bash
   git checkout main
   ```

#### 6. **Cherry-Pick the Commit**

   - Use the `git cherry-pick` command with the commit hash:
     ```bash
     git cherry-pick a987654
     ```
   - This applies the changes from the specified commit (`a987654`) to the `main` branch.

#### 7. **Verify the Result**

   - View the history of the `main` branch:
     ```bash
     git log --oneline
     ```
   - You should see the `Add feature 1 to dev` commit added to the `main` branch.

#### 8. **Resolving Conflicts (If Any)**

   - If there are conflicts during the cherry-pick:
     - Git will stop and notify you about the conflict.
     - Open the conflicting file(s), resolve the conflict, and stage the changes:
       ```bash
       git add file.txt
       ```
     - Continue the cherry-pick:
       ```bash
       git cherry-pick --continue
       ```

#### 9. **Pushing the Changes**

   - Push the updated `main` branch to the remote repository:
     ```bash
     git push origin main
     ```

#### 10. **Cherry-Pick Multiple Commits (Optional)**

   - If you need to cherry-pick multiple commits, you can provide a range:
     ```bash
     git cherry-pick a987654..b123456
     ```

---

### Summary

- **When to Use**: When you need specific commits from another branch without merging the entire branch history.
- **Key Advantages**:
  - Keeps the branch history clean.
  - Allows selective application of changes.

