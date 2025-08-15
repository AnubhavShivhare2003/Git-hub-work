# Unit 1: Git Quick Reference and Troubleshooting

## 🚀 Git Command Cheat Sheet

### Essential Commands (Learn These First!)

| Command | What It Does | When to Use |
|---------|--------------|-------------|
| `git init` | Start a new Git project | Beginning a new project |
| `git status` | Check what's happening | Before and after every action |
| `git add .` | Stage all changes | When ready to save everything |
| `git commit -m "message"` | Save your changes | After staging files |
| `git log` | View your history | To see what you've done |

---

## 📚 Complete Command Reference

### Starting and Setting Up

**Create New Project:**
```bash
git init                    # Start Git in current folder
git clone <url>            # Copy project from internet
```

**Tell Git Who You Are:**
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@college.edu"
```

**Check Your Settings:**
```bash
git config --list          # See all settings
git config user.name       # See your name
git config user.email      # See your email
```

### Daily Workflow Commands

**Check Status:**
```bash
git status                 # See what's happening
git status --short         # Shorter version
```

**Stage Files:**
```bash
git add filename.txt       # Stage specific file
git add .                  # Stage all changes
git add *.txt              # Stage all .txt files
```

**Save Changes:**
```bash
git commit -m "Message"    # Save with message
git commit -am "Message"   # Add and commit modified files
```

**View History:**
```bash
git log                    # Full history
git log --oneline          # Compact history
git log -5                 # Last 5 commits
git show HEAD              # Show last commit details
```

### Working with Files

**See Changes:**
```bash
git diff                   # See unstaged changes
git diff --staged          # See staged changes
git diff HEAD~1            # Compare with previous commit
```

**File Management:**
```bash
git mv oldname.txt newname.txt    # Rename file
git rm filename.txt               # Remove file
git restore filename.txt          # Undo changes to file
```

**Project Structure:**
```bash
# On Windows:
dir                         # List files
tree /f                     # Show folder structure

# On macOS/Linux:
ls                          # List files
tree                        # Show folder structure
```

---

## 🔧 Troubleshooting Common Problems

### Problem 1: "Git is not recognized"

**Symptoms:**
```bash
'git' is not recognized as an internal or external command
```

**Solution:**
1. **Windows:** Install Git from https://git-scm.com/download/win
2. **macOS:** Install with Homebrew: `brew install git`
3. **Linux:** Install with package manager: `sudo apt install git`

**Verify Installation:**
```bash
git --version
```

### Problem 2: "Please tell me who you are"

**Symptoms:**
```bash
*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
```

**Solution:**
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@college.edu"
```

### Problem 3: "Nothing to commit, working tree clean"

**Symptoms:**
```bash
On branch main
nothing to commit, working tree clean
```

**What This Means:**
- All your changes are already saved
- No new files to commit
- This is actually good news!

**To Check:**
```bash
git status                 # Should show "clean"
git log --oneline          # Should show your commits
```

### Problem 4: "Changes not staged for commit"

**Symptoms:**
```bash
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
        modified:   README.md
```

**Solution:**
```bash
git add README.md          # Stage the file
git commit -m "Updated README"  # Save changes
```

### Problem 5: "Already up to date"

**Symptoms:**
```bash
Already up to date.
```

**What This Means:**
- Your local project is current
- No new changes to pull
- This is normal and good!

### Problem 6: "Permission denied"

**Symptoms:**
```bash
Permission denied (publickey).
```

