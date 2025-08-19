# Assignment 3: Branching Basics

## 🎯 Assignment Overview

**Goal:** Master the fundamentals of Git branching by creating, switching between, and working with multiple branches simultaneously.

**Duration:** 60-75 minutes
**Difficulty:** Beginner to Intermediate
**Prerequisites:** Assignment 2 completion, understanding of basic Git commands

---

## 📚 What You'll Learn

By completing this assignment, you will:
- ✅ Create and manage multiple branches
- ✅ Switch between branches seamlessly
- ✅ Understand branch isolation
- ✅ Work on different features simultaneously
- ✅ Practice proper branch naming conventions
- ✅ Build confidence with branching workflows

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

### Step 2: Create Your First Feature Branch

```bash
# Create and switch to a new feature branch
git checkout -b feature/portfolio-website

# Verify you're on the new branch
git branch --show-current

# Should show: feature/portfolio-website

# Check all branches
git branch

# Should show both main and feature/portfolio-website
```

### Step 3: Work on Portfolio Website

```bash
# Create the main portfolio HTML file
echo "<!DOCTYPE html>" > src/portfolio.html
echo "<html lang=\"en\">" >> src/portfolio.html
echo "<head>" >> src/portfolio.html
echo "    <meta charset=\"UTF-8\">" >> src/portfolio.html
echo "    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">" >> src/portfolio.html
echo "    <title>My codingGita Portfolio</title>" >> src/portfolio.html
echo "    <link rel=\"stylesheet\" href=\"../css/portfolio.css\">" >> src/portfolio.html
echo "</head>" >> src/portfolio.html
echo "<body>" >> src/portfolio.html
echo "    <header>" >> src/portfolio.html
echo "        <h1>Welcome to My Portfolio</h1>" >> src/portfolio.html
echo "        <nav>" >> src/portfolio.html
echo "            <ul>" >> src/portfolio.html
echo "                <li><a href=\"#about\">About</a></li>" >> src/portfolio.html
echo "                <li><a href=\"#projects\">Projects</a></li>" >> src/portfolio.html
echo "                <li><a href=\"#contact\">Contact</a></li>" >> src/portfolio.html
echo "            </ul>" >> src/portfolio.html
echo "        </nav>" >> src/portfolio.html
echo "    </header>" >> src/portfolio.html
echo "    <main>" >> src/portfolio.html
echo "        <section id=\"about\">" >> src/portfolio.html
echo "            <h2>About Me</h2>" >> src/portfolio.html
echo "            <p>I'm a first-year student at codingGita College learning web development.</p>" >> src/portfolio.html
echo "        </section>" >> src/portfolio.html
echo "    </main>" >> src/portfolio.html
echo "    <script src=\"../js/portfolio.js\"></script>" >> src/portfolio.html
echo "</body>" >> src/portfolio.html
echo "</html>" >> src/portfolio.html
```

### Step 4: Commit Portfolio Changes

```bash
# Add the portfolio HTML file
git add src/portfolio.html

# Commit with descriptive message
git commit -m "feat: create portfolio website structure

- Add HTML5 boilerplate with semantic elements
- Include navigation menu with anchor links
- Create about section for personal information
- Link to CSS and JavaScript files
- Follow accessibility best practices"
```

### Step 5: Switch to Main Branch

```bash
# Switch back to main branch
git checkout main

# Verify you're on main
git branch --show-current

# Should show: main

# Check what files exist here
ls src/

# Should show: calculator.html (portfolio.html is only in feature branch)
```

### Step 6: Create Another Feature Branch

```bash
# Create a new feature branch for a different project
git checkout -b feature/weather-app

# Verify you're on the new branch
git branch --show-current

# Should show: feature/weather-app

# Check all branches
git branch

# Should show: main, feature/portfolio-website, feature/weather-app
```

### Step 7: Work on Weather App

