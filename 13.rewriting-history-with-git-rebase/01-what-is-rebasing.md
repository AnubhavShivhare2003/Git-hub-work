# What is Rebasing and How it Differs from Merging

## 🎯 Learning Objectives
By the end of this lesson, you will understand:
- What git rebase is and why it's useful
- How rebasing differs from merging
- When to use rebase vs merge
- The visual differences between the two approaches

## 📚 What is Git Rebase?

**Git rebase** is a powerful command that allows you to "replay" your commits on top of another branch. Think of it like moving your work to a different starting point.

### Simple Analogy 🏗️
Imagine you're building a tower of blocks:
- **Merging**: You take your tower and place it next to another tower, creating a fork
- **Rebasing**: You take your blocks and rebuild your tower on top of the other tower

## 🔄 Rebasing vs Merging: The Key Differences

### Visual Comparison

#### Before Any Operation
```
main:     A---B---C
feature:      D---E---F
```

#### After Merging
```
main:     A---B---C---G (merge commit)
feature:      D---E---F
```

#### After Rebasing
```
main:     A---B---C
feature:              D'---E'---F'
```

### Key Differences Table

| Aspect | Merging | Rebasing |
|--------|---------|----------|
| **History** | Preserves original branch history | Rewrites history (creates new commits) |
| **Commit Graph** | Creates merge commits | Creates linear history |
| **Safety** | Safe (non-destructive) | Rewrites history (can be risky) |
| **Use Case** | Public branches, team collaboration | Personal branches, clean history |
| **Result** | Branching structure preserved | Linear, clean history |

## 🎯 When to Use Each Approach

### Use Merging When:
- ✅ Working on a shared/public branch
- ✅ You want to preserve the exact history
- ✅ Multiple people are working on the same branch
- ✅ You're unsure about the changes

### Use Rebasing When:
- ✅ Working on your personal feature branch
- ✅ You want a clean, linear history
- ✅ Preparing to merge into main branch
- ✅ You understand the risks involved

## 🔍 Understanding the Process

### What Happens During a Rebase?

1. **Git identifies the common ancestor** (the point where branches diverged)
2. **Git temporarily removes your commits** from the feature branch
3. **Git applies the latest changes** from the target branch
4. **Git replays your commits** one by one on top of the new base
5. **Git creates new commit hashes** for your replayed commits

### Important Note ⚠️
When you rebase, Git creates **new commits** with different hashes. Your original commits are replaced, not just moved.

## 📝 Basic Syntax and Command Explanation

### Command Structure
```bash
git rebase <target-branch>
```

### Detailed Command Breakdown

#### `git rebase`
- **Purpose**: The main command for rebasing operations
- **What it does**: Tells Git to replay commits from your current branch onto a different base
- **When to use**: When you want to move your commits to a new starting point

#### `<target-branch>`
- **Purpose**: Specifies which branch to rebase onto
- **What it does**: This is the branch that will become the new base for your commits
- **Examples**: `main`, `develop`, `master`, or any other branch name

### Complete Command Examples

#### Example 1: Basic Rebase
```bash
# You are currently on feature-branch
git rebase main
```
**What happens**:
1. Git finds the common ancestor between `feature-branch` and `main`
2. Git temporarily removes your commits from `feature-branch`
3. Git applies the latest changes from `main`
4. Git replays your commits one by one on top of the new base
5. Git creates new commits with new hashes

#### Example 2: Rebase with Specific Branch
```bash
# Switch to your feature branch first
git checkout feature-branch

# Then rebase onto main
git rebase main
```

#### Example 3: Rebase onto Different Branch
```bash
# Rebase feature-branch onto develop instead of main
git checkout feature-branch
git rebase develop
```

### Command Options and Flags

#### `--continue`
```bash
git rebase --continue
```
- **Purpose**: Continue a rebase after resolving conflicts
- **When to use**: After you've manually resolved merge conflicts
- **What it does**: Applies the next commit in the rebase sequence

#### `--abort`
```bash
git rebase --abort
```
- **Purpose**: Cancel a rebase and return to original state
- **When to use**: When you want to stop the rebase and go back to how things were
- **What it does**: Restores your branch to the state before rebase started

#### `--skip`
```bash
git rebase --skip
```
- **Purpose**: Skip the current commit during rebase
- **When to use**: When a commit causes unresolvable conflicts or is no longer needed
- **What it does**: Removes the current commit from the rebase sequence

### Interactive Rebase Syntax
```bash
git rebase -i <commit-hash>
git rebase -i HEAD~n
```

