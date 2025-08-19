# Assignment 1: Repository Setup

## 🎯 Assignment Overview

**Goal:** Create your first professional repository and set up a proper project structure for your codingGita learning journey.

**Duration:** 30-45 minutes
**Difficulty:** Beginner
**Prerequisites:** Unit 1 completion, Git installed, GitHub account

---

## 📚 What You'll Learn

By completing this assignment, you will:
- ✅ Create a local Git repository
- ✅ Set up a proper project structure
- ✅ Create a professional README file
- ✅ Connect your local repository to GitHub
- ✅ Make your first commit and push
- ✅ Understand repository organization

---

## 🚀 Step-by-Step Instructions

### Step 1: Create Your Project Folder

```bash
# Navigate to your desktop or preferred location
cd C:\Users\YourName\Desktop

# Create a new folder for your project
mkdir codinggita-learning-journal

# Enter the folder
cd codinggita-learning-journal
```

### Step 2: Initialize Git Repository

```bash
# Initialize Git in your folder
git init

# Verify Git is initialized
git status
```

**Expected Output:**
```
On branch main
No commits yet
nothing to commit (working tree clean)
```

### Step 3: Create Project Structure

```bash
# Create the main project folders
mkdir src
mkdir docs
mkdir images
mkdir css
mkdir js

# Create initial files
echo "# codingGita Learning Journal" > README.md
echo "/* Main stylesheet */" > css/style.css
echo "// Main JavaScript file" > js/script.js
echo "# Project Documentation" > docs/README.md
```

### Step 4: Create a Professional README

Open `README.md` in your text editor and replace the content with:

```markdown
# codingGita Learning Journal

## 📚 About This Project

Welcome to my codingGita learning journey! This repository tracks my progress through the codingGita curriculum, showcasing my projects, assignments, and learning milestones.

## 🎯 Learning Goals

- Master Git and version control
- Build a portfolio of coding projects
- Develop practical web development skills
- Collaborate with classmates on GitHub
- Prepare for future career opportunities

## 🚀 Projects

### Unit 1: Introduction to Version Control and Git
- [x] Basic Git commands
- [x] Understanding Git workflow
- [x] First repository setup

### Unit 2: Working with Repositories
- [ ] Repository management
- [ ] Branching and merging
- [ ] Conflict resolution
- [ ] GitHub collaboration

## 🛠️ Technologies Used

- HTML5
- CSS3
- JavaScript
- Git & GitHub
- VS Code

## 📁 Project Structure

```
codinggita-learning-journal/
├── README.md          # This file
├── css/               # Stylesheets
│   └── style.css
├── js/                # JavaScript files
│   └── script.js
├── docs/              # Documentation
│   └── README.md
├── images/            # Project images
└── src/               # Source code
```

## 🎓 About Me

**Student:** [Your Name]
**College:** codingGita College
**Program:** [Your Program]
**Year:** First Year
**Email:** [Your Email]

## 📖 How to Use This Repository

1. Clone the repository: `git clone [repository-url]`
2. Navigate to the project: `cd codinggita-learning-journal`
3. Open in your favorite editor
4. Explore the different projects and assignments

## 🤝 Contributing

This is a personal learning repository, but feedback and suggestions are welcome!

## 📄 License

This project is for educational purposes as part of the codingGita curriculum.

---

**Last Updated:** [Today's Date]
**Git Version:** [Your Git version]
```

### Step 5: Make Your First Commit

```bash
# Check what files are ready to commit
git status

# Add all files to staging
git add .

# Make your first commit
git commit -m "feat: initialize codingGita learning journal repository

- Create project structure with organized folders
- Add professional README with learning goals
- Set up basic CSS and JavaScript files
- Document project organization and purpose"
```

### Step 6: Create GitHub Repository

1. **Go to GitHub.com** and sign in
2. **Click the "+" icon** in the top right
3. **Select "New repository"**
4. **Fill in the details:**
   - **Repository name:** `codinggita-learning-journal`
   - **Description:** `My codingGita learning journey and portfolio`
   - **Visibility:** Public
   - **Initialize with:** Don't check any boxes (we'll push our existing code)
5. **Click "Create repository"**

### Step 7: Connect Local to GitHub

```bash
# Add the remote origin
git remote add origin https://github.com/YourUsername/codinggita-learning-journal.git

# Verify the remote is added
git remote -v

# Push your code to GitHub
git push -u origin main
```

### Step 8: Verify Everything Works

1. **Refresh your GitHub repository page**
2. **Check that all files are there**
3. **Verify the README displays properly**
4. **Check the commit history**

---

## 🧪 Testing Your Setup

### Test 1: Local Repository
```bash
# Check Git status
git status

# Should show: "working tree clean"
```

### Test 2: Remote Connection
```bash
# Check remote connections
git remote -v

# Should show your GitHub URL
```

### Test 3: File Structure
```bash
# List all files and folders
dir

# Should show: README.md, css/, js/, docs/, images/, src/
```

---

## 📋 Assignment Checklist

- [ ] Project folder created
- [ ] Git repository initialized
- [ ] Project structure created
- [ ] Professional README written
- [ ] First commit made
- [ ] GitHub repository created
- [ ] Local connected to remote
- [ ] Code pushed to GitHub
- [ ] Repository verified on GitHub

---

## 🎯 Success Criteria

**Your assignment is complete when:**
- ✅ Repository is properly organized
- ✅ README is professional and informative
- ✅ All files are committed and pushed
- ✅ Repository is accessible on GitHub
- ✅ Project structure follows best practices

---

## 🆘 Troubleshooting

### Problem: Git not initialized
```bash
# Solution: Make sure you're in the right folder
pwd  # Check current directory
git init  # Initialize Git
```

### Problem: Remote connection failed
```bash
# Solution: Check your GitHub URL
git remote -v
git remote remove origin
git remote add origin https://github.com/YourUsername/repository-name.git
```

### Problem: Push failed
```bash
# Solution: Check if you're authenticated
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

---

## 🚀 Next Steps

After completing this assignment:
1. **Take a screenshot** of your GitHub repository
2. **Share your repository URL** with classmates
3. **Move to Assignment 2:** Commit Practice
4. **Start building your portfolio!**

---

## 💡 Bonus Challenges

### Challenge 1: Enhanced README
- Add a profile picture
- Include social media links
- Add a skills progress bar
- Include project screenshots

### Challenge 2: Project Templates
- Create template files for future projects
- Add a `.gitignore` file
- Set up branch protection rules
- Add issue templates

### Challenge 3: Documentation
- Create a contributing guide
- Add a changelog
- Document your learning process
- Create project roadmaps

---

## 🎓 Learning Reflection

**After completing this assignment, ask yourself:**
- What did you learn about repository organization?
- How does this structure help with project management?
- What would you do differently next time?
- How will this help with future projects?

---

## 🔗 Related Resources

- **Topic Notes:** [Creating and Cloning Repositories](../notes/01-repositories-cloning.md)
- **GitHub Guide:** [Creating a New Repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository)
- **Markdown Guide:** [Basic Syntax](https://www.markdownguide.org/basic-syntax/)

---

**Congratulations on setting up your first repository! 🎉**

You're now ready to start building your codingGita portfolio and learning journey!