```bash
# Create the weather app HTML file
echo "<!DOCTYPE html>" > src/weather.html
echo "<html lang=\"en\">" >> src/weather.html
echo "<head>" >> src/weather.html
echo "    <meta charset=\"UTF-8\">" >> src/weather.html
echo "    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">" >> src/weather.html
echo "    <title>codingGita Weather App</title>" >> src/weather.html
echo "    <link rel=\"stylesheet\" href=\"../css/weather.css\">" >> src/weather.html
echo "</head>" >> src/weather.html
echo "<body>" >> src/weather.html
echo "    <div class=\"weather-container\">" >> src/weather.html
echo "        <h1>Weather App</h1>" >> src/weather.html
echo "        <div class=\"search-box\">" >> src/weather.html
echo "            <input type=\"text\" id=\"city-input\" placeholder=\"Enter city name\">" >> src/weather.html
echo "            <button onclick=\"getWeather()\">Search</button>" >> src/weather.html
echo "        </div>" >> src/weather.html
echo "        <div class=\"weather-info\" id=\"weather-info\">" >> src/weather.html
echo "            <p>Enter a city to see the weather</p>" >> src/weather.html
echo "        </div>" >> src/weather.html
echo "    </div>" >> src/weather.html
echo "    <script src=\"../js/weather.js\"></script>" >> src/weather.html
echo "</body>" >> src/weather.html
echo "</html>" >> src/weather.html
```

### Step 8: Commit Weather App Changes

```bash
# Add the weather HTML file
git add src/weather.html

# Commit with descriptive message
git commit -m "feat: create weather app interface

- Design clean weather app layout
- Include city search functionality
- Add weather information display area
- Implement responsive design principles
- Prepare for JavaScript weather API integration"
```

### Step 9: Switch Between Branches

```bash
# Switch to portfolio branch
git checkout feature/portfolio-website

# Verify you're on portfolio branch
git branch --show-current

# Check what files exist here
ls src/

# Should show: calculator.html, portfolio.html

# Switch to weather app branch
git checkout feature/weather-app

# Check files here
ls src/

# Should show: calculator.html, weather.html

# Switch back to main
git checkout main

# Check files on main
ls src/

# Should show: calculator.html only
```

### Step 10: Add CSS to Portfolio Branch

```bash
# Switch to portfolio branch
git checkout feature/portfolio-website

# Create portfolio CSS file
echo "/* Portfolio Styles */" > css/portfolio.css
echo "body {" >> css/portfolio.css
echo "    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;" >> css/portfolio.css
echo "    margin: 0;" >> css/portfolio.css
echo "    padding: 0;" >> css/portfolio.css
echo "    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);" >> css/portfolio.css
echo "    color: white;" >> css/portfolio.css
echo "}" >> css/portfolio.css
echo "" >> css/portfolio.css
echo "header {" >> css/portfolio.css
echo "    background: rgba(255, 255, 255, 0.1);" >> css/portfolio.css
echo "    backdrop-filter: blur(10px);" >> css/portfolio.css
echo "    padding: 20px 0;" >> css/portfolio.css
echo "    text-align: center;" >> css/portfolio.css
echo "}" >> css/portfolio.css
echo "" >> css/portfolio.css
echo "nav ul {" >> css/portfolio.css
echo "    list-style: none;" >> css/portfolio.css
echo "    padding: 0;" >> css/portfolio.css
echo "    display: flex;" >> css/portfolio.css
echo "    justify-content: center;" >> css/portfolio.css
echo "    gap: 30px;" >> css/portfolio.css
echo "}" >> css/portfolio.css
echo "" >> css/portfolio.css
echo "nav a {" >> css/portfolio.css
echo "    color: white;" >> css/portfolio.css
echo "    text-decoration: none;" >> css/portfolio.css
echo "    font-weight: 500;" >> css/portfolio.css
echo "    transition: color 0.3s ease;" >> css/portfolio.css
echo "}" >> css/portfolio.css
echo "" >> css/portfolio.css
echo "nav a:hover {" >> css/portfolio.css
echo "    color: #ffd700;" >> css/portfolio.css
echo "}" >> css/portfolio.css
```

