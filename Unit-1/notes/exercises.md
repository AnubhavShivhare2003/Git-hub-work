# Unit 1: Practical Exercises and Hands-On Examples

## Hands-On Learning: Let's Practice Git!

**Remember:** The best way to learn Git is by doing! These exercises will help you understand Git through real practice.

---

## Exercise 1: Your First Git Project (codingGita Learning Journal)

### What We'll Build
A personal learning journal where you'll track your codingGita journey using Git.

### Step-by-Step Instructions

**Step 1: Create Your Project Folder**
```bash
# Open your terminal/command prompt and type:
mkdir codingGita-journal
cd codingGita-journal
```

**What This Does:**
- Creates a new folder called "codingGita-journal"
- Moves you inside that folder
- Like creating a new notebook for your studies

**Step 2: Initialize Git**
```bash
git init
```

**What You Should See:**
```
Initialized empty Git repository in /path/to/codingGita-journal/.git/
```

**What This Means:**
- Git is now watching this folder
- Every change you make will be tracked
- Like opening the first page of your notebook

**Step 3: Create Your First File**
```bash
# Create a README file:
echo "# My codingGita Learning Journey" > README.md
```

**What This Does:**
- Creates a file called README.md
- Puts the title inside it
- Like writing the title on your notebook's first page

**Step 4: Check Git Status**
```bash
git status
```

**What You Should See:**
```
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" and/or "git commit -m <message>" to commit)
```

**What This Means:**
- Git sees your new file
- But it's not tracking it yet
- Like having a photo but not putting it in an album

**Step 5: Add Your File to Git**
```bash
git add README.md
```

**What This Does:**
- Tells Git "I want to save this file"
- Moves it to the staging area
- Like selecting a photo to print

**Step 6: Check Status Again**
```bash
git status
```

**What You Should See:**
```
On branch main
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   README.md
```

**What This Means:**
- Your file is ready to be saved permanently
- Like having your photo ready for the album

**Step 7: Save Your Work (Commit)**
```bash
git commit -m "Created my codingGita learning journal"
```

**What You Should See:**
```
[main (root-commit) abc1234] Created my codingGita learning journal
 1 file changed, 1 insertion(+)
```

**What This Means:**
- Your work is now permanently saved!
- Git gave it a unique ID (abc1234)
- Like putting your photo in the album

**Step 8: View Your History**
```bash
git log
```

**What You Should See:**
```
commit abc1234 (HEAD -> main)
Author: Your Name <your.email@college.edu>
Date:   [Current Date and Time]

    Created my codingGita learning journal
```

**What This Means:**
- You can see when you made your first save
- Git remembers everything!
- Like looking at your photo album

---

## Exercise 2: Making Changes and Tracking Progress

### What We'll Do
Add more content to your journal and see how Git tracks changes.

### Step-by-Step Instructions

**Step 1: Add More Content**
```bash
# Add a new section to your README:
echo "" >> README.md
echo "## What I Learned Today" >> README.md
echo "" >> README.md
echo "- Git helps track changes in my code" >> README.md
echo "- I can always go back to previous versions" >> README.md
echo "- This is like having a super-smart backup system!" >> README.md
```

**What This Does:**
- Adds new lines to your README.md file
- Like writing more pages in your notebook

**Step 2: Check What Changed**
```bash
git status
```

**What You Should See:**
```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
```

**What This Means:**
- Git knows you changed the file
- But you haven't saved the changes yet
- Like editing a photo but not printing the new version

**Step 3: See Exactly What Changed**
```bash
git diff
```

**What You Should See:**
```
diff --git a/README.md b/README.md
index 1234567..abcdefg 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,6 @@
 # My codingGita Learning Journey
+
+## What I Learned Today
+
+- Git helps track changes in my code
+- I can always go back to previous versions
+- This is like having a super-smart backup system!
```

**What This Means:**
- `+` shows new lines added
- Git shows you exactly what changed
- Like seeing before/after photos

**Step 4: Save Your Changes**
```bash
git add README.md
git commit -m "Added today's learning notes"
```

**Step 5: View Your Complete History**
```bash
git log --oneline
```

