# Topic 3: Viewing Commit History with git log

## 🎯 Learning Objectives

By the end of this topic, you will understand:
- How to view your project's commit history
- Different ways to display commit information
- How to filter and search through commits
- Understanding commit hashes and references
- How commit history appears on GitHub
- Real-world applications in your codingGita projects

---

## 📚 What is Commit History?

### Definition
**Commit history** is like a **timeline** of your project showing every change made, when it was made, and who made it. It's your project's complete story from start to finish.

### Real-Life Analogy: College Yearbook 📖
Think of commit history like your college yearbook:
- **Each page** = One commit
- **Page numbers** = Commit hashes
- **Dates** = When changes were made
- **Student names** = Who made the changes
- **Photos/Content** = What was changed
- **Index** = Different ways to find information

---

## 🔍 Basic git log Commands

### 1. **Simple Log View**
```bash
# Show basic commit history
git log

# Output shows:
# commit a1b2c3d4e5f6... (commit hash)
# Author: Your Name <your.email@codinggita.edu>
# Date:   Mon Aug 19 10:30:00 2024 +0530
# 
#     Your commit message here
```

### 2. **Compact Log View**
```bash
# Show one line per commit
git log --oneline

# Output:
# a1b2c3d Add user login functionality
# b2c3d4e Fix navigation menu bug
# c3d4e5f Update README documentation
```

### 3. **Graph View (Branch Visualization)**
```bash
# Show commit history with branch structure
git log --graph --oneline --all

# Output:
# * a1b2c3d Add user login functionality
# * b2c3d4e Fix navigation menu bug
# * c3d4e5f Update README documentation
# | * d4e5f6g Work on feature branch
# | * e5f6g7h Add new feature
# |/
# * f6g7h8i Merge feature branch
```

---

## 🎨 Advanced git log Options

### 1. **Custom Formatting**
```bash
# Show specific information
git log --pretty=format:"%h - %an, %ar : %s"

# Output:
# a1b2c3d - Priya Sharma, 2 hours ago : Add user login functionality
# b2c3d4e - Priya Sharma, 1 day ago : Fix navigation menu bug
# c3d4e5f - Priya Sharma, 3 days ago : Update README documentation
```

### 2. **Filtering by Author**
```bash
# Show commits by specific person
git log --author="Priya Sharma"

# Show commits by email
git log --author="priya.sharma@codinggita.edu"
```

### 3. **Filtering by Date**
```bash
# Show commits since yesterday
git log --since="yesterday"

# Show commits in last week
git log --since="1 week ago"

# Show commits between dates
git log --since="2024-08-01" --until="2024-08-31"

# Show commits in last month
git log --since="1 month ago"
```

### 4. **Filtering by File**
```bash
# Show commits that changed specific file
git log --follow README.md

# Show commits that changed any .js file
git log -- "*.js"

# Show commits that changed files in css folder
git log -- css/
```

---

## 🔍 Understanding Commit References

### Commit Hash (SHA-1)
```bash
# Full hash (40 characters)
a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t

# Short hash (7 characters) - usually unique
a1b2c3d
```

### Relative References
```bash
# Current commit
HEAD

# Previous commit
HEAD~1    # or HEAD^
HEAD~2    # 2 commits back
HEAD~3    # 3 commits back

# Specific branch
main
feature-branch
```

### Real-Life Example: Navigation
```bash
# You're at commit a1b2c3d (current)
# Want to see what changed in last 3 commits
git log HEAD~3..HEAD

# Want to see commits between two points
git log a1b2c3d..d4e5f6g
```

---

## 🌐 GitHub Implementation

### How Commit History Appears on GitHub

#### 1. **Repository Main Page**
- **Commits:** Shows number of commits
- **Branches:** Shows active branches
- **Contributors:** Shows who has contributed

#### 2. **Commit History Page**
- **Timeline view:** Chronological list of commits
- **Commit details:** Click any commit to see changes
- **Compare view:** Compare any two commits
- **Blame view:** See who changed each line

#### 3. **Individual Commit View**
- **Commit message:** Full message with description
- **Author info:** Name, avatar, timestamp
- **Files changed:** List of modified files
- **Diff view:** Side-by-side comparison
- **Parent commits:** Links to previous commits

### GitHub-Specific Features

#### 1. **Commit Search**
```bash
# Search commits by message
git log --grep="login"

# Search commits by author
git log --author="priya"

# Search commits by date range
git log --since="2024-08-01" --until="2024-08-31"
```

#### 2. **Commit Links**
- **Commit URL:** `https://github.com/username/repo/commit/a1b2c3d`
- **Compare URL:** `https://github.com/username/repo/compare/a1b2c3d...d4e5f6g`
- **Branch comparison:** `https://github.com/username/repo/compare/main...feature`

---

## 🎯 Real-Life codingGita Examples

### Example 1: Assignment Development Timeline
```bash
# View your assignment progress
git log --oneline --since="1 week ago"

# Output shows your development journey:
# a1b2c3d Create basic calculator structure
# b2c3d4e Add addition and subtraction
# c3d4e5f Style calculator interface
# d4e5f6g Add multiplication and division
# e5f6g7h Fix decimal point bug
# f6g7h8i Add unit tests
# g7h8i9j Final documentation
```

