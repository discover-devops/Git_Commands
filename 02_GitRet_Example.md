### A step-by-step guide on how to use each of the `git reset` modes (`--soft`, `--mixed`, and `--hard`) with examples from scratch.

---

## **Example Setup**

Let's first create a new Git repository and make some commits to demonstrate the `git reset` command.

### **Step 1: Initialize a New Git Repository**

```bash
mkdir git-reset-demo
cd git-reset-demo
git init
```

### **Step 2: Create an Initial File and Commit**

```bash
echo "Initial content" > file.txt
git add file.txt
git commit -m "Initial commit"
```

### **Step 3: Make Additional Commits**

Let's create a few more commits.

```bash
echo "Change 1" >> file.txt
git add file.txt
git commit -m "Added change 1"

echo "Change 2" >> file.txt
git add file.txt
git commit -m "Added change 2"

echo "Change 3" >> file.txt
git add file.txt
git commit -m "Added change 3"
```

At this point, your commit history looks like this:

```bash
git log --oneline
```

Output:
```
<commit_hash3> Added change 3
<commit_hash2> Added change 2
<commit_hash1> Added change 1
<commit_hash0> Initial commit
```

---

## **Example 1: Git Reset with `--soft`**

### **Scenario:**
You want to undo the last commit but keep the changes staged so you can recommit them.

### **Step 1: Perform a Soft Reset**

```bash
git reset --soft HEAD~1
```

This command will reset the repository to the commit before the last one (`HEAD~1`).

### **Step 2: Check the Status and Log**

```bash
git status
```

Output:
```
On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
	modified:   file.txt
```

```bash
git log --oneline
```

Output:
```
<commit_hash2> Added change 2
<commit_hash1> Added change 1
<commit_hash0> Initial commit
```

The last commit (`"Added change 3"`) is gone from the history, but the changes are still staged and ready to be recommitted.

### **Step 3: Recommit the Changes**

```bash
git commit -m "Recommitted change 3 after soft reset"
```

---

## **Example 2: Git Reset with `--mixed` (Default)**

### **Scenario:**
You want to undo the last commit and keep the changes in the working directory but unstaged.

### **Step 1: Perform a Mixed Reset**

```bash
git reset HEAD~1
```

This command will reset the repository to the commit before the last one (`HEAD~1`) and unstages the changes.

### **Step 2: Check the Status and Log**

```bash
git status
```

Output:
```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt
```

```bash
git log --oneline
```

Output:
```
<commit_hash2> Added change 2
<commit_hash1> Added change 1
<commit_hash0> Initial commit
```

The last commit (`"Added change 3"`) is gone from the history, and the changes are now in your working directory but not staged.

### **Step 3: Recommit the Changes**

If you want to recommit these changes, you first need to stage them again:

```bash
git add file.txt
git commit -m "Recommitted change 3 after mixed reset"
```

---

## **Example 3: Git Reset with `--hard`**

### **Scenario:**
You want to completely undo the last commit and discard the changes in the working directory.

### **Step 1: Perform a Hard Reset**

```bash
git reset --hard HEAD~1
```

This command will reset the repository to the commit before the last one (`HEAD~1`), and it will also discard any changes made in the last commit.

### **Step 2: Check the Status and Log**

```bash
git status
```

Output:
```
On branch main
nothing to commit, working tree clean
```

```bash
git log --oneline
```

Output:
```
<commit_hash2> Added change 2
<commit_hash1> Added change 1
<commit_hash0> Initial commit
```

The last commit (`"Added change 3"`) is gone from the history, and the changes are completely discarded from your working directory and staging area.

---

## **Example 4: Git Reset by a Specific Number of Commits**

### **Scenario:**
You want to reset the last two commits, keeping changes in the working directory.

### **Step 1: Perform a Mixed Reset by Number of Commits**

```bash
git reset HEAD~2
```

This command will reset the last two commits and keep the changes in the working directory.

### **Step 2: Check the Status and Log**

```bash
git status
```

Output:
```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
	modified:   file.txt
```

```bash
git log --oneline
```

Output:
```
<commit_hash1> Added change 1
<commit_hash0> Initial commit
```

The last two commits (`"Added change 3"` and `"Added change 2"`) are gone, but the changes are present in the working directory.

### **Step 3: Recommit the Changes**

If needed, stage and recommit the changes:

```bash
git add file.txt
git commit -m "Recommitted changes after resetting last two commits"
```

---

## **Conclusion**

The `git reset` command is an essential tool for managing your commit history and modifying your repository's state. Use the `--soft`, `--mixed`, and `--hard` options depending on how you want to handle the changes in your working directory and staging area. Always be cautious, especially when using the `--hard` option, as it can lead to data loss if not used carefully.
