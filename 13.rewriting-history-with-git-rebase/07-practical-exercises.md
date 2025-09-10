# Practical Exercises for Git Rebase

## 🎯 Learning Objectives
By the end of these exercises, you will have:
- Hands-on experience with all rebase concepts
- Confidence in using rebase commands
- Understanding of when and how to resolve conflicts
- Practical skills for real-world scenarios

## 📋 Exercise Setup

Before starting any exercise, create a practice repository:

```bash
# Create practice directory
mkdir git-rebase-practice
cd git-rebase-practice

# Initialize git repository
git init

# Create initial files
echo "# My Project" > README.md
echo "console.log('Hello World');" > app.js
git add .
git commit -m "Initial commit"
```

## 🚀 Exercise 1: Understanding Rebasing vs Merging

### Objective
Compare the visual differences between merging and rebasing.

### Steps

1. **Create the base scenario**:
   ```bash
   # Create main branch content
   echo "// Main branch feature" >> app.js
   git add app.js
   git commit -m "Add main branch feature"
   
   # Create feature branch
   git checkout -b feature-branch
   echo "// Feature branch work" >> app.js
   git add app.js
   git commit -m "Add feature branch work"
   
   # Add more commits to main
   git checkout main
   echo "// Another main feature" >> app.js
   git add app.js
   git commit -m "Add another main feature"
   ```

2. **Create a backup for merging**:
   ```bash
   git checkout feature-branch
   git checkout -b feature-merge-backup
   ```

3. **Perform a merge**:
   ```bash
   git checkout feature-branch
   git merge main
   ```

4. **Observe the result**:
   ```bash
   git log --oneline --graph
   ```

5. **Reset and try rebasing**:
   ```bash
   git checkout feature-merge-backup
   git checkout -b feature-rebase
   git rebase main
   ```

6. **Compare the results**:
   ```bash
   git log --oneline --graph
   ```

### Expected Outcomes
- **Merge**: Creates a merge commit and preserves branching structure
- **Rebase**: Creates linear history without merge commits

### Questions to Answer
1. What is the difference in the commit graph?
2. Which approach creates cleaner history?
3. When would you prefer each approach?

---

## 🔄 Exercise 2: Moving Commits Between Branches

### Objective
Practice moving commits from one branch to another using different methods.

### Scenario Setup
```bash
# Reset to clean state
git checkout main
git reset --hard HEAD~3  # Go back to initial commit

# Create two feature branches
git checkout -b frontend-feature
echo "// Frontend code" > frontend.js
git add frontend.js
git commit -m "Add frontend component"

echo "// More frontend code" >> frontend.js
git add frontend.js
git commit -m "Add frontend styling"

git checkout main
git checkout -b backend-feature
echo "// Backend code" > backend.js
git add backend.js
git commit -m "Add backend API"

echo "// More backend code" >> backend.js
git add backend.js
git commit -m "Add backend validation"
```

### Task 1: Move Commits Using Cherry-pick

1. **Identify commits to move**:
   ```bash
   git log --oneline frontend-feature
   ```

2. **Move commits to backend-feature**:
   ```bash
   git checkout backend-feature
   git cherry-pick <frontend-commit-1>
   git cherry-pick <frontend-commit-2>
   ```

3. **Verify the move**:
   ```bash
   git log --oneline --graph
   ```

### Task 2: Move Commits Using Rebase

1. **Create a new branch for the move**:
   ```bash
   git checkout main
   git checkout -b combined-feature
   ```

2. **Use rebase to move commits**:
   ```bash
   git rebase --onto combined-feature frontend-feature~2 frontend-feature
   ```

3. **Verify the result**:
   ```bash
   git log --oneline --graph
   ```

### Questions to Answer
1. Which method was easier to use?
2. What are the differences in the final commit history?
3. When would you use each method?

---

## ⚡ Exercise 3: Fast-Forward vs Non-Fast-Forward Rebase

### Objective
Experience both types of rebase scenarios.

### Scenario A: Fast-Forward Rebase

1. **Create clean scenario**:
   ```bash
   git checkout main
   git reset --hard HEAD~5  # Clean slate
   
   # Add content to main
   echo "// Main feature 1" > main-feature.js
   git add main-feature.js
   git commit -m "Add main feature 1"
   
   # Create feature branch
   git checkout -b clean-feature
   echo "// Clean feature" > clean-feature.js
   git add clean-feature.js
   git commit -m "Add clean feature"
   ```

2. **Perform fast-forward rebase**:
   ```bash
   git rebase main
   ```

3. **Observe the result**:
   ```bash
   git log --oneline --graph
   ```

### Scenario B: Non-Fast-Forward Rebase

