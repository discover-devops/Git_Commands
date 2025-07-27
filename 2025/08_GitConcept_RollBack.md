
---

##  **High-Level View: Git Rollback = Two Options**

From the **first diagram**, you accurately split rollback into:

<img width="1385" height="325" alt="image" src="https://github.com/user-attachments/assets/46731e3d-e5dc-4b9d-91bf-e04d80ed2f9c" />


1. **restore** — file-level, safe, local rollback
2. **reset** — commit-level, timeline rollback (soft, mixed, hard)

This is **100% correct**. Now let’s dive into both.

---

##  **1. Git Restore – Safe, File-Level Undo**

**Use when**:

* You made changes to a file but haven't committed yet
* You want to undo modifications in the working directory or unstage files

---

###  Example 1: File Modified, Not Staged

From your second image, this is the top part.

Command:

```
git restore demo.txt
```

Effect:

* Discards local changes in **Working Directory**
* Reverts file to last committed version
* No impact on staging or repo

---
<img width="1139" height="606" alt="image" src="https://github.com/user-attachments/assets/458129cb-f5b9-4d4b-a908-6aefa1e941c8" />



###  Example 2: File Staged but Not Yet Committed

From your second image, bottom part.

Command:

```
git restore --staged demo.txt
```

Effect:

* Removes the file from the **Staging Area**
* Keeps the file in the Working Directory

---

###  Summary of `restore`:

| Use Case                    | Command                   |
| --------------------------- | ------------------------- |
| Undo changes in working dir | git restore file          |
| Unstage a file              | git restore --staged file |

---

##  **2. Git Reset – Commit-Level Rollback**

<img width="1409" height="635" alt="image" src="https://github.com/user-attachments/assets/5ccb5aa2-ffd2-4c37-aedf-9eba3f084408" />


From the third and fourth diagrams, you illustrate the **3 types** of `git reset`.

<img width="1198" height="601" alt="image" src="https://github.com/user-attachments/assets/816fc5e2-1e39-48c6-8549-29c8b2d716dd" />


---

###  SOFT Reset

> Pushes you back to just before the commit
> Keeps changes in **Staging Area**

Command:

```
git reset --soft HEAD~1
```

You can now:

* Edit files further
* Recommit with a better message
* Or unstage with `git restore --staged`

---

###  MIXED Reset

> Pushes you back to just before the commit
> Moves changes to **Working Directory**, unstagged

Command:

```
git reset --mixed HEAD~1
```

You can now:

* Review code
* Restage with `git add`
* Or discard using `git restore`

---

###  HARD Reset

> Full rewind: commit, staging, and working directory
> Danger: all changes are lost

Command:

```
git reset --hard HEAD~1
```

Use only when:

* You are sure
* Or in a local branch

---

###  Summary of `reset`:

| Type  | Keeps Changes | Keeps Staging | Destroys Everything |
| ----- | ------------- | ------------- | ------------------- |
| soft  | yes           | yes           | no                  |
| mixed | yes           | no            | no                  |
| hard  | no            | no            | yes                 |

---

##  Final Diagram (Your 4th image)
<img width="1198" height="601" alt="image" src="https://github.com/user-attachments/assets/9747b174-0046-413a-8164-918b501152ca" />


This is a great **timeline model** showing how:

* `git add` → moves forward from untracked to staging
* `git commit` → moves forward to repo
* `restore` and `reset` → help rewind

And you use boxes (`hard`, `mixed`, `soft`) to show where each reset jumps back to — that’s absolutely right.

---

##  Final Takeaway

| Tool      | Scope        | Risk           | Use For                    |
| --------- | ------------ | -------------- | -------------------------- |
| `restore` | File level   | Low            | Undo uncommitted changes   |
| `reset`   | Commit level | Medium to High | Rewind commits and history |

---