#### `-i` Flag Explanation
- **Purpose**: Starts interactive rebase mode
- **What it does**: Opens an editor where you can modify commits
- **Options available**: pick, reword, edit, squash, drop, fixup

#### `<commit-hash>` Explanation
- **Purpose**: Specifies where to start the interactive rebase
- **What it does**: Tells Git which commit to begin editing from
- **Examples**: `abc123`, `HEAD~3`, `main`

### Command Execution Flow

#### Step-by-Step Process
1. **Check current branch**: `git branch` or `git status`
2. **Ensure clean working directory**: `git status`
3. **Execute rebase**: `git rebase <target-branch>`
4. **Handle conflicts** (if any): Edit files, then `git add`
5. **Continue rebase**: `git rebase --continue`
6. **Verify result**: `git log --oneline --graph`

## 🎨 Visual Example

Let's say you have this situation:

```
main:     A---B---C---D
feature:      E---F---G
```

After running `git rebase main` from the feature branch:

```
main:     A---B---C---D
feature:              E'---F'---G'
```

Notice how commits E, F, and G become E', F', and G' (new commits with new hashes).

## ⚡ Quick Summary

- **Rebasing** = Moving your commits to a new starting point
- **Merging** = Combining two branches while preserving both histories
- **Rebase** creates linear history, **merge** preserves branching
- **Rebase** rewrites history, **merge** is non-destructive
- Choose **rebase** for clean history, **merge** for safety

## 🚨 Important Warnings

1. **Never rebase public branches** that others are working on
2. **Rebasing rewrites history** - original commits are lost
3. **Always backup your work** before rebasing
4. **Communicate with your team** about rebasing practices

## 🎯 Key Takeaways

- Rebase creates a cleaner, linear project history
- Merge preserves the exact branching structure
- Both approaches have their place in Git workflows
- Understanding when to use each is crucial for effective collaboration

---

## 🎯 Detailed Exercises

### Exercise 1: Understanding the Difference Between Merge and Rebase

#### Objective
Compare the visual and practical differences between merging and rebasing by performing both operations on the same scenario.

#### Setup Instructions
```bash
# Create a new directory for practice
mkdir rebase-vs-merge-practice
cd rebase-vs-merge-practice

# Initialize a new Git repository
git init

# Create initial files
echo "# My Project" > README.md
echo "console.log('Hello World');" > app.js
git add .
git commit -m "Initial commit"
```

#### Step 1: Create the Base Scenario
```bash
# Add content to main branch
echo "// Main branch feature" >> app.js
git add app.js
git commit -m "Add main branch feature"

# Create and switch to feature branch
git checkout -b feature-branch
echo "// Feature branch work" >> app.js
git add app.js
git commit -m "Add feature branch work"

# Switch back to main and add more content
git checkout main
echo "// Another main feature" >> app.js
git add app.js
git commit -m "Add another main feature"
```

**Command Explanation**:
- `git checkout -b feature-branch`: Creates a new branch called "feature-branch" and switches to it
- `git add app.js`: Stages the modified app.js file for commit
- `git commit -m "message"`: Creates a commit with the specified message

#### Step 2: Create Backup for Merge Comparison
```bash
# Create a backup of feature-branch for merge
git checkout feature-branch
git checkout -b feature-merge-backup
```

**Command Explanation**:
- `git checkout feature-branch`: Switches to the feature-branch
- `git checkout -b feature-merge-backup`: Creates a new branch called "feature-merge-backup" from the current position

#### Step 3: Perform Merge Operation
```bash
# Switch to feature-branch
git checkout feature-branch

# Merge main into feature-branch
git merge main
```

**Command Explanation**:
- `git merge main`: Merges the main branch into the current branch (feature-branch)
- This creates a merge commit that combines both histories

#### Step 4: Observe Merge Result
```bash
# View the commit history
git log --oneline --graph
```

**Expected Output**:
```
* abc123 (HEAD -> feature-branch) Merge branch 'main' into feature-branch
|\
| * def456 Add another main feature
* | ghi789 Add feature branch work
|/
* jkl012 Add main branch feature
* mno345 Initial commit
```

**Command Explanation**:
- `git log --oneline --graph`: Shows commit history in a compact format with a visual graph
- The `|\` and `|/` symbols show the branching structure

#### Step 5: Reset and Try Rebase
```bash
# Switch to the backup branch
git checkout feature-merge-backup

# Create a new branch for rebase
git checkout -b feature-rebase

