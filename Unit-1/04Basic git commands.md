# 🖥️ Basic Git Commands – CodingGita Hostel Guide

Welcome to **CodingGita’s Git Hostel Guide**!  
Now that you’ve installed and configured Git, it’s time to **start using it**.  
This guide covers the **basic Git commands** every beginner should master.

---

## 📋 Commands We’ll Learn
1. `git init` – Initialize a repository  
2. `git clone` – Copy a repository  
3. `git status` – Check the status of your files  
4. `git add` – Stage changes for commit  
5. `git commit` – Save changes to history  
6. `git log` – View commit history  

---

## 1️⃣ `git init` – Initialize a Repository

Creates a **new Git repository** in the current folder.

```bash
git init
```

💡 **Hostel Example:**  
You and your hostel friends want to track contributions for a **"Hostel Expense Tracker"** project.  
Run `git init` inside the project folder — now Git will start tracking changes.

---

## 2️⃣ `git clone` – Copy a Repository

Copies an **existing repository** from a remote location (like GitHub) to your computer.

```bash
git clone <repository-url>
```

💡 **Example:**  
```bash
git clone https://github.com/CodingGita/hostel-expense-tracker.git
```
You now have your own editable copy.

---

## 3️⃣ `git status` – Check Current Changes

Tells you:
- Which files are **untracked** (new)  
- Which files are **modified**  
- Which files are **staged** for commit  

```bash
git status
```

💡 **Example:**  
After editing `canteen-menu.txt`, run `git status` to see if Git has detected the changes.

---

## 4️⃣ `git add` – Stage Changes

Moves files from the **Working Directory** to the **Staging Area**.

```bash
git add <file-name>
```
Or, add all files:
```bash
git add .
```

💡 **Example:**  
```bash
git add canteen-menu.txt
```
This means you’re ready to commit that file’s changes.

---

## 5️⃣ `git commit` – Save Changes

Takes everything in the staging area and **saves it to the repository history**.

```bash
git commit -m "Your commit message"
```

💡 **Example:**  
```bash
git commit -m "Updated canteen menu with weekend specials"
```
📌 Commit messages should be short but descriptive.

---

## 6️⃣ `git log` – View Commit History

Displays the list of all commits with **author, date, and message**.

```bash
git log
```
Press `q` to quit the log.

💡 **Example Output:**
```
commit 7f4a1e2a9f8b6a3dcd1234f...
Author: Aman Sharma - CodingGita <aman.codinggita@gmail.com>
Date:   Mon Aug 12 14:23:16 2025 +0530

    Updated canteen menu with weekend specials
```

---

## 🗂 Git Workflow Recap

Git has **three areas**:
1. **Working Directory** – Where you make changes.
2. **Staging Area** – Where you prepare changes (`git add`).
3. **Repository** – Where committed changes live permanently.

📌 **Hostel Example:**  
- You edit `milk-expenses.txt` → **Working Directory**  
- You run `git add milk-expenses.txt` → **Staging Area**  
- You run `git commit -m "Added weekly milk bill"` → **Repository**

---

## 📺 YouTube Tutorials for Basic Git Commands

1. **[Git & GitHub Crash Course – Traversy Media](https://www.youtube.com/watch?v=SWYqp7iY_Tc)**  
2. **[Git Commands Explained – freeCodeCamp](https://www.youtube.com/watch?v=Uszj_k0DGsg)**  
3. **[Git Tutorial for Beginners – CodeWithHarry (Hindi)](https://www.youtube.com/watch?v=gwWKnnCMQ5c)**  

---

## 📊 Summary Table

| Command      | Purpose                                    | Example |
|--------------|--------------------------------------------|---------|
| `git init`   | Start a new Git repo                       | `git init` |
| `git clone`  | Copy an existing repo                      | `git clone https://github.com/CodingGita/repo.git` |
| `git status` | Show status of files                       | `git status` |
| `git add`    | Stage changes                              | `git add file.txt` |
| `git commit` | Save changes to history                    | `git commit -m "message"` |
| `git log`    | View commit history                        | `git log` |

---

✅ **Now you know the core Git commands.**  
Next, we’ll explore **branching and merging** so you can work on multiple features without conflicts.