### Step 11: Commit Portfolio CSS

```bash
# Add portfolio CSS
git add css/portfolio.css

# Commit with descriptive message
git commit -m "style: add modern portfolio styling

- Implement gradient background with glassmorphism effect
- Add smooth hover animations for navigation
- Use modern typography and spacing
- Include responsive design considerations
- Create professional portfolio appearance"
```

### Step 12: Add CSS to Weather App Branch

```bash
# Switch to weather app branch
git checkout feature/weather-app

# Create weather CSS file
echo "/* Weather App Styles */" > css/weather.css
echo "body {" >> css/weather.css
echo "    font-family: 'Arial', sans-serif;" >> css/weather.css
echo "    margin: 0;" >> css/weather.css
echo "    padding: 0;" >> css/weather.css
echo "    background: linear-gradient(45deg, #74b9ff, #0984e3);" >> css/weather.css
echo "    min-height: 100vh;" >> css/weather.css
echo "    display: flex;" >> css/weather.css
echo "    justify-content: center;" >> css/weather.css
echo "    align-items: center;" >> css/weather.css
echo "}" >> css/weather.css
echo "" >> css/weather.css
echo ".weather-container {" >> css/weather.css
echo "    background: rgba(255, 255, 255, 0.95);" >> css/weather.css
echo "    padding: 40px;" >> css/weather.css
echo "    border-radius: 20px;" >> css/weather.css
echo "    box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);" >> css/weather.css
echo "    text-align: center;" >> css/weather.css
echo "    color: #2d3436;" >> css/weather.css
echo "}" >> css/weather.css
echo "" >> css/weather.css
echo ".search-box {" >> css/weather.css
echo "    margin: 20px 0;" >> css/weather.css
echo "}" >> css/weather.css
echo "" >> css/weather.css
echo "#city-input {" >> css/weather.css
echo "    padding: 12px 20px;" >> css/weather.css
echo "    border: 2px solid #ddd;" >> css/weather.css
echo "    border-radius: 25px;" >> css/weather.css
echo "    font-size: 16px;" >> css/weather.css
echo "    margin-right: 10px;" >> css/weather.css
echo "    outline: none;" >> css/weather.css
echo "}" >> css/weather.css
echo "" >> css/weather.css
echo "button {" >> css/weather.css
echo "    padding: 12px 25px;" >> css/weather.css
echo "    background: #00b894;" >> css/weather.css
echo "    color: white;" >> css/weather.css
echo "    border: none;" >> css/weather.css
echo "    border-radius: 25px;" >> css/weather.css
echo "    font-size: 16px;" >> css/weather.css
echo "    cursor: pointer;" >> css/weather.css
echo "    transition: background 0.3s ease;" >> css/weather.css
echo "}" >> css/weather.css
echo "" >> css/weather.css
echo "button:hover {" >> css/weather.css
echo "    background: #00a085;" >> css/weather.css
echo "}" >> css/weather.css
```

### Step 13: Commit Weather App CSS

```bash
# Add weather CSS
git add css/weather.css

# Commit with descriptive message
git commit -m "style: add weather app interface styling

- Create modern card-based design with shadows
- Implement gradient background for visual appeal
- Add smooth transitions and hover effects
- Design responsive search interface
- Use consistent color scheme and typography"
```

### Step 14: View Branch Structure

```bash
# Switch to main branch
git checkout main

# View all branches with graph
git log --graph --oneline --all

# This will show the branching structure
```

### Step 15: Push All Branches to GitHub

```bash
# Push main branch
git push origin main

# Push portfolio branch
git checkout feature/portfolio-website
git push -u origin feature/portfolio-website

# Push weather app branch
git checkout feature/weather-app
git push -u origin feature/weather-app

# Switch back to main
git checkout main
```