1. **Create conflict scenario**:
   ```bash
   git checkout main
   echo "// Main feature 2" >> main-feature.js
   git add main-feature.js
   git commit -m "Add main feature 2"
   
   git checkout clean-feature
   echo "// Clean feature update" >> clean-feature.js
   git add clean-feature.js
   git commit -m "Update clean feature"
   
   # Create conflict by modifying same file
   echo "// Conflicting change" >> main-feature.js
   git add main-feature.js
   git commit -m "Add conflicting change"
   ```

2. **Attempt rebase (will create conflicts)**:
   ```bash
   git rebase main
   ```

3. **Resolve conflicts**:
   ```bash
   # Edit main-feature.js to resolve conflicts
   git add main-feature.js
   git rebase --continue
   ```

### Questions to Answer
1. What was the difference in the rebase process?
2. How did you resolve the conflicts?
3. What would happen if you couldn't resolve conflicts?

---

## 🛠️ Exercise 4: Interactive Rebase

### Objective
Master interactive rebase for cleaning up commit history.

### Setup
```bash
git checkout main
git reset --hard HEAD~10  # Clean slate

# Create messy commit history
git checkout -b messy-feature
echo "// Feature 1" > feature1.js
git add feature1.js
git commit -m "Add feature 1"

echo "// Feature 2" > feature2.js
git add feature2.js
git commit -m "Add feature 2"

echo "// Fix typo" >> feature1.js
git add feature1.js
git commit -m "Fix typo in feature 1"

echo "// More features" >> feature2.js
git add feature2.js
git commit -m "Add more to feature 2"

echo "// Another typo fix" >> feature1.js
git add feature1.js
git commit -m "Fix another typo"
```

### Task: Clean Up History

1. **Start interactive rebase**:
   ```bash
   git rebase -i HEAD~5
   ```

2. **In the editor, modify the rebase plan**:
   ```text
   pick abc123 Add feature 1
   pick def456 Add feature 2
   squash ghi789 Fix typo in feature 1
   pick jkl012 Add more to feature 2
   squash mno345 Fix another typo
   ```

3. **Complete the rebase**:
   - Save and close the editor
   - Edit commit messages as prompted
   - Complete the rebase

4. **Verify the result**:
   ```bash
   git log --oneline
   ```

### Advanced Task: Reorder Commits

1. **Create more commits**:
   ```bash
   echo "// Feature 3" > feature3.js
   git add feature3.js
   git commit -m "Add feature 3"
   
   echo "// Feature 4" > feature4.js
   git add feature4.js
   git commit -m "Add feature 4"
   ```

2. **Reorder commits**:
   ```bash
   git rebase -i HEAD~4
   ```

3. **In the editor, reorder the commits**:
   ```text
   pick abc123 Add feature 1
   pick def456 Add feature 2
   pick ghi789 Add feature 4
   pick jkl012 Add feature 3
   ```

### Questions to Answer
1. How did squashing affect your commit history?
2. What happened when you reordered commits?
3. When would you use interactive rebase?

---

## ⚠️ Exercise 5: Conflict Resolution Practice

### Objective
Practice resolving different types of conflicts during rebase.

### Setup Complex Conflicts
```bash
git checkout main
git reset --hard HEAD~15  # Clean slate

# Create conflicting branches
git checkout -b conflict-branch-1
echo "function calculate(a, b) {" > calculator.js
echo "    return a + b;" >> calculator.js
echo "}" >> calculator.js
git add calculator.js
git commit -m "Add calculator function"

echo "function multiply(a, b) {" >> calculator.js
echo "    return a * b;" >> calculator.js
echo "}" >> calculator.js
git add calculator.js
git commit -m "Add multiply function"

git checkout main
git checkout -b conflict-branch-2
echo "function calculate(a, b) {" > calculator.js
echo "    return a - b;" >> calculator.js
echo "}" >> calculator.js
git add calculator.js
git commit -m "Add calculator function (different implementation)"

echo "function divide(a, b) {" >> calculator.js
echo "    return a / b;" >> calculator.js
echo "}" >> calculator.js
git add calculator.js
git commit -m "Add divide function"
```

### Task: Resolve Conflicts

1. **Attempt rebase**:
   ```bash
   git checkout conflict-branch-1
   git rebase conflict-branch-2
   ```

2. **Resolve conflicts**:
   ```bash
   # Check status
   git status
   
   # Edit calculator.js to resolve conflicts
   # Keep both implementations or create a combined version
   
   # Stage resolved file
   git add calculator.js
   
   # Continue rebase
   git rebase --continue
   ```

3. **Handle additional conflicts**:
   - Repeat the process for each conflicted commit
   - Test your resolution

### Advanced Task: File Deletion Conflicts

