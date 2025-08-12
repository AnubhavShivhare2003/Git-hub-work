# 📜 Viewing Commit History with `git log` – CodingGita Guide

## 📌 Why View Commit History?

Commit history is like a **diary of your project's journey**.  
It tells you:
- What changes were made  
- When they were made  
- Who made them  
- Why they were made (via commit messages)

💡 **Hostel Life Example:**  
Think of the commit history as the **notice board in your hostel**.  
Every update (commit) is pinned there — date, author, and details —  
so you know **who changed the dinner menu**, **who fixed the broken fan**, and **when it happened**.

---

## ⚙️ Basic Command – `git log`

```bash
git log
```

### Example output:

```
commit a3f5d21b6f8a8e9d1e3a9f5c1a9b7a6f8e9c0d1a
Author: Aman Sharma - CodingGita <aman.codinggita@gmail.com>
Date:   Mon Aug 5 10:30:21 2025 +0530

    Added hostel lunch menu for Tuesday
```

---

## 🎯 Useful `git log` Options

### 1️⃣ Shorter Log — One Line per Commit
```bash
git log --oneline
```

**Example:**
```
a3f5d21 Added lunch menu for CodingGita hostel
9b2c7ef Fixed spelling in Paneer Butter Masala
c1d9e34 Added Monday breakfast menu
```

### 2️⃣ Show Last N Commits
```bash
git log -n 5
```
Shows the last 5 commits only.

### 3️⃣ Filter by Author
```bash
git log --author="Aman Sharma"
```
Shows commits made by a specific person.

### 4️⃣ Search for a Word in Commit Messages
```bash
git log --grep="menu"
```
Finds all commits that have the word "menu" in their message.

### 5️⃣ Show Changes Made in Each Commit
```bash
git log -p
```
Displays the actual code changes (diff) with each commit.

### 6️⃣ Pretty / Graph View (visualize branches)
```bash
git log --oneline --graph --decorate --all
```
Shows a compact visual graph of branches and commits.

---

## 💡 Handy Examples (hostel scenarios)

**Find who edited the dinner menu last week:**
```bash
git log --since="7 days ago" --grep="dinner menu"
```

**See only merges (useful after group work):**
```bash
git log --merges --oneline
```

**Show commit messages and names only:**
```bash
git log --pretty=format:"%h - %an: %s"
```

---

## 🖼 Quick Workflow Tip

- Make small, logical commits (one idea per commit).
- Use `git log --oneline` to get a quick overview.
- Use `git log -p` when you need to inspect exact changes.

---

## 📺 Recommended Videos (focused on git log / viewing history)

- **[Git Log made easy!](https://www.youtube.com/watch?v=-3c77Y7KpRo)** — Practical walkthrough of git log options
- **[Git Log Fully Explained](https://www.youtube.com/watch?v=UZN7tPC4dHk)** — Deep dive into formatting and flags
- **[Using git log --oneline and useful variations](https://www.youtube.com/watch?v=DnYAVzHpquI)** — Short practical examples

---

## 📝 Summary

- **`git log`** is your project diary — use it to trace changes, authors, and reasons.
- Use short (`--oneline`) and graph (`--graph`) views for quick understanding.
- Filter by author, date, or keyword to find exactly what you need.
- Watching a focused git log video helps make these flags click faster.

---

## 🚀 Next Steps

If you want, I'll prepare **Topic 4: Understanding Branching & Merging** in the same polished README style (with hostel examples and tutorial links).

---

*This guide is part of the CodingGita Hostel Project - helping developers master Git fundamentals through real-world examples.*