**What You Should See:**
```
def5678 Added today's learning notes
abc1234 Created my codingGita learning journal
```

**What This Means:**
- You now have two saved versions
- Each with a unique ID
- Like having two photos in your album

---

## Exercise 3: Working with Multiple Files

### What We'll Do
Create different types of files and organize them properly.

### Step-by-Step Instructions

**Step 1: Create a CSS File**
```bash
# Create a styles file:
echo "/* My codingGita Project Styles */" > style.css
echo "" >> style.css
echo "body {" >> style.css
echo "    font-family: Arial, sans-serif;" >> style.css
echo "    background-color: #f0f0f0;" >> style.css
echo "}" >> style.css
```

**Step 2: Create a JavaScript File**
```bash
# Create a script file:
echo "// My codingGita Project Scripts" > script.js
echo "" >> script.js
echo "function sayHello() {" >> script.js
echo "    console.log('Hello from codingGita!');" >> script.js
echo "}" >> script.js
```

**Step 3: Check Status**
```bash
git status
```

**What You Should See:**
```
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        script.js
        style.css
```

**Step 4: Add All Files at Once**
```bash
git add .
```

**What This Does:**
- Adds all new and changed files
- Like selecting all your photos for printing

**Step 5: Save Everything**
```bash
git commit -m "Added CSS and JavaScript files for codingGita project"
```

**Step 6: View Your Project Structure**
```bash
# On Windows:
dir

# On macOS/Linux:
ls -la
```

**What You Should See:**
```
README.md
script.js
style.css
.git/ (hidden folder)
```

---

## Exercise 4: Understanding File States

### What We'll Do
See how files move through different states in Git.

### Step-by-Step Instructions

**Step 1: Modify Multiple Files**
```bash
# Change README.md:
echo "" >> README.md
echo "## Project Files" >> README.md
echo "- README.md: Project documentation" >> README.md
echo "- style.css: Project styling" >> README.md
echo "- script.js: Project functionality" >> README.md

# Change style.css:
echo "" >> style.css
echo ".header {" >> style.css
echo "    color: blue;" >> style.css
echo "}" >> style.css

# Change script.js:
echo "" >> script.js
echo "function showProjectInfo() {" >> script.js
echo "    alert('Welcome to codingGita!');" >> script.js
echo "}" >> script.js
```

**Step 2: Check Status**
```bash
git status
```

**What You Should See:**
```
On branch main
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md
        modified:   style.css
        modified:   script.js
```

**Step 3: Stage Only Some Files**
```bash
git add README.md style.css
```

**Step 4: Check Status Again**
```bash
git status
```

**What You Should See:**
```
On branch main
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        modified:   README.md
        modified:   style.css

Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   script.js
```

**What This Means:**
- README.md and style.css are ready to save
- script.js still needs to be staged
- Like having some photos ready for printing, others still being edited

**Step 5: Stage the Remaining File**
```bash
git add script.js
```

**Step 6: Save Everything**
```bash
git commit -m "Updated project documentation and added new features"
```

---

## Exercise 5: Viewing History and Understanding Changes

### What We'll Do
Learn how to explore your project's history and understand what changed when.

### Step-by-Step Instructions

**Step 1: View Complete History**
```bash
git log
```

**What You Should See:**
```
commit ghi9012 (HEAD -> main)
Author: Your Name <your.email@college.edu>
Date:   [Current Date and Time]

    Updated project documentation and added new features

commit def5678
Author: Your Name <your.email@college.edu>
Date:   [Previous Date and Time]

    Added today's learning notes

commit abc1234
Author: Your Name <your.email@college.edu>
Date:   [Previous Date and Time]

    Created my codingGita learning journal
```

**Step 2: View Compact History**
```bash
git log --oneline
```

**What You Should See:**
```
ghi9012 Updated project documentation and added new features
def5678 Added today's learning notes
abc1234 Created my codingGita learning journal
```

**Step 3: See What Changed in the Last Commit**
```bash
git show HEAD
```

**What This Shows:**
- The exact changes in your most recent save
- Who made the changes
- When they were made