**Solution:**
- This usually happens with GitHub (we'll learn this later)
- For now, focus on local Git commands
- This error won't affect your local projects

---

## 🎯 Quick Start Guide for codingGita Projects

### Step 1: Start Your Project
```bash
# Create project folder:
mkdir my-codingGita-project
cd my-codingGita-project

# Initialize Git:
git init

# Set your identity:
git config user.name "Your Name"
git config user.email "your.email@college.edu"
```

### Step 2: Create Your First File
```bash
# Create a README:
echo "# My codingGita Project" > README.md

# Check status:
git status

# Stage and commit:
git add README.md
git commit -m "Created project README"
```

### Step 3: Daily Workflow
```bash
# 1. Make changes to your files
# 2. Check what changed:
git status

# 3. Stage your changes:
git add .

# 4. Save your work:
git commit -m "Describe what you did"

# 5. View your progress:
git log --oneline
```

---

## 📝 Best Practices for First-Year Students

### 1. Commit Frequently
**Good:**
```bash
git commit -m "Added user login form"
git commit -m "Fixed button styling"
git commit -m "Updated project documentation"
```

**Bad:**
```bash
git commit -m "stuff"
git commit -m "changes"
git commit -m "fixed things"
```

### 2. Use Descriptive Messages
**Good:**
```bash
git commit -m "Added navigation menu to codingGita homepage"
git commit -m "Fixed bug where user couldn't save their progress"
git commit -m "Updated CSS to match college branding guidelines"
```

**Bad:**
```bash
git commit -m "w"
git commit -m "."
git commit -m "asdf"
```

### 3. Check Status Before Committing
**Always do this:**
```bash
git status              # See what's happening
git add .               # Stage changes
git status              # Verify what's staged
git commit -m "Message" # Save changes
```

### 4. Organize Your Projects
**Good Structure:**
```
my-project/
├── README.md           # Project description
├── css/               # Styling files
├── js/                # JavaScript files
├── images/            # Project images
└── docs/              # Documentation
```

**Bad Structure:**
```
my-project/
├── file1.txt
├── file2.txt
├── file3.txt
└── file4.txt
```

---

## 🚨 Emergency Commands (When Things Go Wrong)

### Undo Last Commit (But Keep Changes)
```bash
git reset --soft HEAD~1
```

**What This Does:**
- Removes the last commit
- Keeps your changes staged
- Like "un-submitting" your assignment but keeping your work

### Undo Last Commit (Lose Changes)
```bash
git reset --hard HEAD~1
```

**⚠️ Warning:** This permanently deletes your last commit and changes!

### Discard All Unstaged Changes
```bash
git restore .
```

**What This Does:**
- Undoes all unsaved changes
- Returns files to last committed state
- Like "reverting" your document to last saved version

### See What You're About to Lose
```bash
git status              # See what's changed
git diff                # See exact changes
```

**Always check before using destructive commands!**

---

## 📊 Understanding Git Output

### Git Status Colors
- **Red text** = Changes not staged (need `git add`)
- **Green text** = Changes staged (ready to commit)
- **No color** = Everything is saved

### Git Log Format
```bash
commit abc1234 (HEAD -> main)
Author: Your Name <your.email@college.edu>
Date:   Mon Dec 4 14:30:25 2023 +0530

    Your commit message here
```

**What Each Part Means:**
- `commit abc1234` = Unique ID for this save
- `(HEAD -> main)` = Current position in history
- `Author` = Who made the change
- `Date` = When it was saved
- `Message` = What you wrote about the change

### Git Diff Symbols
```bash
- old line that was removed
+ new line that was added
```

---

## 🎓 Study Tips for Git

### 1. Practice Daily
- Use Git for every codingGita assignment
- Commit your progress each day
- Review your learning history weekly

### 2. Start Small
- Begin with simple projects
- Practice basic commands until they're automatic
- Add advanced features gradually

### 3. Learn by Doing
- Don't just read - practice!
- Make mistakes and learn from them
- Experiment with different scenarios

### 4. Use Real Projects
- Apply Git to your actual assignments
- Track your learning journey
- Build a portfolio of your work

### 5. Ask for Help
- Use `git status` when confused
- Check `git log` to see what you've done
- Don't be afraid to start over with `git init`

---

## 🔍 Common Scenarios and Solutions

### Scenario 1: "I made changes but forgot to commit"
```bash
# Check what you have:
git status

# Stage and save:
git add .
git commit -m "Saved my work before leaving"
```

### Scenario 2: "I want to see what I changed yesterday"
```bash
# See recent commits:
git log --oneline

# See changes in specific commit:
git show <commit-id>
```

### Scenario 3: "I want to start over with this file"
```bash
# Discard changes:
git restore filename.txt

# Or restore from specific commit:
git restore --source=HEAD filename.txt
```

### Scenario 4: "I want to see my project's history"
```bash
# See all commits:
git log

# See compact history:
git log --oneline

# See history with changes:
git log -p
```

---

## 📚 What to Learn Next

### After Mastering These Basics:
1. **Working with Remote Repositories (GitHub)**
   - Upload your projects to the internet
   - Share code with classmates
   - Build a public portfolio

2. **Branching and Merging**
   - Work on different features simultaneously
   - Experiment safely without breaking working code
   - Collaborate with others

3. **Advanced Git Features**
   - Stashing changes temporarily
   - Cherry-picking specific commits
   - Rebase and interactive rebase

### Your Learning Path:
```
Week 1: Basic commands (init, add, commit, status, log)
Week 2: File management (diff, restore, mv, rm)
Week 3: Project organization and best practices
Week 4: Ready for GitHub and collaboration!
```

---

## 💡 Pro Tips for College Students

### 1. Use Git for All Your Projects
- codingGita assignments
- Personal coding projects
- Group projects
- Even non-coding assignments (track document versions)

### 2. Build a Learning Portfolio
- Every commit shows your progress
- Professors can see your work ethic
- Future employers will be impressed

### 3. Practice with Friends
- Help each other learn Git
- Share projects and collaborate
- Learn from each other's mistakes

### 4. Don't Panic
- Git is designed to be safe
- You can almost always recover from mistakes
- Start with simple projects and build confidence

### 5. Use Meaningful Commit Messages
- Future you will thank you
- Professors will appreciate your organization
- It shows professional habits

---

## 🎯 Final Checklist

**Before Moving to Next Unit, Make Sure You Can:**

✅ **Start a new Git project** with `git init`
✅ **Check project status** with `git status`
✅ **Stage files** with `git add`
✅ **Save changes** with `git commit`
✅ **View history** with `git log`
✅ **Understand the workflow** (working → staging → repository)
✅ **Use Git for a real project** (like codingGita)
✅ **Write clear commit messages**
✅ **Organize project files** logically

**If you can do all of these, you're ready for the next level!**

---

## 🚀 Ready to Continue?

**You've now mastered the fundamentals of Git!**

**What's Next:**
- Unit 2: Working with Remote Repositories (GitHub)
- Unit 3: Branching and Collaboration
- Unit 4: Advanced Git Techniques

**Remember:**
Git is like learning to drive - it seems complicated at first, but with practice, it becomes second nature. You're building skills that will help you throughout your coding career!

**Your codingGita Journey Continues:**
Every commit you make is a step forward. Keep practicing, keep learning, and keep building amazing projects! 🎉
