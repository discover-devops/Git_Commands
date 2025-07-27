**Lab 4: Branching and Merging in Git**  step-by-step instructions.

---

# GIT LAB 4

## Branching and Merging in Git

---

## OBJECTIVE

Learn how to:

* Create and switch branches
* Make changes in a feature branch
* Merge changes into the main branch
* Handle simple merge cases

---

## STEP 1: Setup a New Git Project

```
mkdir git-lab4
cd git-lab4
git init
```

Create a file and commit it

```
echo "This is the main file" > main.txt
git add main.txt
git commit -m "Initial commit on main branch"
```

---

## STEP 2: Create a New Branch

```
git branch feature1
```

Check available branches

```
git branch
```

You will see:

```
main
feature1
```

The current branch will have a star symbol before it
To switch to the new branch:

```
git switch feature1
```

---

## STEP 3: Make Changes in Feature Branch

Create or update a file

```
echo "This is a new line in feature1 branch" >> main.txt
git add main.txt
git commit -m "Updated main.txt in feature1 branch"
```

Now you have a new commit in the feature1 branch

---

## STEP 4: Switch Back to Main Branch

```
git switch main
```

Check file content

```
cat main.txt
```

It will not show the feature1 changes yet
Main branch still has the original content

---

## STEP 5: Merge Feature Branch into Main

```
git merge feature1
```

Git will bring the changes from feature1 into main
Check the file again:

```
cat main.txt
```

Now it includes both lines

---

## STEP 6: View Commit History

Use this to see a simple log

```
git log --oneline --graph
```

This will show how the branches were merged

---

## STEP 7: Delete the Feature Branch

After merging, if the feature branch is no longer needed

```
git branch -d feature1
```

This removes the branch from the list (safe to delete after merge)

---

## IMPORTANT SUMMARY

| Task              | Command                    |
| ----------------- | -------------------------- |
| Create new branch | git branch branch\_name    |
| Switch to branch  | git switch branch\_name    |
| Create and switch | git switch -c branch\_name |
| Merge a branch    | git merge branch\_name     |
| Delete a branch   | git branch -d branch\_name |

---

