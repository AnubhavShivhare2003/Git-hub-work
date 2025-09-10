# Moving Commits from One Branch to Another

## 🎯 Learning Objectives
By the end of this lesson, you will understand:
- How to move commits between branches using rebase
- Different scenarios for moving commits
- Step-by-step process of moving commits
- Best practices for commit relocation

## 🚀 Why Move Commits Between Branches?

Sometimes you realize you've been working on the wrong branch, or you want to reorganize your work. Git rebase allows you to move commits from one branch to another seamlessly.

### Common Scenarios:
- 🔄 Accidentally committed to the wrong branch
- 📦 Want to reorganize your feature branches
- 🧹 Clean up your commit history before sharing
- 🔀 Move work from one feature to another

## 📋 Step-by-Step Process

### Scenario 1: Moving Commits to a Different Branch

Let's say you have this situation:
```
main:     A---B---C
feature1:     D---E---F
feature2:         G---H
```

You want to move commits G and H from `feature2` to `feature1`.

#### Step 1: Identify the Commits to Move
```bash
# See the commit history
git log --oneline --graph --all
```

#### Step 2: Create a New Branch from the Target Location
```bash
# Switch to feature1 branch
git checkout feature1

# Create a new branch from current position
git checkout -b feature1-updated
```

#### Step 3: Cherry-pick the Commits
```bash
# Cherry-pick commits G and H from feature2
git cherry-pick <commit-G-hash>
git cherry-pick <commit-H-hash>
```

#### Step 4: Update the Original Branch
```bash
# Switch back to feature1
git checkout feature1

# Reset to the new position
git reset --hard feature1-updated
```

### Scenario 2: Moving All Commits from One Branch to Another

#### Using Interactive Rebase

```bash
# Switch to the branch you want to move commits FROM
git checkout source-branch

# Start interactive rebase
git rebase -i main

# In the editor, you can:
# - Reorder commits
# - Edit commit messages
# - Drop unwanted commits
# - Squash multiple commits
```

## 🛠️ Practical Commands

### Moving Specific Commits - Detailed Explanation

#### Step 1: Find the Commit Hash
```bash
git log --oneline
```
**Command Explanation**:
- `git log --oneline`: Shows commit history in compact format
- Each line shows: `<commit-hash> <commit-message>`
- Example output:
  ```
  abc123 Add new feature
  def456 Fix bug in authentication
  ghi789 Update documentation
  ```

#### Step 2: Switch to Target Branch
```bash
git checkout target-branch
```
**Command Explanation**:
- `git checkout target-branch`: Switches to the branch where you want to move the commit
- This is the destination branch for your commit
- Make sure this branch exists or create it first with `git checkout -b target-branch`

#### Step 3: Cherry-pick the Commit
```bash
git cherry-pick <commit-hash>
```
**Command Explanation**:
- `git cherry-pick`: Copies a specific commit to the current branch
- `<commit-hash>`: The hash of the commit you want to move (e.g., `abc123`)
- This creates a new commit with the same changes but a new hash
- Example: `git cherry-pick abc123`

#### Step 4: Remove Commit from Original Branch
```bash
git checkout original-branch
git rebase -i <commit-before-the-one-to-move>
```
**Command Explanation**:
- `git checkout original-branch`: Switches back to the branch where the commit originally was
- `git rebase -i <commit-before-the-one-to-move>`: Starts interactive rebase from the commit before the one you moved
- In the editor that opens, change `pick` to `drop` for the commit you moved
- Example: If you moved commit `abc123`, find it in the list and change `pick abc123` to `drop abc123`

### Moving Multiple Commits - Detailed Explanation

#### Cherry-pick a Range of Commits
```bash
git cherry-pick <start-commit>^..<end-commit>
```

**Command Explanation**:
- `git cherry-pick`: Copies commits to the current branch
- `<start-commit>^`: The commit before the first commit you want to move (the `^` means "parent of")
- `..`: Range operator indicating "from start to end"
- `<end-commit>`: The last commit you want to move
- This will copy all commits from start to end (inclusive)

