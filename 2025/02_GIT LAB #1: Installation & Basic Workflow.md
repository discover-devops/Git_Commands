 **Step-by-Step Git Labs** guide with clear explanations and practical commands. 

---

#  GIT LAB #1: Installation & Basic Workflow

---

##  **1. Git Installation**

###  For Windows:

* Download from: [https://git-scm.com/download/win](https://git-scm.com/download/win)
* Run installer and follow defaults (includes Git Bash)

###  For Linux (Ubuntu/Debian):

```bash
sudo apt update
sudo apt install git
```

###  For macOS (using Homebrew):

```bash
brew install git
```

---

##  **2. How Git Works Internally (Simplified)**

Think of Git like a **3-stage process**:

| Stage                           | Description                                    |
| ------------------------------- | ---------------------------------------------- |
| 1️ Working Directory           | Where you edit/create files (normal OS folder) |
| 2️ Staging Area (Index)        | A prep zone: files you selected for commit     |
| 3️ Repository (Commit History) | Permanent snapshot stored in `.git`            |

---

##  **3. Create a New File & Initialize Git**

###  Step-by-step:

```bash
mkdir my-git-lab
cd my-git-lab
touch hello.txt
```

 At this stage:

* `hello.txt` is just a regular file managed by the OS.
* Git has no idea it exists yet.

---

##  **4. Run `git init`**

```bash
git init
```

 What it does:

* Initializes a **new empty Git repository**.
* Creates a hidden folder: `.git/` → This is where Git tracks all versions.
* Doesn’t track any files yet.

---

##  **5. Configure Git (Required for Commits)**

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

 This sets your **identity** for all commits made on this machine.

---

##  **6. Check Git Status**

```bash
git status
```

You’ll see:

```
Untracked files:
  hello.txt
```

 Meaning: Git sees the file, but it’s **not being tracked** yet.

---

##  **7. Add File to Staging Area**

```bash
git add hello.txt
```

###  What is Staging Area?

* It’s a **temporary holding zone**.
* You say: “Git, prepare this file for the next commit.”
* Think of it like a **shopping cart** before checkout.

---

##  **8. Commit the File**

```bash
git commit -m "Initial commit with hello.txt"
```

 What Happens:

* Git **takes a snapshot** of the file as it is in the staging area.
* This snapshot is stored **permanently** in the `.git` history.
* Your file is now **under version control**.

---

##  Recap: Lifecycle of a File

| Stage               | Command               | Description                      |
| ------------------- | --------------------- | -------------------------------- |
| OS File             | `touch file.txt`      | File exists on disk only         |
| Untracked → Tracked | `git add file.txt`    | Moves file to staging area       |
| Committed           | `git commit -m "..."` | Stores a snapshot in Git history |

---

##  Check What’s Happening

* See log of commits:

```bash
git log
```

* See status again:

```bash
git status
```

---


Lifecycle of a File in Git (3-Step Flow)

<img width="1344" height="675" alt="image" src="https://github.com/user-attachments/assets/14c2c7b0-b55a-4671-a543-cac7a0d703f6" />


This diagram perfectly illustrates the **Lifecycle of a File in Git** — from being just a file under your Operating System to becoming a fully tracked version-controlled asset inside Git.

Let me explain each step clearly:

---

##  Lifecycle of a File in Git (3-Step Flow)

---

### STEP 1️

**File is created**

* At this point, the file is only in your folder.
* It is **under control of the Operating System only**.
* Git has no knowledge of this file yet.

 Think of it as:
“This file exists, but Git is ignoring it.”

---

### STEP 2️

**You want Git to start tracking it**

You run:

```
git add file_name
```

* This command **moves the file into the staging area**.
* Git now knows: “You want to include this file in the next commit.”

 The **Staging Area** is a temporary area where you review and prepare your changes.

---

### STEP 3️

**You finalize and record the file into Git’s history**

You run:

```
git commit -m "some message"
```

* This takes the file from the staging area
* It creates a **permanent snapshot** inside your Git repository
* The commit goes into the `.git` folder as part of the version history

 At this stage, the file is officially under **Git version control**.

---

##  Summary

| Step | State of the File | Description                            |
| ---- | ----------------- | -------------------------------------- |
| 1    | Untracked         | File created, only visible to OS       |
| 2    | Staged            | `git add` moves it to staging          |
| 3    | Committed         | `git commit` records it in Git history |

---

This diagram is a **great visual** to explain to beginners exactly **how Git takes control over a file step by step**.


