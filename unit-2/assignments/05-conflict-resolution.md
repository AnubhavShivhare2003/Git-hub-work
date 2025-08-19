# Assignment 5: Conflict Resolution

## 🎯 Assignment Overview

**Goal:** Learn how to identify, understand, and resolve merge conflicts confidently using different resolution strategies.

**Duration:** 60-75 minutes
**Difficulty:** Intermediate to Advanced
**Prerequisites:** Assignment 4 completion, understanding of merging

---

## 📚 What You'll Learn

By completing this assignment, you will:
- ✅ Create merge conflicts intentionally
- ✅ Identify conflict markers in files
- ✅ Resolve conflicts using different strategies
- ✅ Choose the best resolution approach
- ✅ Complete conflicted merges successfully
- ✅ Build confidence in handling conflicts

---

## 🚀 Step-by-Step Instructions

### Step 1: Prepare Your Repository

```bash
# Make sure you're in your learning journal repository
cd codinggita-learning-journal

# Check current status
git status

# Should show: "working tree clean"

# Check current branch
git branch --show-current

# Should show: main
```

### Step 2: Create a New Feature Branch

```bash
# Create a new feature branch for a contact form
git checkout -b feature/contact-form

# Verify you're on the new branch
git branch --show-current

# Should show: feature/contact-form
```

### Step 3: Work on Contact Form in Feature Branch

```bash
# Create the contact form HTML file
echo "<!DOCTYPE html>" > src/contact.html
echo "<html lang=\"en\">" >> src/contact.html
echo "<head>" >> src/contact.html
echo "    <meta charset=\"UTF-8\">" >> src/contact.html
echo "    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">" >> src/contact.html
echo "    <title>Contact Me - codingGita Portfolio</title>" >> src/contact.html
echo "    <link rel=\"stylesheet\" href=\"../css/contact.css\">" >> src/contact.html
echo "</head>" >> src/contact.html
echo "<body>" >> src/contact.html
echo "    <div class=\"contact-container\">" >> src/contact.html
echo "        <h1>Get In Touch</h1>" >> src/contact.html
echo "        <form class=\"contact-form\">" >> src/contact.html
echo "            <div class=\"form-group\">" >> src/contact.html
echo "                <label for=\"name\">Name:</label>" >> src/contact.html
echo "                <input type=\"text\" id=\"name\" name=\"name\" required>" >> src/contact.html
echo "            </div>" >> src/contact.html
echo "            <div class=\"form-group\">" >> src/contact.html
echo "                <label for=\"email\">Email:</label>" >> src/contact.html
echo "                <input type=\"email\" id=\"email\" name=\"email\" required>" >> src/contact.html
echo "            </div>" >> src/contact.html
echo "            <div class=\"form-group\">" >> src/contact.html
echo "                <label for=\"message\">Message:</label>" >> src/contact.html
echo "                <textarea id=\"message\" name=\"message\" rows=\"5\" required></textarea>" >> src/contact.html
echo "            </div>" >> src/contact.html
echo "            <button type=\"submit\">Send Message</button>" >> src/contact.html
echo "        </form>" >> src/contact.html
echo "    </div>" >> src/contact.html
echo "    <script src=\"../js/contact.js\"></script>" >> src/contact.html
echo "</body>" >> src/contact.html
echo "</html>" >> src/contact.html
```

### Step 4: Commit Contact Form

```bash
# Add the contact form file
git add src/contact.html

# Commit with descriptive message
git commit -m "feat: create contact form interface

- Add HTML5 form with proper validation
- Include name, email, and message fields
- Use semantic HTML structure
- Link to CSS and JavaScript files
- Follow accessibility best practices"
```

### Step 5: Switch to Main and Modify Portfolio

```bash
# Switch to main branch
git checkout main

# Modify the portfolio.html file to add a contact section
echo "        <section id=\"contact\">" >> src/portfolio.html
echo "            <h2>Contact Me</h2>" >> src/portfolio.html
echo "            <p>Get in touch for collaborations or questions!</p>" >> src/portfolio.html
echo "            <a href=\"contact.html\" class=\"contact-btn\">Contact Form</a>" >> src/portfolio.html
echo "        </section>" >> src/portfolio.html
echo "    </main>" >> src/portfolio.html
echo "    <script src=\"../js/portfolio.js\"></script>" >> src/portfolio.html
echo "</body>" >> src/portfolio.html
echo "</html>" >> src/portfolio.html
```

