**Lab 9: Working with Remote Repositories** 

---

# GIT LAB 9

## Working with Remote Repositories

---

## OBJECTIVE

Learn how to:

* Connect a local repository to a remote
* Push code to GitHub or GitLab
* Pull latest updates
* Clone existing remote repositories

---

## STEP 1: Setup a Local Repository

```
mkdir git-lab9
cd git-lab9
git init
```

Create and commit a sample file

```
echo "Remote test file" > remote.txt
git add remote.txt
git commit -m "Initial commit for remote lab"
```

---

## STEP 2: Create a Remote Repository

Go to your GitHub or GitLab account

* Click on **New Repository**
* Name it for example `git-lab9`
* Do not add README or license
* Click **Create Repository**

You will be shown a remote URL, for example:

```
https colon slash slash github dot com slash yourname slash git-lab9 dot git
```

---

## STEP 3: Add the Remote to Your Local Git

Use the URL copied in step 2

```
git remote add origin https colon slash slash github dot com slash yourname slash git-lab9 dot git
```

Now verify the remote

```
git remote -v
```

You will see:

```
origin  https colon slash slash github dot com slash yourname slash git-lab9 dot git  fetch
origin  https colon slash slash github dot com slash yourname slash git-lab9 dot git  push
```

---

## STEP 4: Push Local Code to Remote

If this is your first push, run:

```
git branch -M main
git push -u origin main
```

This pushes the local `main` branch to the `origin` remote
The `-u` flag sets the upstream branch for future pushes and pulls

---

## STEP 5: Pull Changes from Remote

If someone else made changes to the remote:

```
git pull origin main
```

This will merge changes from the remote `main` branch into your local branch

---

## STEP 6: Clone a Remote Repository

If you want to copy an existing remote repository to your local system:

```
git clone https colon slash slash github dot com slash someuser slash someproject dot git
```

This will create a local folder with the entire history

---

## STEP 7: Remove or Change Remote URL

To remove:

```
git remote remove origin
```

To change the remote URL:

```
git remote set-url origin new-url
```

---

## STEP 8: Push New Commits

If you make changes locally:

```
echo "Another line" >> remote.txt
git add remote.txt
git commit -m "Updated file"
git push
```

---

## IMPORTANT SUMMARY

| Task              | Command                         |
| ----------------- | ------------------------------- |
| Add remote        | git remote add origin url       |
| Push to remote    | git push -u origin branch\_name |
| Pull from remote  | git pull origin branch\_name    |
| Clone remote repo | git clone url                   |
| View remotes      | git remote -v                   |

---

Let me know if you want to continue with **Lab 10: Git Tagging and Releases** next.