# Perform rebase onto main
git rebase main
```

**Command Explanation**:
- `git checkout feature-merge-backup`: Switches to the backup branch
- `git checkout -b feature-rebase`: Creates a new branch for rebase practice
- `git rebase main`: Rebases the current branch onto main

#### Step 6: Observe Rebase Result
```bash
# View the commit history after rebase
git log --oneline --graph
```

**Expected Output**:
```
* pqr789 (HEAD -> feature-rebase) Add feature branch work
* def456 Add another main feature
* jkl012 Add main branch feature
* mno345 Initial commit
```

**Key Differences Observed**:
- **Merge**: Creates a merge commit and preserves branching structure
- **Rebase**: Creates linear history without merge commits

#### Questions to Answer
1. What is the difference in the commit graph between merge and rebase?
2. Which approach creates a cleaner, more linear history?
3. When would you prefer each approach in a real project?

### Exercise 2: Basic Rebase Command Practice

#### Objective
Practice using basic rebase commands with different scenarios.

#### Setup Instructions
```bash
# Create a new practice directory
mkdir basic-rebase-practice
cd basic-rebase-practice

# Initialize Git repository
git init

# Create initial content
echo "# Basic Rebase Practice" > README.md
echo "function hello() { console.log('Hello'); }" > script.js
git add .
git commit -m "Initial project setup"
```

#### Step 1: Create Multiple Branches
```bash
# Create main branch content
echo "function goodbye() { console.log('Goodbye'); }" >> script.js
git add script.js
git commit -m "Add goodbye function"

# Create feature branch
git checkout -b feature-branch
echo "function welcome() { console.log('Welcome'); }" >> script.js
git add script.js
git commit -m "Add welcome function"

# Add more content to main
git checkout main
echo "function thanks() { console.log('Thanks'); }" >> script.js
git add script.js
git commit -m "Add thanks function"
```

**Command Explanation**:
- `>>`: Appends content to a file (vs `>` which overwrites)
- Each `git add` and `git commit` sequence creates a new commit

#### Step 2: Practice Basic Rebase
```bash
# Switch to feature branch
git checkout feature-branch

# Check current status
git status
```

**Command Explanation**:
- `git status`: Shows the current state of your working directory and staging area

```bash
# Perform rebase onto main
git rebase main
```

**Command Explanation**:
- `git rebase main`: Replays commits from feature-branch on top of main
- This should be a fast-forward rebase since there are no conflicts

#### Step 3: Verify Rebase Result
```bash
# Check the commit history
git log --oneline --graph

# Check the current branch
git branch

# Check the file content
cat script.js
```

**Command Explanation**:
- `git log --oneline --graph`: Shows commit history
- `git branch`: Lists all branches and shows current branch with *
- `cat script.js`: Displays the content of script.js file

#### Step 4: Practice Rebase with Different Target
```bash
# Create another branch
git checkout main
git checkout -b another-feature

# Add content to this branch
echo "function farewell() { console.log('Farewell'); }" >> script.js
git add script.js
git commit -m "Add farewell function"

# Rebase onto feature-branch
git rebase feature-branch
```

**Command Explanation**:
- `git checkout main`: Switches to main branch
- `git checkout -b another-feature`: Creates and switches to new branch
- `git rebase feature-branch`: Rebases current branch onto feature-branch

#### Step 5: Handle Potential Conflicts
```bash
# Check if there are conflicts
git status

# If conflicts exist, resolve them
# Edit script.js to remove conflict markers
# Then continue the rebase
git add script.js
git rebase --continue
```

**Command Explanation**:
- `git status`: Shows if there are conflicts to resolve
- `git add script.js`: Stages the resolved file
- `git rebase --continue`: Continues the rebase after resolving conflicts

#### Questions to Answer
1. What happened to the commit hashes after rebasing?
2. How did the file content change after rebasing?
3. What would you do if conflicts occurred during rebase?

### Exercise 3: Understanding Rebase Safety

#### Objective
Learn about rebase safety by practicing with backups and understanding the risks.

#### Setup Instructions
```bash
# Create a new practice directory
mkdir rebase-safety-practice
cd rebase-safety-practice

# Initialize Git repository
git init

# Create initial content
echo "# Rebase Safety Practice" > README.md
echo "let data = [1, 2, 3];" > data.js
git add .
git commit -m "Initial commit with data array"
```

#### Step 1: Create Important Work
```bash
# Add significant work to main
echo "function processData(arr) { return arr.map(x => x * 2); }" >> data.js
git add data.js
git commit -m "Add data processing function"

# Create feature branch with important work
git checkout -b important-feature
echo "function validateData(arr) { return arr.every(x => typeof x === 'number'); }" >> data.js
git add data.js
git commit -m "Add data validation function"