### Example 2: Group Project Collaboration
```bash
# See who worked on what
git log --pretty=format:"%h - %an, %ar : %s"

# Output shows teamwork:
# a1b2c3d - Priya Sharma, 2 hours ago : Add user login form
# b2c3d4e - Rahul Kumar, 1 day ago : Design navigation menu
# c3d4e5f - Priya Sharma, 1 day ago : Fix form validation
# d4e5f6g - Anjali Singh, 2 days ago : Add CSS styling
# e5f6g7h - Rahul Kumar, 3 days ago : Create project structure
```

### Example 3: Bug Investigation
```bash
# Find when a bug was introduced
git log --follow --grep="bug\|fix" script.js

# Output shows bug history:
# a1b2c3d Fix calculation error in grade calculator
# b2c3d4e Add input validation to prevent errors
# c3d4e5f Fix division by zero bug
# d4e5f6g Fix decimal precision issue
```

---

## 🔧 Practical git log Commands

### 1. **Daily Work Summary**
```bash
# See what you worked on today
git log --since="today" --author="$(git config user.name)"

# See what you worked on this week
git log --since="1 week ago" --author="$(git config user.name)"
```

### 2. **Project Progress Tracking**
```bash
# See commits by feature
git log --grep="feat:"

# See bug fixes
git log --grep="fix:"

# See documentation updates
git log --grep="docs:"
```

### 3. **File History**
```bash
# See complete history of a file
git log --follow --oneline README.md

# See who changed what in a file
git blame README.md
```

---

## 📊 Useful git log Aliases

### Create Helpful Shortcuts
```bash
# Add these to your Git configuration
git config --global alias.lg "log --oneline --graph --all"
git config --global alias.lg1 "log --oneline --graph --all -1"
git config --global alias.lg5 "log --oneline --graph --all -5"
git config --global alias.lg10 "log --oneline --graph --all -10"
git config --global alias.lg20 "log --oneline --graph --all -20"
```

### Using Aliases
```bash
# Show all commits with graph
git lg

# Show last 5 commits
git lg5

# Show last 10 commits
git lg10
```

---

## ⚠️ Common Mistakes and Solutions

### Mistake 1: Too Much Information
```bash
# ❌ Bad - Overwhelming output
git log

# ✅ Good - Focused output
git log --oneline -10
```

### Mistake 2: Forgetting to Filter
```bash
# ❌ Bad - Hard to find specific commits
git log

# ✅ Good - Filter by what you need
git log --grep="login" --since="1 week ago"
```

### Mistake 3: Not Understanding Hashes
```bash
# ❌ Bad - Copying wrong hash
git show a1b2c3d  # Wrong hash

# ✅ Good - Copy exact hash from git log
git show a1b2c3d4e5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t
```

---

## 🧪 Practice Exercises

### Exercise 1: Explore Your Repository History
1. Open your codingGita project repository
2. Use `git log --oneline` to see recent commits
3. Use `git log --graph --oneline --all` to see branch structure
4. Find a specific commit and use `git show <hash>` to see details

### Exercise 2: Filter Commit History
1. Find all commits you made today
2. Find all commits that mention "fix" or "bug"
3. Find all commits that changed CSS files
4. Find commits between two specific dates

### Exercise 3: Create Useful Aliases
1. Create an alias for `git log --oneline --graph --all`
2. Create an alias for viewing last 5 commits
3. Create an alias for viewing commits by date
4. Test your new aliases

---

## 📋 Quick Reference

### Basic git log Commands
```bash
git log                    # Full commit history
git log --oneline         # One line per commit
git log --graph --all     # Show branch structure
git log -n 10             # Show last 10 commits
```

### Filtering Options
```bash
git log --author="name"   # Filter by author
git log --since="date"    # Filter by date
git log --grep="text"     # Filter by message
git log -- "file"         # Filter by file
```

### Formatting Options
```bash
git log --pretty=format:"%h - %an, %ar : %s"
git log --pretty=short    # Short format
git log --pretty=full     # Full format
git log --pretty=fuller   # Even more details
```

### Useful Aliases
```bash
git lg                    # Graph view (if configured)
git lg5                   # Last 5 commits
git lg10                  # Last 10 commits
```

---

## 🎓 Summary

**Key Takeaways:**
- `git log` shows your project's complete history
- Use filters to find specific commits quickly
- Commit hashes are unique identifiers
- GitHub provides beautiful commit history views
- Aliases make common commands faster

**Next Steps:**
- Practice using different git log options
- Create useful aliases for your workflow
- Explore commit history on GitHub
- Get ready to learn about branching and merging!

---

## 🔗 Related Topics

- **Next:** [Understanding Branching and Merging](04-branching-merging.md)
- **Previous:** [Understanding Commits and Commit Messages](02-commits-messages.md)
- **GitHub:** [Viewing Commit History](https://docs.github.com/en/repositories/viewing-activity-and-data-in-your-repository/viewing-commit-history)
