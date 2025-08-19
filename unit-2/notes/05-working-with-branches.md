# Topic 5: Creating and Working with Branches

## 🎯 Learning Objectives

By the end of this topic, you will understand:
- How to create, switch, and manage branches
- Working with multiple branches simultaneously
- Branch naming conventions and best practices
- How to update branches with latest changes
- Real-world applications in your codingGita projects
- GitHub's branch management features

---

## 🚀 Creating Your First Branch

### Step-by-Step Branch Creation

#### 1. **Start from Main Branch**
```bash
# Make sure you're on main branch
git checkout main

# Verify current branch
git branch --show-current
# Output: main
```

#### 2. **Create a New Feature Branch**
```bash
# Create and switch to new branch
git checkout -b feature/calculator

# Verify you're on new branch
git branch --show-current
# Output: feature/calculator
```

#### 3. **Make Changes and Commit**
```bash
# Create a new file
echo "# Calculator App" > calculator.html

# Add and commit
git add calculator.html
git commit -m "feat: create calculator interface"
```

#### 4. **Switch Back to Main**
```bash
# Go back to main branch
git checkout main

# Notice: calculator.html is not here!
ls
# Output: README.md (calculator.html is only in feature branch)
```

---

## 🔄 Working with Multiple Branches

### Real-Life Example: Portfolio Website Development

Imagine you're building a portfolio website with multiple features:

#### 1. **Main Branch (Stable)**
```bash
git checkout main
# This branch always has working code
```

#### 2. **About Page Feature**
```bash
git checkout -b feature/about-page
# Work on about page
echo "# About Me" > about.html
git add about.html
git commit -m "feat: create about page"
```

#### 3. **Projects Showcase Feature**
```bash
git checkout -b feature/projects-showcase
# Work on projects page
echo "# My Projects" > projects.html
git add projects.html
git commit -m "feat: create projects showcase"
```

#### 4. **Contact Form Feature**
```bash
git checkout -b feature/contact-form
# Work on contact form
echo "# Contact Me" > contact.html
git add contact.html
git commit -m "feat: create contact form"
```

### Branch Structure Visualization
```bash
# View all branches
git branch -a

# Output:
# * feature/contact-form
#   feature/projects-showcase
#   feature/about-page
#   main
```

---

## 🌿 Branch Naming Conventions

### Recommended Naming Patterns

#### 1. **Feature Branches**
```bash
# Format: feature/description
feature/user-authentication
feature/calculator-app
feature/portfolio-website
feature/dark-mode-toggle
feature/mobile-responsive-design
```

#### 2. **Bug Fix Branches**
```bash
# Format: fix/description
fix/login-validation-error
fix/calculation-bug
fix/mobile-responsive-issue
fix/typo-in-readme
fix/button-hover-effect
```

#### 3. **Documentation Branches**
```bash
# Format: docs/description
docs/update-readme
docs/add-installation-guide
docs/improve-api-documentation
docs/add-code-examples
docs/update-troubleshooting
```

#### 4. **Hotfix Branches**
```bash
# Format: hotfix/description
hotfix/critical-security-issue
hotfix/breaking-change-fix
hotfix/urgent-bug-fix
```

### Real-Life codingGita Examples
```bash
# Assignment 1: Calculator
feature/assignment1-calculator
feature/assignment1-styling
feature/assignment1-testing

# Assignment 2: Portfolio
feature/assignment2-portfolio
feature/assignment2-responsive
feature/assignment2-contact-form

# Group Project
feature/group-project-login
feature/group-project-database
feature/group-project-ui
```

---

## 🔧 Essential Branch Commands

### 1. **Branch Creation and Switching**
```bash
# Create new branch
git branch feature-name

# Create and switch to new branch
git checkout -b feature-name

# Modern way to create and switch
git switch -c feature-name

# Switch to existing branch
git checkout branch-name
git switch branch-name
```

### 2. **Branch Information**
```bash
# List local branches
git branch

# List all branches (local and remote)
git branch -a

# List branches with details
git branch -v

# Show current branch
git branch --show-current

# Show merged branches
git branch --merged

# Show unmerged branches
git branch --no-merged
```

### 3. **Branch Management**
```bash
# Rename current branch
git branch -m new-name

# Delete local branch (after merging)
git branch -d feature-name

# Force delete branch (even if not merged)
git branch -D feature-name

# Push branch to remote
git push -u origin feature-name
```

---

## 📡 Working with Remote Branches

### 1. **Pushing Branches to GitHub**
```bash
# First time pushing a branch
git push -u origin feature-name

# Subsequent pushes
git push origin feature-name

# Push all branches
git push --all origin
```

### 2. **Pulling Remote Branches**
```bash
# Fetch all remote branches
git fetch origin

# Checkout remote branch
git checkout -b feature-name origin/feature-name

# Pull latest changes from remote branch
git pull origin feature-name
```

### 3. **Tracking Remote Branches**
```bash
# Set up tracking for current branch
git branch --set-upstream-to=origin/feature-name

# Check tracking information
git branch -vv
```

---

## 🔄 Updating Branches

### 1. **Keeping Feature Branches Updated**
```bash
# Switch to main branch
git checkout main

# Pull latest changes
git pull origin main

# Switch to feature branch
git checkout feature/calculator

# Merge main into feature branch
git merge main

# This brings your feature branch up to date
```

### 2. **Rebasing (Alternative to Merging)**
```bash
# Switch to feature branch
git checkout feature/calculator

# Rebase on main (cleaner history)
git rebase main

# This rewrites your commits on top of main
```