### Step 6: Commit Portfolio Changes

```bash
# Add the modified portfolio file
git add src/portfolio.html

# Commit with descriptive message
git commit -m "feat: add contact section to portfolio

- Include contact section with navigation
- Add link to contact form page
- Improve portfolio navigation structure
- Enhance user experience with contact options"
```

### Step 7: Create the Conflict

```bash
# Now try to merge the contact form branch
git merge feature/contact-form

# Git will show a conflict message:
# "CONFLICT (content): Merge conflict in src/portfolio.html"
# "Automatic merge failed; fix conflicts and then commit the result."
```

### Step 8: Understand the Conflict

```bash
# Check the status
git status

# Should show:
# "You have unmerged paths.
#   (fix conflicts and run "git commit")
#   (use "git merge --abort" to abort the merge)
#
# Unmerged paths:
#   (use "git add <file>..." to mark resolution)
#         both modified:   src/portfolio.html"
```

### Step 9: Examine the Conflict

```bash
# Open src/portfolio.html in your text editor
# Look for conflict markers:

# <<<<<<< HEAD
# [Your changes from main branch]
# =======
# [Changes from feature branch]
# >>>>>>> feature/contact-form

# The conflict is in the portfolio.html file
# Both branches modified the same file in different ways
```

### Step 10: Resolve the Conflict

You have several options for resolving this conflict:

#### Option 1: Keep Both Changes (Recommended)
```html
        <section id="contact">
            <h2>Contact Me</h2>
            <p>Get in touch for collaborations or questions!</p>
            <a href="contact.html" class="contact-btn">Contact Form</a>
        </section>
    </main>
    <script src="../js/portfolio.js"></script>
</body>
</html>
```

#### Option 2: Keep Main Branch Changes Only
```html
        <section id="contact">
            <h2>Contact Me</h2>
            <p>Get in touch for collaborations or questions!</p>
            <a href="contact.html" class="contact-btn">Contact Form</a>
        </section>
    </main>
    <script src="../js/portfolio.js"></script>
</body>
</html>
```

#### Option 3: Keep Feature Branch Changes Only
```html
    </main>
    <script src="../js/portfolio.js"></script>
</body>
</html>
```

### Step 11: Choose Your Resolution Strategy

For this assignment, let's use **Option 1: Keep Both Changes** because:
- Main branch adds the contact section
- Feature branch adds the contact form page
- Both are valuable and complementary

### Step 12: Edit the File

```bash
# Open src/portfolio.html in your text editor
# Remove all conflict markers (<<<<<<<, =======, >>>>>>>)
# Keep the content you want (in this case, both changes)
# Save the file
```

### Step 13: Mark Conflict as Resolved

```bash
# Add the resolved file
git add src/portfolio.html

# Check status
git status

# Should show: "All conflicts fixed but you are still merging"
```

### Step 14: Complete the Merge

```bash
# Complete the merge by committing
git commit -m "Merge branch 'feature/contact-form'

- Resolve merge conflict in portfolio.html
- Integrate contact section from main branch
- Add contact form page from feature branch
- Maintain both features for complete functionality"
```

### Step 15: Verify the Merge

```bash
# Check that the merge is complete
git status

# Should show: "working tree clean"

# View the merged file
cat src/portfolio.html

# Should show the resolved content without conflict markers
```

### Step 16: Test the Resolved Project

```bash
# Test both files:
# 1. Portfolio: file:///path/to/your/repository/src/portfolio.html
# 2. Contact Form: file:///path/to/your/repository/src/contact.html

# Make sure:
# - Portfolio loads correctly with contact section
# - Contact form loads correctly
# - Navigation between pages works
```

### Step 17: Clean Up

```bash
# Delete the feature branch locally
git branch -d feature/contact-form

# Push the updated main branch
git push origin main
```

---

## 🧪 Testing Your Conflict Resolution

### Test 1: Conflict Resolution
```bash
# Check that conflict markers are gone
grep -n "<<<<<<<" src/portfolio.html
grep -n "=======" src/portfolio.html
grep -n ">>>>>>>" src/portfolio.html

# Should show no results (no conflict markers)
```

