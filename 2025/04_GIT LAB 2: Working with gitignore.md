step-by-step **Gitignore Lab** 
---

# GIT LAB 2: Working with gitignore

---

## OBJECTIVE

Learn how to:

* Create a `.gitignore` file
* Exclude files or folders from being tracked by Git
* Understand what happens when files are ignored

---

## STEP 1: Setup a New Git Project

Open your terminal and run:

```
mkdir gitignore-lab
cd gitignore-lab
git init
```

Now you're inside a fresh Git repo.

---

## STEP 2: Create Files and Folders

```
echo "Hello World" > notes.txt
mkdir logs
touch logs/debug.log
touch temp.txt
```

You now have:

* notes.txt (a regular file)
* logs/debug.log (inside a folder)
* temp.txt

---

## STEP 3: Create .gitignore File

```
touch .gitignore
```

Now edit the `.gitignore` file using any editor (like `nano`, `code`, or `notepad`), and add:

```
logs/
temp.txt
```

Explanation:

* `logs/` tells Git to ignore everything in the logs folder
* `temp.txt` tells Git to ignore this specific file

---

## STEP 4: Check Git Status

```
git status
```

Expected Output:

```
Untracked files:
  notes.txt
  .gitignore
```

Git is ignoring:

* logs/debug.log
* temp.txt

Because they match the rules in `.gitignore`.

---

## STEP 5: Add and Commit the Allowed Files

```
git add .gitignore notes.txt
git commit -m "Added notes and gitignore"
```

Now your repo contains:

* notes.txt
* .gitignore
* But not logs/ or temp.txt

---

## STEP 6: Verify Ignored Files

You can double-check:

```
git ls-files
```

Only tracked files will show up.

Or check what is ignored using:

```
git status --ignored
```

---

## STEP 7: Try Adding Ignored File (It Won't Work)

Try:

```
git add temp.txt
```

You’ll get no output — Git silently ignores it based on `.gitignore`.

---

## SUMMARY

| Action                                           | Result                  |
| ------------------------------------------------ | ----------------------- |
| File listed in .gitignore                        | Git will ignore it      |
| File already committed, then added to .gitignore | Git will still track it |
| Use `git status --ignored`                       | View ignored files      |

---

