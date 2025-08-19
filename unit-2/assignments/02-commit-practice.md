# Assignment 2: Commit Practice

## 🎯 Assignment Overview

**Goal:** Master the art of writing meaningful commit messages and creating a clear project timeline through proper commits.

**Duration:** 45-60 minutes
**Difficulty:** Beginner
**Prerequisites:** Assignment 1 completion, basic Git knowledge

---

## 📚 What You'll Learn

By completing this assignment, you will:
- ✅ Write clear, descriptive commit messages
- ✅ Use conventional commit format
- ✅ Create a meaningful project timeline
- ✅ Understand commit organization
- ✅ Practice good Git habits
- ✅ Build a professional commit history

---

## 🚀 Step-by-Step Instructions

### Step 1: Prepare Your Repository

```bash
# Make sure you're in your learning journal repository
cd codinggita-learning-journal

# Check current status
git status

# Should show: "working tree clean"
```

### Step 2: Create Your First Project File

Let's create a simple calculator project to practice commits:

```bash
# Create the main HTML file
echo "<!DOCTYPE html>" > src/calculator.html
echo "<html lang=\"en\">" >> src/calculator.html
echo "<head>" >> src/calculator.html
echo "    <meta charset=\"UTF-8\">" >> src/calculator.html
echo "    <meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0\">" >> src/calculator.html
echo "    <title>codingGita Calculator</title>" >> src/calculator.html
echo "    <link rel=\"stylesheet\" href=\"../css/calculator.css\">" >> src/calculator.html
echo "</head>" >> src/calculator.html
echo "<body>" >> src/calculator.html
echo "    <h1>codingGita Calculator</h1>" >> src/calculator.html
echo "    <div class=\"calculator\">" >> src/calculator.html
echo "        <input type=\"text\" id=\"display\" readonly>" >> src/calculator.html
echo "        <div class=\"buttons\">" >> src/calculator.html
echo "            <button onclick=\"clearDisplay()\">C</button>" >> src/calculator.html
echo "            <button onclick=\"appendNumber('7')\">7</button>" >> src/calculator.html
echo "            <button onclick=\"appendNumber('8')\">8</button>" >> src/calculator.html
echo "            <button onclick=\"appendNumber('9')\">9</button>" >> src/calculator.html
echo "        </div>" >> src/calculator.html
echo "    </div>" >> src/calculator.html
echo "    <script src=\"../js/calculator.js\"></script>" >> src/calculator.html
echo "</body>" >> src/calculator.html
echo "</html>" >> src/calculator.html
```

### Step 3: Make Your First Commit

```bash
# Check what files are ready to commit
git status

# Add the new file
git add src/calculator.html

# Make your first commit with a good message
git commit -m "feat: create basic calculator HTML structure

- Add HTML5 boilerplate with proper meta tags
- Create calculator interface with display and buttons
- Link to CSS and JavaScript files
- Follow semantic HTML best practices"
```

### Step 4: Add CSS Styling

```bash
# Create the CSS file
echo "/* Calculator Styles */" > css/calculator.css
echo "body {" >> css/calculator.css
echo "    font-family: Arial, sans-serif;" >> css/calculator.css
echo "    display: flex;" >> css/calculator.css
echo "    justify-content: center;" >> css/calculator.css
echo "    align-items: center;" >> css/calculator.css
echo "    min-height: 100vh;" >> css/calculator.css
echo "    margin: 0;" >> css/calculator.css
echo "    background-color: #f0f0f0;" >> css/calculator.css
echo "}" >> css/calculator.css
echo "" >> css/calculator.css
echo ".calculator {" >> css/calculator.css
echo "    background: white;" >> css/calculator.css
echo "    border-radius: 10px;" >> css/calculator.css
echo "    padding: 20px;" >> css/calculator.css
echo "    box-shadow: 0 4px 8px rgba(0,0,0,0.1);" >> css/calculator.css
echo "}" >> css/calculator.css
echo "" >> css/calculator.css
echo "#display {" >> css/calculator.css
echo "    width: 100%;" >> css/calculator.css
echo "    height: 50px;" >> css/calculator.css
echo "    margin-bottom: 20px;" >> css/calculator.css
echo "    font-size: 24px;" >> css/calculator.css
echo "    text-align: right;" >> css/calculator.css
echo "    border: 1px solid #ccc;" >> css/calculator.css
echo "    border-radius: 5px;" >> css/calculator.css
echo "    padding: 10px;" >> css/calculator.css
echo "}" >> css/calculator.css
echo "" >> css/calculator.css
echo ".buttons {" >> css/calculator.css
echo "    display: grid;" >> css/calculator.css
echo "    grid-template-columns: repeat(4, 1fr);" >> css/calculator.css
echo "    gap: 10px;" >> css/calculator.css
echo "}" >> css/calculator.css
echo "" >> css/calculator.css
echo "button {" >> css/calculator.css
echo "    padding: 15px;" >> css/calculator.css
echo "    font-size: 18px;" >> css/calculator.css
echo "    border: none;" >> css/calculator.css
echo "    border-radius: 5px;" >> css/calculator.css
echo "    background: #007bff;" >> css/calculator.css
echo "    color: white;" >> css/calculator.css
echo "    cursor: pointer;" >> css/calculator.css
echo "}" >> css/calculator.css
echo "" >> css/calculator.css
echo "button:hover {" >> css/calculator.css
echo "    background: #0056b3;" >> css/calculator.css
echo "}" >> css/calculator.css
```

