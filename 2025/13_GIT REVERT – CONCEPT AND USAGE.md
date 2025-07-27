**concept of Git REVERT**

---

# GIT REVERT – CONCEPT AND USAGE

---

## 1. WHAT IS `git revert`

`git revert` is a **safe way to undo** a commit by creating a **new commit** that **reverses** the changes made by a previous commit.

* It **does not delete history**
* It is **safe for shared or remote branches**
* It is ideal when you want to undo something **publicly visible** but still maintain a clean history

---

## 2. HOW `git revert` WORKS

Let us say you made three commits:

```
Commit A  →  Commit B  →  Commit C
```

If you run:

```
git revert Commit B
```

Git will create a new commit like:

```
Commit A  →  Commit B  →  Commit C  →  Revert B
```

This **revert commit** undoes the changes made in Commit B without affecting C or A.

---

## 3. THREE COMMON USE CASES OR TYPES OF REVERT

### TYPE 1: Revert a Single Commit

**Use Case**: You added a wrong change in one commit

**Command**:

```
git revert commit_id
```

**Result**: One new commit is created that undoes the selected commit

---

### TYPE 2: Revert a Range of Commits (Multiple Commits)

**Use Case**: You want to undo several commits (for example, a full feature)

**Command**:

```
git revert commit_id_oldest^..commit_id_newest
```

**Example**:

```
git revert HEAD~3..HEAD
```

**Result**: Git creates multiple revert commits, one for each commit in the range

---

### TYPE 3: Revert a Merge Commit

**Use Case**: You merged a feature branch and later realize it introduced issues

**Command**:

```
git revert -m 1 merge_commit_id
```

**Explanation**:

* `-m 1` tells Git which parent to keep

  * `1` usually means the main branch
  * `2` would mean the feature branch

**Important**: Reverting merge commits can be tricky. Always double-check before pushing.

---

## 4. WHEN TO USE `git revert` INSTEAD OF `git reset`

| Situation                         | Use `revert` | Use `reset`                             |
| --------------------------------- | ------------ | --------------------------------------- |
| Branch is public or pushed        | Yes          | No                                      |
| Want to keep commit history       | Yes          | No                                      |
| Need to safely undo changes       | Yes          | No                                      |
| Rewriting your own local history  | No           | Yes                                     |
| Need to completely remove commits | No           | Yes (only in private or local branches) |

---

## 5. KEY DIFFERENCES

| Feature                        | Revert    | Reset |
| ------------------------------ | --------- | ----- |
| Modifies history               | No        | Yes   |
| Safe for shared branches       | Yes       | No    |
| Creates new commit             | Yes       | No    |
| Use for undoing remote commits | Yes       | No    |
| Use for local rollback         | Sometimes | Yes   |

---

## SUMMARY

* `git revert` is your **undo button for shared history**
* It creates a **new commit** that reverses selected changes
* Use it when working in a **team**, especially with **remote branches**

---

