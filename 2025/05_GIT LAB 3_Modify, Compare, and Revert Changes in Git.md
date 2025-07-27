
---

# GIT LAB 3

## Modify, Compare, and Revert Changes in Git

---

## OBJECTIVE

Learn how to:

* Modify a tracked file
* View differences
* Undo changes before and after commit

---

## STEP 1: Setup the Lab

First, go to your existing repo or create a new one

```
mkdir git-lab3
cd git-lab3
git init
```

Create and commit a file

```
echo "Line 1" > demo.txt
git add demo.txt
git commit -m "Initial commit"
```

---

## STEP 2: Modify the File

Edit the file

```
echo "Line 2" >> demo.txt
```

Now the file has two lines:

* Line 1
* Line 2

---

## STEP 3: View the Change

Check the status

```
git status
```

You should see:

```
modified: demo.txt
```

Now check what exactly changed

```
git diff
```

You will see:

* That Line 2 was added

---

## STEP 4: Revert Unstaged Change

Now, let us undo this modification

```
git restore demo.txt
```

This will reset the file back to the last committed version
(Line 2 will be removed)

---

## STEP 5: Modify and Stage the File Again

Add Line 2 again

```
echo "Line 2" >> demo.txt
git add demo.txt
```

Now the file is in staging area

Check the diff from staging

```
git diff --staged
```

You will see the same Line 2 addition

---

## STEP 6: Unstage the File

If you want to remove it from staging without deleting changes:

```
git restore --staged demo.txt
```

Now it is back to modified but not staged

---

## STEP 7: Commit the Change

Let us commit the modified file

```
git add demo.txt
git commit -m "Added Line 2"
```

---

## STEP 8: Revert a Committed Change

If you want to undo the last commit (but keep the changes)

```
git reset --soft HEAD~1
```

If you want to undo the last commit and discard the changes

```
git reset --hard HEAD~1
```

---

## IMPORTANT SUMMARY

| Task                                 | Command                       |
| ------------------------------------ | ----------------------------- |
| View changes not staged              | git diff                      |
| View changes staged                  | git diff --staged             |
| Undo local file edit                 | git restore file.txt          |
| Unstage a file                       | git restore --staged file.txt |
| Undo last commit but keep changes    | git reset --soft HEAD\~1      |
| Undo last commit and discard changes | git reset --hard HEAD\~1      |

---

