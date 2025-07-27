**Lab 5: Resolving Merge Conflicts in Git** 

---

# GIT LAB 5

## Resolving Merge Conflicts

---

## OBJECTIVE

Learn how to:

* Create a merge conflict
* Understand Git conflict markers
* Manually resolve the conflict
* Complete the merge

---

## STEP 1: Setup a New Repository

```
mkdir git-lab5
cd git-lab5
git init
```

Create a file and commit it

```
echo "Line from main branch" > data.txt
git add data.txt
git commit -m "Initial commit on main"
```

---

## STEP 2: Create and Switch to a New Branch

```
git switch -c branch1
```

Modify the file

```
echo "Change from branch1" > data.txt
git add data.txt
git commit -m "Update from branch1"
```

---

## STEP 3: Switch Back to Main and Modify the Same File

```
git switch main
echo "Change from main branch" > data.txt
git add data.txt
git commit -m "Update from main"
```

Now both main and branch1 modified the same file differently

---

## STEP 4: Try to Merge and Create a Conflict

```
git merge branch1
```

You will see:

```
Auto-merging data.txt
CONFLICT content: merge conflict in data.txt
Automatic merge failed
```

---

## STEP 5: Open the File and See Conflict Markers

Open `data.txt` in any editor

You will see something like:

```
<<<<<<< HEAD
Change from main branch
=======
Change from branch1
>>>>>>> branch1
```

This means:

* HEAD section shows current branch (main)
* Bottom section shows incoming changes from branch1

---

## STEP 6: Resolve the Conflict Manually

Choose one version or combine both:

Example of resolved content:

```
Change from main branch
Change from branch1
```

Save the file

---

## STEP 7: Mark Conflict as Resolved and Commit

```
git add data.txt
git commit -m "Resolved merge conflict between main and branch1"
```

Merge is now complete

---

## STEP 8: Clean Up (Optional)

You can now delete the feature branch

```
git branch -d branch1
```

---

## IMPORTANT SUMMARY

| Task            | Command                                |
| --------------- | -------------------------------------- |
| Create conflict | Modify same file in two branches       |
| Merge branch    | git merge branch\_name                 |
| See conflict    | Git shows conflict markers in the file |
| Resolve it      | Manually edit file, then git add       |
| Finish merge    | git commit -m "message"                |

---