---

## 🧪 Testing Your Branches

### Test 1: Branch Switching
```bash
# Test switching between all branches
git checkout main
git checkout feature/portfolio-website
git checkout feature/weather-app
git checkout main

# Each switch should work smoothly
```

### Test 2: File Isolation
```bash
# Check files on each branch
git checkout main
ls src/  # Should show: calculator.html

git checkout feature/portfolio-website
ls src/  # Should show: calculator.html, portfolio.html

git checkout feature/weather-app
ls src/  # Should show: calculator.html, weather.html
```

### Test 3: Branch Information
```bash
# View all branches
git branch -a

# Should show local and remote branches
```

---

## 📋 Assignment Checklist

- [ ] Portfolio feature branch created
- [ ] Weather app feature branch created
- [ ] HTML files created in respective branches
- [ ] CSS styling added to both branches
- [ ] All changes committed with good messages
- [ ] Branches pushed to GitHub
- [ ] Branch switching tested
- [ ] File isolation verified

---

## 🎯 Success Criteria

**Your assignment is complete when:**
- ✅ Three branches exist: main, feature/portfolio-website, feature/weather-app
- ✅ Each branch has its own unique files
- ✅ Files are properly isolated between branches
- ✅ All commits have meaningful messages
- ✅ Branches are pushed to GitHub
- ✅ You can switch between branches smoothly

---

## 🌿 Branch Management Best Practices

### 1. **Naming Conventions**
```bash
# Use descriptive names
feature/user-authentication
feature/calculator-app
feature/portfolio-website

# Avoid generic names
feature/new
feature/stuff
feature/update
```

### 2. **Branch Organization**
```bash
# Keep main branch clean
# Work on features in separate branches
# Use consistent naming patterns
# Delete branches after merging
```

### 3. **Workflow Tips**
```bash
# Always check which branch you're on
git branch --show-current

# Switch branches frequently
git checkout branch-name

# Keep branches focused on single features
# Don't mix different types of work
```

---

## 🆘 Troubleshooting

### Problem: Can't switch branches
```bash
# Check if you have uncommitted changes
git status

# Commit or stash changes first
git add .
git commit -m "Save work before switching branches"
```

### Problem: Files not showing in branch
```bash
# Make sure you're on the right branch
git branch --show-current

# Check if files were committed
git log --oneline
```

### Problem: Branch not pushing to GitHub
```bash
# Set upstream for new branches
git push -u origin branch-name

# Check remote connections
git remote -v
```

---

## 🚀 Next Steps

After completing this assignment:
1. **Review your branch structure** on GitHub
2. **Practice switching between branches** regularly
3. **Move to Assignment 4:** Merge Practice
4. **Start using branches** for all new features

---

## 💡 Bonus Challenges

### Challenge 1: More Feature Branches
- Create a `feature/contact-form` branch
- Add a `feature/blog-section` branch
- Experiment with different project types

### Challenge 2: Branch Organization
- Create a `develop` branch for integration
- Set up branch protection rules
- Use branch descriptions on GitHub

### Challenge 3: Advanced Branching
- Create branches from other branches
- Experiment with branch renaming
- Practice branch deletion

---

## 🎓 Learning Reflection

**After completing this assignment, ask yourself:**
- How does branching help organize your work?
- What are the benefits of working in separate branches?
- How does this improve collaboration?
- What would you do differently with branching?

---

## 🔗 Related Resources

- **Topic Notes:** [Understanding Branching and Merging](../notes/04-branching-merging.md)
- **GitHub Guide:** [Managing Branches](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/managing-branches-in-your-repository)
- **Git Branching:** [Git Documentation](https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell)

---

**Excellent work on mastering Git branching! 🌿**

You're now ready to handle complex projects with multiple features and collaborators!