### Step 5: Commit CSS Changes

```bash
# Add CSS file
git add css/calculator.css

# Commit with descriptive message
git commit -m "style: add calculator styling and layout

- Implement responsive grid layout for calculator buttons
- Add modern design with shadows and rounded corners
- Include hover effects for better user experience
- Use consistent color scheme and typography
- Ensure mobile-friendly responsive design"
```

### Step 6: Add JavaScript Functionality

```bash
# Create the JavaScript file
echo "// Calculator JavaScript Logic" > js/calculator.js
echo "" >> js/calculator.js
echo "let displayValue = '';" >> js/calculator.js
echo "" >> js/calculator.js
echo "function appendNumber(num) {" >> js/calculator.js
echo "    displayValue += num;" >> js/calculator.js
echo "    updateDisplay();" >> js/calculator.js
echo "}" >> js/calculator.js
echo "" >> js/calculator.js
echo "function clearDisplay() {" >> js/calculator.js
echo "    displayValue = '';" >> js/calculator.js
echo "    updateDisplay();" >> js/calculator.js
echo "}" >> js/calculator.js
echo "" >> js/calculator.js
echo "function updateDisplay() {" >> js/calculator.js
echo "    document.getElementById('display').value = displayValue;" >> js/calculator.js
echo "}" >> js/calculator.js
echo "" >> js/calculator.js
echo "// Initialize display" >> js/calculator.js
echo "updateDisplay();" >> js/calculator.js
```

### Step 7: Commit JavaScript Changes

```bash
# Add JavaScript file
git add js/calculator.js

# Commit with descriptive message
git commit -m "feat: implement basic calculator functionality

- Add number input functionality to calculator
- Implement clear display function
- Create display update mechanism
- Initialize calculator on page load
- Follow JavaScript best practices"
```

### Step 8: Add More Calculator Features

```bash
# Add more functionality to JavaScript
echo "" >> js/calculator.js
echo "function add() {" >> js/calculator.js
echo "    if (displayValue !== '') {" >> js/calculator.js
echo "        displayValue += ' + ';" >> js/calculator.js
echo "        updateDisplay();" >> js/calculator.js
echo "    }" >> js/calculator.js
echo "}" >> js/calculator.js
echo "" >> js/calculator.js
echo "function subtract() {" >> js/calculator.js
echo "    if (displayValue !== '') {" >> js/calculator.js
echo "        displayValue += ' - ';" >> js/calculator.js
echo "        updateDisplay();" >> js/calculator.js
echo "    }" >> js/calculator.js
echo "}" >> js/calculator.js
echo "" >> js/calculator.js
echo "function calculate() {" >> js/calculator.js
echo "    try {" >> js/calculator.js
echo "        displayValue = eval(displayValue).toString();" >> js/calculator.js
echo "        updateDisplay();" >> js/calculator.js
echo "    } catch (error) {" >> js/calculator.js
echo "        displayValue = 'Error';" >> js/calculator.js
echo "        updateDisplay();" >> js/calculator.js
echo "    }" >> js/calculator.js
echo "}" >> js/calculator.js
```

### Step 9: Commit Enhanced Functionality

```bash
# Add enhanced JavaScript
git add js/calculator.js

# Commit with descriptive message
git commit -m "feat: add arithmetic operations to calculator

- Implement addition and subtraction operations
- Add calculation function with error handling
- Include input validation for mathematical expressions
- Enhance user experience with mathematical operations
- Follow proper error handling practices"
```

### Step 10: Update HTML with New Buttons

