
---

# GIT LAB 8

## Git Revert and Git Log

---

## OBJECTIVE

Learn how to:

* View commit history using git log
* Revert a previous commit without rewriting history
* Understand the difference between revert and reset

---

## STEP 1: Setup a Git Project

```
mkdir git-lab8
cd git-lab8
git init
```

Create and commit a file

```
echo "Version one" > message.txt
git add message.txt
git commit -m "First commit"
```

Make a second change and commit it

```
echo "Version two" >> message.txt
git add message.txt
git commit -m "Second commit"
```

Make a third change and commit it

```
echo "Version three" >> message.txt
git add message.txt
git commit -m "Third commit"
```

---

## STEP 2: View Commit History

Run:

```
git log --oneline
```

You will see output like:

```
a3b2c1d Third commit
c2b1a0f Second commit
f1e0d9a First commit
```

Each line shows:

* A short commit ID
* The commit message

This helps you track the state of your project at each point

---

## STEP 3: Revert a Previous Commit

Let us revert the second commit

Find its commit ID from `git log`

Example:

```
git revert c2b1a0f
```

This creates a **new commit** that undoes the changes from the second commit
It does not delete any commits or history

Now run:

```
git log --oneline
```

You will see:

```
xxxxxxx Revert Second commit
a3b2c1d Third commit
c2b1a0f Second commit
f1e0d9a First commit
```

---

## STEP 4: Check File Content

Run:

```
cat message.txt
```

You will see that the line from the second commit is now removed
But the third commit is still there

---

## STEP 5: Compare Revert vs Reset

| Feature            | git revert           | git reset                       |
| ------------------ | -------------------- | ------------------------------- |
| Safe for team use  | Yes                  | No                              |
| Keeps history      | Yes                  | No (for hard or mixed)          |
| Creates new commit | Yes                  | No (only modifies history)      |
| Best use case      | Undo a commit safely | Rewind your own commits locally |

---

## STEP 6: View More Log Details

Run:

```
git log
```

This shows:

* Author
* Date
* Full commit message
* Commit hash

You can also use:

```
git log --stat
```

To view files changed and number of lines added or removed

---

## IMPORTANT SUMMARY

| Task                        | Command                      |
| --------------------------- | ---------------------------- |
| View commit history         | git log or git log --oneline |
| Revert a commit             | git revert commit\_id        |
| See file changes per commit | git log --stat               |

---