1. **Create deletion conflict**:
   ```bash
   git checkout main
   git checkout -b delete-branch
   rm calculator.js
   git add calculator.js
   git commit -m "Remove calculator.js"
   
   git checkout conflict-branch-1
   echo "// Updated calculator" >> calculator.js
   git add calculator.js
   git commit -m "Update calculator"
   ```

2. **Resolve deletion conflict**:
   ```bash
   git rebase delete-branch
   # Choose to keep or delete the file
   ```

### Questions to Answer
1. How did you resolve the content conflicts?
2. What strategy did you use for the deletion conflict?
3. How did you test your resolution?

---

## 🎯 Exercise 6: Real-World Scenario

### Objective
Apply rebase skills to a realistic development scenario.

### Scenario: Feature Branch Cleanup

You're working on a feature branch that needs to be cleaned up before merging to main.

### Setup
```bash
git checkout main
git reset --hard HEAD~20  # Clean slate

# Simulate main branch development
echo "// Main app" > app.js
git add app.js
git commit -m "Initial app setup"

echo "// Add authentication" >> app.js
git add app.js
git commit -m "Add authentication"

echo "// Add user management" >> app.js
git add app.js
git commit -m "Add user management"

# Create your feature branch
git checkout -b user-profile-feature
echo "// User profile component" > user-profile.js
git add user-profile.js
git commit -m "Add user profile component"

echo "// Profile styling" >> user-profile.js
git add user-profile.js
git commit -m "Add profile styling"

echo "// Fix typo" >> user-profile.js
git add user-profile.js
git commit -m "Fix typo in profile"

echo "// Add profile validation" >> user-profile.js
git add user-profile.js
git commit -m "Add profile validation"

echo "// Fix validation bug" >> user-profile.js
git add user-profile.js
git commit -m "Fix validation bug"

echo "// Add profile tests" > user-profile.test.js
git add user-profile.test.js
git commit -m "Add profile tests"

echo "// Fix test typo" >> user-profile.test.js
git add user-profile.test.js
git commit -m "Fix test typo"
```

### Task: Clean Up Feature Branch

1. **Analyze the commit history**:
   ```bash
   git log --oneline
   ```

2. **Plan your cleanup**:
   - Identify commits that should be combined
   - Identify commits that should be reordered
   - Identify commits that should be dropped

3. **Perform interactive rebase**:
   ```bash
   git rebase -i main
   ```

4. **Clean up the history**:
   - Squash related commits
   - Reorder commits logically
   - Drop unnecessary commits
   - Reword commit messages

5. **Test your changes**:
   ```bash
   # Verify files are correct
   ls -la
   cat user-profile.js
   cat user-profile.test.js
   ```

6. **Update main branch**:
   ```bash
   git checkout main
   git pull origin main  # Simulate main updates
   ```

7. **Rebase onto updated main**:
   ```bash
   git checkout user-profile-feature
   git rebase main
   ```

8. **Resolve any conflicts**:
   - Handle conflicts if they arise
   - Test your resolution

### Final Verification

```bash
# Check final history
git log --oneline --graph

# Verify all files are present and correct
git status
ls -la

# Test your feature
node user-profile.js  # or your test command
```

### Questions to Answer
1. How did you organize your commits?
2. What conflicts did you encounter?
3. How did you resolve them?
4. What would you do differently next time?

---

## 📊 Exercise Summary and Reflection

### Complete This Checklist

After completing all exercises, reflect on:

- [ ] **Understanding**: Do you understand when to use rebase vs merge?
- [ ] **Commands**: Can you use rebase commands confidently?
- [ ] **Conflicts**: Can you resolve rebase conflicts?
- [ ] **History**: Can you clean up commit history effectively?
- [ ] **Safety**: Do you understand the risks and how to mitigate them?

### Key Skills Developed

1. **Visual Understanding**: Seeing the difference between merge and rebase
2. **Command Proficiency**: Using rebase commands effectively
3. **Conflict Resolution**: Handling various conflict scenarios
4. **History Management**: Cleaning up commit history
5. **Real-World Application**: Applying skills to realistic scenarios

### Next Steps

1. **Practice regularly** with your own projects
2. **Experiment safely** with backup branches
3. **Learn advanced techniques** as you become more comfortable
4. **Share knowledge** with team members
5. **Stay updated** with Git best practices

## 🎯 Final Challenge

Create a comprehensive rebase workflow that includes:
- Creating a feature branch
- Making multiple commits
- Cleaning up history with interactive rebase
- Rebasing onto updated main
- Resolving conflicts
- Final verification

Document your process and share it with others!

---

**Congratulations!** You've completed all the practical exercises for Git Rebase. You now have hands-on experience with all the key concepts and should feel confident using rebase in your development workflow.