**Step 4: Compare Two Commits**
```bash
git diff abc1234..def5678
```

**What This Shows:**
- All changes between your first and second commits
- Like seeing the difference between two photos

---

## Exercise 6: Creating a Real Project Structure

### What We'll Do
Organize your codingGita project like a professional developer would.

### Step-by-Step Instructions

**Step 1: Create Organized Folders**
```bash
# Create folders for different types of files:
mkdir css
mkdir js
mkdir images
mkdir docs
```

**Step 2: Move Files to Appropriate Folders**
```bash
# Move CSS file:
git mv style.css css/

# Move JavaScript file:
git mv script.js js/

# Move README to docs:
git mv README.md docs/
```

**Step 3: Create New README in Root**
```bash
echo "# codingGita Project" > README.md
echo "" >> README.md
echo "A learning project to understand Git and version control." >> README.md
echo "" >> README.md
echo "## Project Structure" >> README.md
echo "- css/: Styling files" >> README.md
echo "- js/: JavaScript files" >> README.md
echo "- images/: Project images" >> README.md
echo "- docs/: Project documentation" >> README.md
```

**Step 4: Check Status**
```bash
git status
```

**Step 5: Save the New Structure**
```bash
git add .
git commit -m "Reorganized project structure for better organization"
```

**Step 6: View Final Structure**
```bash
# On Windows:
tree /f

# On macOS/Linux:
tree
```

**What You Should See:**
```
codingGita-journal/
├── README.md
├── css/
│   └── style.css
├── js/
│   └── script.js
├── images/
├── docs/
│   └── README.md
└── .git/
```

---

## Practice Challenges

### Challenge 1: Daily Journal Entries
- Add a new entry to your journal every day
- Commit each entry with a descriptive message
- Use `git log` to see your learning progress

### Challenge 2: Experiment with Changes
- Make changes to your CSS file
- See how `git diff` shows the changes
- Practice staging and committing files

### Challenge 3: Project Documentation
- Create a detailed project description
- Add installation instructions
- Commit each section separately

### Challenge 4: Multiple Features
- Work on different features in separate commits
- Use meaningful commit messages
- Practice viewing your work history

---

## Common Mistakes and How to Fix Them

### Mistake 1: Forgetting to Stage Files
**Problem:** You commit but your changes aren't saved
```bash
# Wrong way:
git commit -m "Added new feature"

# Right way:
git add filename.txt
git commit -m "Added new feature"
```

### Mistake 2: Vague Commit Messages
**Problem:** You can't remember what each commit did
```bash
# Wrong way:
git commit -m "stuff"

# Right way:
git commit -m "Added user login functionality to codingGita app"
```

### Mistake 3: Not Checking Status
**Problem:** You're confused about what's happening
```bash
# Always check status before committing:
git status
```

### Mistake 4: Committing Too Many Changes at Once
**Problem:** Your commits are too big to understand
```bash
# Better: Make smaller, focused commits:
git add feature1.txt
git commit -m "Added user authentication"

git add feature2.txt
git commit -m "Added password validation"
```

---

## Summary of What You've Learned

**✅ Basic Git Workflow:**
1. Make changes to files
2. Check status with `git status`
3. Stage files with `git add`
4. Save changes with `git commit`
5. View history with `git log`

**✅ File Organization:**
- Create meaningful folder structures
- Keep related files together
- Use descriptive names

**✅ Best Practices:**
- Commit frequently with clear messages
- Check status before committing
- Organize your project logically

**✅ Real-World Application:**
- Use Git for all your codingGita projects
- Track your learning progress
- Build a portfolio of your work

---

## Next Steps

**What to Practice:**
- Use Git for your next codingGita assignment
- Create a daily learning journal
- Experiment with different project structures

**What to Learn Next:**
- Working with remote repositories (GitHub)
- Branching and merging
- Collaborating with others

**Remember:**
Git is a tool that gets easier with practice. Start small, make mistakes, and learn from them. Every professional developer started exactly where you are now!

**Your codingGita Journey:**
You're now ready to use Git in your real projects. Every commit you make is a step forward in your coding journey. Keep practicing, keep learning, and keep committing your progress!