### 3. **When to Use Each Method**
```bash
# Use merge when:
# - Feature branch is shared with others
# - You want to preserve exact history
git merge main

# Use rebase when:
# - Feature branch is only yours
# - You want clean, linear history
git rebase main
```

---

## 🌐 GitHub Branch Management

### 1. **Creating Branches on GitHub**
- **Web Interface:** Click branch dropdown → "New branch"
- **Command Line:** Create locally, then push
- **Pull Request:** GitHub creates branch automatically

### 2. **Branch Protection Rules**
```bash
# Protect main branch from direct pushes
# Require pull requests for changes
# Require code review before merging
# Require status checks to pass
```

### 3. **Branch Visualization**
- **Network Graph:** Shows branch relationships
- **Commit History:** Shows commits per branch
- **Branch Comparison:** Compare any two branches

### 4. **GitHub Branch Features**
- **Branch Descriptions:** Add context to branches
- **Branch Templates:** Standardize branch creation
- **Auto-deletion:** Remove branches after merging
- **Branch Insights:** See branch activity and health

---

## 🎯 Real-Life codingGita Workflows

### Workflow 1: Individual Assignment Development
```bash
# Start assignment
git checkout main
git checkout -b assignment1-calculator

# Work on calculator
echo "# Calculator App" > index.html
git add index.html
git commit -m "feat: create calculator structure"

# Add styling
echo "/* Calculator styles */" > style.css
git add style.css
git commit -m "style: add calculator styling"

# Add functionality
echo "// Calculator logic" > script.js
git add script.js
git commit -m "feat: implement calculator functions"

# Test and finalize
git commit -m "test: add unit tests for calculator"
git commit -m "docs: add user manual"

# Ready to merge back to main
git checkout main
git merge assignment1-calculator
```

### Workflow 2: Group Project Collaboration
```bash
# Priya works on user interface
git checkout -b feature/priya-ui
# Work on UI components
git push -u origin feature/priya-ui

# Rahul works on backend
git checkout -b feature/rahul-backend
# Work on backend logic
git push -u origin feature/rahul-backend

# Anjali works on database
git checkout -b feature/anjali-database
# Work on database design
git push -u origin feature/anjali-database

# Each person works independently
# Changes are combined through pull requests
```

### Workflow 3: Bug Fix Development
```bash
# Discover bug in main branch
git checkout main
git checkout -b fix/calculation-error

# Fix the bug
# Edit the problematic file
git add .
git commit -m "fix: resolve calculation error in grade calculator"

# Test the fix
# Make sure it works

# Merge back to main
git checkout main
git merge fix/calculation-error

# Delete fix branch
git branch -d fix/calculation-error
```

---

## ⚠️ Common Branching Mistakes

### Mistake 1: Working on Wrong Branch
```bash
# ❌ Bad - Working on main branch
git checkout main
# Make changes and commit
git commit -m "Add new feature"

# ✅ Good - Create feature branch first
git checkout -b feature/new-feature
# Make changes and commit
git commit -m "Add new feature"
```

### Mistake 2: Not Updating Feature Branches
```bash
# ❌ Bad - Feature branch becomes outdated
git checkout -b feature/calculator
# Work for days without updating from main

# ✅ Good - Regular updates from main
git checkout feature/calculator
git merge main  # Keep feature branch updated
```

### Mistake 3: Poor Branch Naming
```bash
# ❌ Bad - Unclear names
git checkout -b new
git checkout -b stuff
git checkout -b fix

# ✅ Good - Descriptive names
git checkout -b feature/user-authentication
git checkout -b feature/portfolio-website
git checkout -b fix/login-validation-error
```

---

## 🧪 Practice Exercises

### Exercise 1: Basic Branch Operations
1. Create a new repository called `branch-practice`
2. Create three feature branches:
   - `feature/homepage`
   - `feature/about-page`
   - `feature/contact-form`
3. Work on each branch separately
4. Practice switching between branches
5. See how files exist only in their respective branches

### Exercise 2: Branch Collaboration Simulation
1. Create a main branch with basic project structure
2. Create feature branches for different components
3. Work on each feature independently
4. Update feature branches from main
5. Practice merging features back to main

### Exercise 3: GitHub Branch Management
1. Push your branches to GitHub
2. Create pull requests for each feature
3. Review the branch visualization on GitHub
4. Practice merging through pull requests
5. Delete merged branches

---

## 📋 Quick Reference

### Essential Branch Commands
```bash
git branch                    # List branches
git branch feature-name       # Create branch
git checkout feature-name     # Switch to branch
git checkout -b feature-name  # Create and switch
git switch -c feature-name    # Modern create and switch
git branch -d feature-name    # Delete branch
git push -u origin feature-name # Push new branch
```

### Branch Information
```bash
git branch --show-current    # Current branch
git branch -a                # All branches
git branch -v                # Branch details
git branch --merged          # Merged branches
git branch -vv               # Tracking information
```

### Branch Management
```bash
git branch -m new-name       # Rename branch
git fetch origin             # Get remote branches
git merge main               # Update from main
git rebase main              # Clean update from main
```

---

## 🎓 Summary

**Key Takeaways:**
- Branches enable parallel development and experimentation
- Use descriptive naming conventions for clarity
- Keep feature branches updated from main
- GitHub provides excellent branch management tools
- Good branching workflow improves project organization

**Next Steps:**
- Practice creating and managing branches
- Learn how to merge branches safely
- Understand merge conflicts and resolution
- Get ready to handle merge conflicts!

---

## 🔗 Related Topics

- **Next:** [Resolving Merge Conflicts](06-merge-conflicts.md)
- **Previous:** [Understanding Branching and Merging](04-branching-merging.md)
- **GitHub:** [Managing Branches](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-and-deleting-branches-within-your-repository)