```bash
# Add more buttons to HTML
echo "            <button onclick=\"add()\">+</button>" >> src/calculator.html
echo "            <button onclick=\"subtract()\">-</button>" >> src/calculator.html
echo "            <button onclick=\"calculate()\">=</button>" >> src/calculator.html
```

### Step 11: Commit HTML Updates

```bash
# Add updated HTML
git add src/calculator.html

# Commit with descriptive message
git commit -m "feat: add arithmetic operation buttons to calculator

- Include addition (+) button for calculations
- Add subtraction (-) button for calculations
- Implement equals (=) button for results
- Complete basic calculator interface
- Ensure all buttons are properly connected to functions"
```

### Step 12: Test Your Calculator

```bash
# Open the calculator in your browser
# Navigate to: file:///path/to/your/repository/src/calculator.html

# Test the functionality:
# 1. Click numbers
# 2. Try addition: 5 + 3 =
# 3. Try subtraction: 10 - 4 =
# 4. Test clear function
```

### Step 13: Final Commit and Push

```bash
# Check status
git status

# Should show: "working tree clean"

# Push all commits to GitHub
git push origin main
```

---

## 🧪 Testing Your Commits

### Test 1: Commit History
```bash
# View your commit history
git log --oneline

# Should show 5 commits with clear messages
```

### Test 2: Commit Details
```bash
# View detailed commit information
git show HEAD

# Should show your latest commit with changes
```

### Test 3: File Status
```bash
# Check file status
git status

# Should show: "working tree clean"
```

---

## 📋 Assignment Checklist

- [ ] Calculator HTML structure created
- [ ] CSS styling added
- [ ] JavaScript functionality implemented
- [ ] All commits have meaningful messages
- [ ] Conventional commit format used
- [ ] Calculator functionality tested
- [ ] All changes pushed to GitHub
- [ ] Commit history reviewed

---

## 🎯 Success Criteria

**Your assignment is complete when:**
- ✅ Calculator is fully functional
- ✅ All commits have clear, descriptive messages
- ✅ Conventional commit format is used consistently
- ✅ Project timeline shows logical development
- ✅ Code is properly organized and committed
- ✅ All changes are pushed to GitHub

---

## 🏷️ Commit Message Examples

### Good Commit Messages
```bash
git commit -m "feat: add user authentication system"
git commit -m "fix: resolve calculation error in calculator"
git commit -m "style: improve button hover effects"
git commit -m "docs: update README with installation steps"
git commit -m "test: add unit tests for calculator functions"
```

### Bad Commit Messages (Avoid These)
```bash
git commit -m "stuff"
git commit -m "fixed bug"
git commit -m "update"
git commit -m "work in progress"
git commit -m "changed things"
```

---

## 🆘 Troubleshooting

### Problem: Calculator not working
```bash
# Check file paths in HTML
# Ensure CSS and JS files are linked correctly
# Check browser console for errors
```

### Problem: Commit message too long
```bash
# Use shorter first line (under 50 characters)
# Add details in commit body
# Use conventional commit format
```

### Problem: Files not showing changes
```bash
# Check if files are added to staging
git add .
git status
```

---

## 🚀 Next Steps

After completing this assignment:
1. **Review your commit history** on GitHub
2. **Share your calculator** with classmates
3. **Move to Assignment 3:** Branching Basics
4. **Practice using conventional commits** in future projects

---

## 💡 Bonus Challenges

### Challenge 1: Enhanced Calculator
- Add multiplication and division
- Include decimal point functionality
- Add keyboard support
- Implement calculator history

### Challenge 2: Better Commit Messages
- Use more specific commit types
- Include issue references
- Add detailed commit bodies
- Use emojis in commit messages

### Challenge 3: Project Documentation
- Update README with calculator details
- Add usage instructions
- Include screenshots
- Document future improvements

---

## 🎓 Learning Reflection

**After completing this assignment, ask yourself:**
- How do good commit messages help with project understanding?
- What makes a commit message effective?
- How does this practice help with team collaboration?
- What would you improve in your commit messages?

---

## 🔗 Related Resources

- **Topic Notes:** [Understanding Commits and Commit Messages](../notes/02-commits-messages.md)
- **Conventional Commits:** [Specification](https://www.conventionalcommits.org/)
- **Git Commit Best Practices:** [GitHub Guide](https://github.com/readme/guides/writing-great-commit-messages)

---

**Great job on mastering commit messages! 🎉**

You're building a professional Git history that will impress future employers and collaborators!
