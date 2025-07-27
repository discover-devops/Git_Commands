
---

# GIT LAB 6

## Undo and Reset in Git

---

## OBJECTIVE

Learn how to:

* Undo changes in working directory
* Unstage files
* Undo commits with reset
* Safely recover from mistakes

---

## STEP 1: Setup a New Repository

```
mkdir git-lab6
cd git-lab6
git init
```

Create a file and commit it

```
echo "Original Line" > file.txt
git add file.txt
git commit -m "Initial commit"
```

---

## STEP 2: Modify the File Without Staging

```
echo "New Line" >> file.txt
```

Check status

```
git status
```

You will see the file is modified but not staged

---

## STEP 3: Undo Unstaged Change

To discard the change and go back to the last committed version

```
git restore file.txt
```

Now the file content is back to "Original Line"

---

## STEP 4: Modify and Stage the File

```
echo "Another Line" >> file.txt
git add file.txt
```

Now the change is in the staging area

To unstage it without discarding the change:

```
git restore --staged file.txt
```

The file is no longer staged but your changes are still in the file

---

## STEP 5: Commit the Change

```
git add file.txt
git commit -m "Second commit"
```

---

## STEP 6: Undo the Last Commit

To undo the last commit but keep the changes in your file:

```
git reset --soft HEAD~1
```

To undo the last commit and also unstage the changes:

```
git reset --mixed HEAD~1
```

To undo the last commit and discard changes permanently:

```
git reset --hard HEAD~1
```

---

## STEP 7: Check Logs to Understand Changes

To see recent commit history

```
git log --oneline
```

This helps you track what was undone

---

## IMPORTANT SUMMARY

| Task                             | Command                         |
| -------------------------------- | ------------------------------- |
| Undo unstaged file change        | git restore file\_name          |
| Unstage a staged file            | git restore --staged file\_name |
| Undo last commit keep changes    | git reset --soft HEAD\~1        |
| Undo last commit unstage changes | git reset --mixed HEAD\~1       |
| Undo and discard changes         | git reset --hard HEAD\~1        |

---