#### Example: Move Multiple Commits
```bash
# Example: Move commits from abc123 to def456
git cherry-pick abc123^..def456
```

**Command Explanation**:
- `abc123^`: The commit before abc123 (parent of abc123)
- `..def456`: All commits from abc123 up to and including def456
- This will copy commits abc123, ghi789, and def456 (assuming they're in sequence)

#### Alternative: Cherry-pick Individual Commits
```bash
# Cherry-pick commits one by one
git cherry-pick abc123
git cherry-pick ghi789
git cherry-pick def456
```

**Command Explanation**:
- This approach gives you more control over which commits to move
- You can skip commits or reorder them
- Each `git cherry-pick` creates a new commit on the current branch

## 🎨 Visual Example

### Before Moving Commits
```
main:     A---B---C
wrong:        D---E---F
correct:      G---H
```

### After Moving Commits D, E, F to correct branch
```
main:     A---B---C
wrong:        
correct:      G---H---D'---E'---F'
```

## 🔧 Advanced Techniques

### Using Rebase with Upstream

```bash
# Move commits from current branch to another branch
git rebase --onto <target-branch> <upstream-branch>

# Example: Move commits from feature to main
git rebase --onto main feature~3 feature
```

### Interactive Rebase for Complex Moves

```bash
# Start interactive rebase
git rebase -i HEAD~5

# In the editor, you'll see:
pick abc123 First commit
pick def456 Second commit
pick ghi789 Third commit
pick jkl012 Fourth commit
pick mno345 Fifth commit

# You can:
# - Reorder lines to change commit order
# - Change 'pick' to 'edit' to modify commits
# - Change 'pick' to 'squash' to combine commits
# - Change 'pick' to 'drop' to remove commits
```

## ⚠️ Important Considerations

### Before Moving Commits:

1. **Backup your work**
   ```bash
   git branch backup-branch
   ```

2. **Check if commits are already pushed**
   ```bash
   git log --oneline origin/branch-name
   ```

3. **Communicate with team members** if working on shared branches

### After Moving Commits:

1. **Verify the move was successful**
   ```bash
   git log --oneline --graph
   ```

2. **Test your changes** to ensure nothing broke

3. **Update remote branches** if needed
   ```bash
   git push --force-with-lease origin branch-name
   ```

## 🎯 Best Practices

### ✅ Do:
- Always backup before major operations
- Use `--force-with-lease` instead of `--force` when pushing
- Test your changes after moving commits
- Use descriptive commit messages
- Keep commits small and focused

### ❌ Don't:
- Move commits that others are already using
- Force push to shared branches without coordination
- Move commits without understanding the impact
- Forget to test after moving commits

## 🔍 Troubleshooting Common Issues

### Issue: "Commit already exists"
**Solution**: The commit might already be in the target branch
```bash
# Check if commit exists
git log --oneline --grep="commit message"
```

### Issue: "Cannot cherry-pick"
**Solution**: Resolve conflicts manually
```bash
# After cherry-pick fails
git status
# Edit conflicted files
git add .
git cherry-pick --continue
```

### Issue: "Branch is behind"
**Solution**: Update your branch first
```bash
git pull origin main
# Then retry your operation
```

## 📝 Quick Reference Commands

```bash
# Move single commit
git cherry-pick <commit-hash>

# Move range of commits
git cherry-pick <start>^..<end>

# Interactive rebase
git rebase -i HEAD~n

# Rebase onto different branch
git rebase --onto <target> <upstream> <branch>

# Check commit history
git log --oneline --graph --all
```

## 🎯 Key Takeaways

- Moving commits between branches is possible but requires care
- Cherry-pick is great for moving individual commits
- Interactive rebase is powerful for complex reorganizations
- Always backup and test after moving commits
- Communication with team members is crucial

---

## 🎯 Detailed Exercises

### Exercise 1: Moving Single Commits Between Branches

#### Objective
Learn how to move individual commits from one branch to another using cherry-pick.

#### Setup Instructions
```bash
# Create a new practice directory
mkdir commit-moving-practice
cd commit-moving-practice

# Initialize Git repository
git init

# Create initial content
echo "# Commit Moving Practice" > README.md
echo "let users = [];" > users.js
git add .
git commit -m "Initial project setup"
```

#### Step 1: Create Multiple Branches with Commits
```bash
# Create frontend branch
git checkout -b frontend
echo "function addUser(name) { users.push(name); }" >> users.js
git add users.js
git commit -m "Add user addition function"

echo "function removeUser(name) { users = users.filter(u => u !== name); }" >> users.js
git add users.js
git commit -m "Add user removal function"

# Create backend branch
git checkout main
git checkout -b backend
echo "function validateUser(name) { return name.length > 0; }" >> users.js
git add users.js
git commit -m "Add user validation function"

echo "function getUserCount() { return users.length; }" >> users.js
git add users.js
git commit -m "Add user count function"
```

**Command Explanation**:
- `git checkout -b frontend`: Creates and switches to a new branch called "frontend"
- `>>`: Appends content to the file (vs `>` which overwrites)
- Each `git add` and `git commit` sequence creates a new commit with specific functionality

#### Step 2: Identify Commits to Move
```bash
# Check commits on frontend branch
git checkout frontend
git log --oneline
```

**Expected Output**:
```
def456 Add user removal function
abc123 Add user addition function
mno345 Initial project setup
```

**Command Explanation**:
- `git log --oneline`: Shows commit history in compact format
- Each line shows: `<commit-hash> <commit-message>`
- Note the commit hashes (abc123, def456) for later use

#### Step 3: Move Commit to Backend Branch
```bash
# Switch to backend branch
git checkout backend

# Cherry-pick the user addition function
git cherry-pick abc123
```

**Command Explanation**:
- `git checkout backend`: Switches to the backend branch
- `git cherry-pick abc123`: Copies commit abc123 to the current branch
- This creates a new commit with the same changes but a new hash

#### Step 4: Verify the Move
```bash
# Check the commit history on backend branch
git log --oneline

# Check the file content
cat users.js
```

**Expected Output**:
```
ghi789 Add user addition function  # New commit hash
jkl012 Add user count function
mno345 Add user validation function
pqr456 Initial project setup
```

**Command Explanation**:
- `git log --oneline`: Shows the updated commit history
- `cat users.js`: Displays the file content to verify the function was added
- Notice the new commit hash (ghi789) - this is different from the original (abc123)

#### Step 5: Remove Commit from Original Branch
```bash
# Switch back to frontend branch
git checkout frontend

# Start interactive rebase to remove the moved commit
git rebase -i HEAD~2
```

**Command Explanation**:
- `git checkout frontend`: Switches back to the frontend branch
- `git rebase -i HEAD~2`: Starts interactive rebase for the last 2 commits
- `HEAD~2`: Refers to the commit that is 2 commits before the current HEAD

#### Step 6: Edit the Rebase Plan
In the editor that opens, you'll see:
```
pick abc123 Add user addition function
pick def456 Add user removal function
```

**Modify it to**:
```
drop abc123 Add user addition function
pick def456 Add user removal function
```

**Command Explanation**:
- `drop`: Removes this commit from the history
- `pick`: Keeps this commit as-is
- This will remove the commit we moved to the backend branch

#### Step 7: Complete the Rebase
```bash
# Save and close the editor
# The rebase will complete automatically
```

#### Step 8: Verify Final State
```bash
# Check frontend branch history
git log --oneline

# Check backend branch history
git checkout backend
git log --oneline
```

**Questions to Answer**:
1. What happened to the commit hash when you cherry-picked it?
2. How did the file content change on both branches?
3. Why is it important to remove the commit from the original branch?

### Exercise 2: Moving Multiple Commits

#### Objective
Practice moving a range of commits from one branch to another.

#### Setup Instructions
```bash
# Create a new practice directory
mkdir multiple-commits-practice
cd multiple-commits-practice

# Initialize Git repository
git init

# Create initial content
echo "# Multiple Commits Practice" > README.md
echo "let data = [];" > data.js
git add .
git commit -m "Initial data structure"
```

#### Step 1: Create Feature Branch with Multiple Commits
```bash
# Create feature branch
git checkout -b feature-branch

# Add multiple related commits
echo "function addData(item) { data.push(item); }" >> data.js
git add data.js
git commit -m "Add data insertion function"

echo "function removeData(item) { data = data.filter(d => d !== item); }" >> data.js
git add data.js
git commit -m "Add data removal function"

echo "function clearData() { data = []; }" >> data.js
git add data.js
git commit -m "Add data clearing function"

echo "function getDataCount() { return data.length; }" >> data.js
git add data.js
git commit -m "Add data count function"
```

**Command Explanation**:
- Each commit adds a related function to the data.js file
- These commits form a logical group that could be moved together
- The functions are related to data manipulation

#### Step 2: Create Target Branch
```bash
# Switch to main and create target branch
git checkout main
git checkout -b data-operations
```

**Command Explanation**:
- `git checkout main`: Switches to the main branch
- `git checkout -b data-operations`: Creates a new branch called "data-operations"

#### Step 3: Identify Commit Range
```bash
# Switch back to feature branch
git checkout feature-branch

# Check commit history
git log --oneline
```

**Expected Output**:
```
mno345 Add data count function
jkl012 Add data clearing function
ghi789 Add data removal function
def456 Add data insertion function
abc123 Initial data structure
```

#### Step 4: Move Multiple Commits
```bash
# Switch to target branch
git checkout data-operations

# Cherry-pick range of commits (from def456 to mno345)
git cherry-pick def456^..mno345
```

**Command Explanation**:
- `def456^`: The commit before def456 (parent of def456)
- `..mno345`: All commits from def456 up to and including mno345
- This will copy commits def456, ghi789, jkl012, and mno345

#### Step 5: Verify the Move
```bash
# Check commit history on target branch
git log --oneline

# Check file content
cat data.js
```

**Expected Output**:
```
pqr789 Add data count function      # New commit hash
stu456 Add data clearing function   # New commit hash
vwx123 Add data removal function    # New commit hash
yza890 Add data insertion function  # New commit hash
bcd345 Initial data structure
```

#### Step 6: Clean Up Original Branch
```bash
# Switch back to feature branch
git checkout feature-branch

# Remove the moved commits using interactive rebase
git rebase -i HEAD~4
```

In the editor, change all the moved commits from `pick` to `drop`:
```
drop def456 Add data insertion function
drop ghi789 Add data removal function
drop jkl012 Add data clearing function
drop mno345 Add data count function
```

#### Questions to Answer:
1. How many commits were moved in this exercise?
2. What happened to the commit hashes after cherry-picking?
3. Why might you want to move multiple related commits together?

### Exercise 3: Using Rebase to Move Commits

#### Objective
Learn how to use rebase as an alternative method for moving commits.

#### Setup Instructions
```bash
# Create a new practice directory
mkdir rebase-moving-practice
cd rebase-moving-practice

# Initialize Git repository
git init

# Create initial content
echo "# Rebase Moving Practice" > README.md
echo "let config = {};" > config.js
git add .
git commit -m "Initial configuration"
```

#### Step 1: Create Branches with Commits
```bash
# Create main branch content
echo "function setConfig(key, value) { config[key] = value; }" >> config.js
git add config.js
git commit -m "Add configuration setter"

# Create feature branch
git checkout -b feature-branch
echo "function getConfig(key) { return config[key]; }" >> config.js
git add config.js
git commit -m "Add configuration getter"

echo "function hasConfig(key) { return key in config; }" >> config.js
git add config.js
git commit -m "Add configuration checker"
```

#### Step 2: Create Target Branch
```bash
# Switch to main and create target branch
git checkout main
git checkout -b config-utils
```

#### Step 3: Use Rebase to Move Commits
```bash
# Switch to feature branch
git checkout feature-branch

# Use rebase --onto to move commits
git rebase --onto config-utils main feature-branch
```

**Command Explanation**:
- `git rebase --onto config-utils main feature-branch`: Moves commits from feature-branch onto config-utils
- `--onto config-utils`: The new base branch
- `main`: The upstream branch (where to start from)
- `feature-branch`: The branch containing commits to move

#### Step 4: Verify the Result
```bash
# Check the commit history on config-utils branch
git checkout config-utils
git log --oneline
```

**Expected Output**:
```
ghi789 Add configuration checker    # New commit hash
def456 Add configuration getter     # New commit hash
abc123 Add configuration setter
mno345 Initial configuration
```

#### Step 5: Clean Up Feature Branch
```bash
# Switch to feature branch
git checkout feature-branch

# Reset the branch to remove moved commits
git reset --hard main
```

**Command Explanation**:
- `git reset --hard main`: Resets the feature-branch to match main
- This removes all commits that were moved to config-utils
- `--hard`: Discards all changes in working directory and staging area

#### Questions to Answer:
1. How does rebase --onto differ from cherry-pick?
2. What happened to the commit hashes after rebasing?
3. When would you use rebase --onto instead of cherry-pick?

### Exercise 4: Complex Commit Moving Scenario

#### Objective
Apply commit moving techniques to a realistic development scenario.

#### Setup Instructions
```bash
# Create a new practice directory
mkdir complex-moving-practice
cd complex-moving-practice

# Initialize Git repository
git init

# Create initial content
echo "# Complex Moving Practice" > README.md
echo "class User {" > user.js
echo "  constructor(name) { this.name = name; }" >> user.js
echo "}" >> user.js
git add .
git commit -m "Initial User class"
```

#### Step 1: Create Multiple Feature Branches
```bash
# Create authentication branch
git checkout -b auth
echo "  login() { console.log('User logged in'); }" >> user.js
git add user.js
git commit -m "Add login method"

echo "  logout() { console.log('User logged out'); }" >> user.js
git add user.js
git commit -m "Add logout method"

# Create profile branch
git checkout main
git checkout -b profile
echo "  updateProfile(data) { this.profile = data; }" >> user.js
git add user.js
git commit -m "Add profile update method"

echo "  getProfile() { return this.profile; }" >> user.js
git add user.js
git commit -m "Add profile getter method"
```

#### Step 2: Identify Commits to Reorganize
```bash
# Check commits on auth branch
git checkout auth
git log --oneline

# Check commits on profile branch
git checkout profile
git log --oneline
```

#### Step 3: Create New Organized Branch
```bash
# Create a new branch for organized user functionality
git checkout main
git checkout -b user-complete
```

#### Step 4: Move Commits in Logical Order
```bash
# First, move authentication methods
git cherry-pick <auth-login-commit>
git cherry-pick <auth-logout-commit>

# Then, move profile methods
git cherry-pick <profile-update-commit>
git cherry-pick <profile-getter-commit>
```

#### Step 5: Verify Organization
```bash
# Check the organized branch
git log --oneline

# Check the file content
cat user.js
```

#### Step 6: Clean Up Original Branches
```bash
# Remove commits from auth branch
git checkout auth
git rebase -i HEAD~2
# Change 'pick' to 'drop' for both commits

# Remove commits from profile branch
git checkout profile
git rebase -i HEAD~2
# Change 'pick' to 'drop' for both commits
```

#### Questions to Answer:
1. How did you decide the order of commits in the organized branch?
2. What are the benefits of organizing commits logically?
3. How would you handle conflicts if they occurred during cherry-picking?

---

**Next**: Learn about fast-forward vs non-fast-forward rebase!