echo "function sortData(arr) { return arr.sort((a, b) => a - b); }" >> data.js
git add data.js
git commit -m "Add data sorting function"
```

**Command Explanation**:
- Each commit represents important work that you don't want to lose
- The feature branch contains valuable functionality

#### Step 2: Create Safety Backup
```bash
# Create backup before rebasing
git branch backup-important-feature
```

**Command Explanation**:
- `git branch backup-important-feature`: Creates a backup branch pointing to the same commit
- This ensures you can always return to the original state

#### Step 3: Practice Safe Rebase
```bash
# Check current status
git status
git log --oneline

# Perform rebase with backup in place
git rebase main
```

**Command Explanation**:
- `git status`: Ensures working directory is clean
- `git log --oneline`: Shows current commit history
- `git rebase main`: Performs the rebase operation

#### Step 4: Verify Safety Measures
```bash
# Check that backup still exists
git branch

# Compare original and rebased versions
git log --oneline backup-important-feature
git log --oneline
```

**Command Explanation**:
- `git branch`: Lists all branches including the backup
- `git log --oneline backup-important-feature`: Shows the original commit history
- `git log --oneline`: Shows the current (rebased) commit history

#### Step 5: Practice Recovery
```bash
# Simulate a problem by creating a bad rebase
echo "// This might cause issues" >> data.js
git add data.js
git commit -m "Add potentially problematic code"

# If you need to recover, switch to backup
git checkout backup-important-feature
git checkout -b recovered-feature
```

**Command Explanation**:
- `git checkout backup-important-feature`: Switches to the backup branch
- `git checkout -b recovered-feature`: Creates a new branch from the backup

#### Questions to Answer
1. Why is it important to create backups before rebasing?
2. How can you verify that your backup is intact?
3. What would you do if a rebase operation went wrong?

### Exercise 4: Interactive Rebase Introduction

#### Objective
Get familiar with interactive rebase for editing commit history.

#### Setup Instructions
```bash
# Create a new practice directory
mkdir interactive-rebase-practice
cd interactive-rebase-practice

# Initialize Git repository
git init

# Create initial content
echo "# Interactive Rebase Practice" > README.md
echo "let counter = 0;" > counter.js
git add .
git commit -m "Initial counter setup"
```

#### Step 1: Create Multiple Commits
```bash
# Add increment function
echo "function increment() { counter++; }" >> counter.js
git add counter.js
git commit -m "Add increment function"

# Add decrement function
echo "function decrement() { counter--; }" >> counter.js
git add counter.js
git commit -m "Add decrement function"

# Add reset function
echo "function reset() { counter = 0; }" >> counter.js
git add counter.js
git commit -m "Add reset function"

# Add display function
echo "function display() { console.log(counter); }" >> counter.js
git add counter.js
git commit -m "Add display function"
```

**Command Explanation**:
- Each commit adds a new function to the counter.js file
- This creates a series of commits that we can later modify

#### Step 2: Start Interactive Rebase
```bash
# Start interactive rebase for last 4 commits
git rebase -i HEAD~4
```

**Command Explanation**:
- `git rebase -i HEAD~4`: Starts interactive rebase for the last 4 commits
- `-i`: Interactive mode
- `HEAD~4`: Last 4 commits from current HEAD

#### Step 3: Modify Commit History
In the editor that opens, you'll see something like:
```
pick abc123 Add increment function
pick def456 Add decrement function
pick ghi789 Add reset function
pick jkl012 Add display function
```

**Modify the file to**:
```
pick abc123 Add increment function
squash def456 Add decrement function
pick ghi789 Add reset function
squash jkl012 Add display function
```

**Command Explanation**:
- `pick`: Use the commit as-is
- `squash`: Combine this commit with the previous one
- This will combine the increment/decrement functions and reset/display functions

#### Step 4: Complete the Rebase
```bash
# Save and close the editor
# Git will open another editor for commit messages
# Edit the commit messages as needed
# Save and close
```

**Command Explanation**:
- After saving the rebase plan, Git opens an editor for commit messages
- You can edit the messages for the squashed commits

#### Step 5: Verify the Result
```bash
# Check the commit history
git log --oneline

# Check the file content
cat counter.js
```

**Command Explanation**:
- `git log --oneline`: Shows the modified commit history
- `cat counter.js`: Shows the final file content

#### Questions to Answer
1. How did the commit history change after interactive rebase?
2. What happened to the commit messages?
3. When would you use interactive rebase in a real project?

---

**Next**: Learn about moving commits from one branch to another in detail!