### Test 2: File Integrity
```bash
# Check that both features are present
grep -n "Contact Me" src/portfolio.html
grep -n "contact.html" src/portfolio.html

# Should show the contact section and link
```

### Test 3: Merge History
```bash
# View the merge commit
git log --merges --oneline -1

# Should show your conflict resolution commit
```

---

## 📋 Assignment Checklist

- [ ] Contact form feature branch created
- [ ] Portfolio modified in main branch
- [ ] Merge conflict intentionally created
- [ ] Conflict markers identified
- [ ] Conflict resolved using chosen strategy
- [ ] Merge completed successfully
- [ ] Project tested after resolution
- [ ] Feature branch cleaned up
- [ ] Changes pushed to GitHub

---

## 🎯 Success Criteria

**Your assignment is complete when:**
- ✅ Merge conflict is successfully created
- ✅ Conflict markers are properly identified
- ✅ Conflict is resolved using appropriate strategy
- ✅ Merge is completed without errors
- ✅ Both features work correctly
- ✅ Project is properly tested
- ✅ Repository is clean and organized

---

## ⚠️ Conflict Resolution Strategies

### 1. **Keep Both Changes (Accept Both)**
```bash
# When both changes are valuable
# Combine the best of both versions
# Most common in collaborative development
```

### 2. **Keep Your Changes (Accept Current)**
```bash
# When your version is better
# Discard incoming changes
# Use when you're confident in your approach
```

### 3. **Keep Their Changes (Accept Incoming)**
```bash
# When incoming version is better
# Discard your changes
# Use when collaborating with experts
```

### 4. **Write Something Completely New**
```bash
# When neither version is ideal
# Create a better solution
# Use when you have a better approach
```

---

## 🆘 Troubleshooting

### Problem: Can't find conflict markers
```bash
# Check if you're actually in a merge state
git status

# Look for "You have unmerged paths"
# If not merging, you won't see conflicts
```

### Problem: Merge won't complete
```bash
# Make sure all conflicts are resolved
git status

# Look for "All conflicts fixed but you are still merging"
# If you see unmerged paths, resolve them first
```

### Problem: Want to start over
```bash
# Abort the merge
git merge --abort

# This will return you to the state before merging
# You can then try a different approach
```

---

## 🚀 Next Steps

After completing this assignment:
1. **Practice creating more conflicts** to build confidence
2. **Try different resolution strategies** in future projects
3. **Move to Assignment 6:** GitHub Collaboration
4. **Start handling conflicts** in real collaborative projects

---

## 💡 Bonus Challenges

### Challenge 1: Multiple File Conflicts
- Create conflicts in multiple files
- Practice resolving complex conflicts
- Use different strategies for different files

### Challenge 2: Advanced Conflict Resolution
- Use visual merge tools
- Practice with different file types
- Handle binary file conflicts

### Challenge 3: Conflict Prevention
- Learn to avoid conflicts
- Use better branching strategies
- Communicate with team members

---

## 🎓 Learning Reflection

**After completing this assignment, ask yourself:**
- How do you feel about handling conflicts now?
- What strategy worked best for you?
- How can you prevent conflicts in the future?
- What would you do differently next time?

---

## 🔗 Related Resources

- **Topic Notes:** [Resolving Merge Conflicts](../notes/06-merge-conflicts.md)
- **Git Conflicts:** [Git Documentation](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging#_basic_merge_conflicts)
- **Conflict Resolution Tools:** [VS Code Git](https://code.visualstudio.com/docs/editor/versioncontrol)

---

## 🌟 Conflict Resolution Best Practices

### 1. **Before Resolving**
```bash
# Understand what caused the conflict
# Read both versions carefully
# Decide on the best resolution strategy
```

### 2. **During Resolution**
```bash
# Remove all conflict markers
# Test your resolution
# Make sure the result makes sense
```

### 3. **After Resolution**
```bash
# Test the merged project thoroughly
# Document what you did
# Learn from the conflict
```

---

**Excellent work on mastering conflict resolution! ⚠️**

You're now ready to handle any merge conflicts that come your way in real projects!
