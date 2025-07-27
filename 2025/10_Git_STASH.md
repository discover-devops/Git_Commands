
---

# GIT LAB 7

## Git Stash

---

## OBJECTIVE

Learn how to:

* Save uncommitted changes temporarily
* Switch to a different task without losing work
* Reapply or discard stashed changes

---

## STEP 1: Setup a Git Project

```
mkdir git-lab7
cd git-lab7
git init
```

Create and commit a file

```
echo "Line one" > notes.txt
git add notes.txt
git commit -m "Initial commit"
```

---

## STEP 2: Make Some Uncommitted Changes

```
echo "Temporary line" >> notes.txt
```

Check status

```
git status
```

The file is modified but not staged or committed

---

## STEP 3: Stash the Changes

```
git stash
```

This command:

* Saves your modifications
* Restores the working directory to the last commit

Now run:

```
git status
```

You will see: nothing to commit, working tree clean
The change is temporarily hidden

---

## STEP 4: List the Stashes

```
git stash list
```

You will see something like:

```
stash at zero: WIP on main: initial commit
```

---

## STEP 5: Reapply the Last Stash

```
git stash apply
```

This brings the stashed change back into your working directory
You can now continue editing or commit it

---

## STEP 6: Drop the Stash After Applying

To delete the stash manually after applying:

```
git stash drop
```

---

## STEP 7: Stash and Apply in One Step

If you want to stash and apply in one go:

```
git stash pop
```

This restores the change and deletes the stash entry

---

## STEP 8: Stash Only Specific Files

Let us say you modified two files but want to stash only one:

```
git stash push -m "only notes file" notes.txt
```

This stashes only that file

---

## STEP 9: Clear All Stashes

To remove all stashes:

```
git stash clear
```

---

## IMPORTANT SUMMARY

| Task                     | Command         |
| ------------------------ | --------------- |
| Save current changes     | git stash       |
| Show list of stashes     | git stash list  |
| Restore last stash       | git stash apply |
| Restore and remove stash | git stash pop   |
| Remove specific stash    | git stash drop  |
| Remove all stashes       | git stash clear |

---

