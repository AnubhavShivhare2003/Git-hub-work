# ⚙️ Configuring Git – CodingGita Hostel Guide  

Now that Git is installed on your laptop, the **next step** is to tell Git *who you are*.  
This is important because Git keeps a record of **who made each change** in a project.  

If you skip this step, Git will not know your identity, and your commits will look anonymous —  
like someone leaving a note under your hostel door without signing it!  

---

## 📌 Step 1: Setting Your Username  

This will appear in all your commits.  

```bash
git config --global user.name "Your Name"
💡 Example:

bash
Copy
Edit
git config --global user.name "Aman Sharma - CodingGita"
📌 Step 2: Setting Your Email
Git uses your email to link commits to you (and to your GitHub account).

bash
Copy
Edit
git config --global user.email "youremail@example.com"
💡 Example:

bash
Copy
Edit
git config --global user.email "aman.codinggita@gmail.com"
📌 Step 3: Checking Your Configuration
You can check if your username and email are set correctly:

bash
Copy
Edit
git config --list
You should see:

ini
Copy
Edit
user.name=Aman Sharma - CodingGita
user.email=aman.codinggita@gmail.com
📌 Step 4: Setting Your Default Editor (Optional)
By default, Git may open Vim when writing commit messages, which can be confusing for beginners.
You can change it to something easier, like Notepad or VS Code.

For VS Code:

bash
Copy
Edit
git config --global core.editor "code --wait"
For Notepad (Windows):

bash
Copy
Edit
git config --global core.editor notepad
📌 Step 5: Making Git Output Colorful (Optional)
Colored output makes it easier to read Git status and logs:

bash
Copy
Edit
git config --global color.ui auto
💡 Hostel Life Example – Why Configure Git?
Imagine you and your roommates at the CodingGita hostel are all editing the same project.
If Git doesn’t know who made which changes, it’s like finding an open milk carton in the fridge —
everyone blames each other, and no one knows who left it! 🥴

By setting your username and email, Git can clearly show:

Aman Sharma added a new feature

Priya Singh fixed a bug

Rohit Kumar broke something 😅

📺 YouTube Tutorials for Configuring Git
How to Configure Git (Corey Schafer)
🔗 https://www.youtube.com/watch?v=4ZtZ_nFutD8&t=350s

Git Configuration for Beginners (ProgrammingKnowledge)
🔗 https://www.youtube.com/watch?v=USjZcfj8yxE&t=450s

Git Basics: Setting Username & Email (CodeWithHarry - Hindi)
🔗 https://www.youtube.com/watch?v=Ez8F0nW6S-w&t=400s

📝 Summary
Set your username:

bash
Copy
Edit
git config --global user.name "Your Name"
Set your email:

bash
Copy
Edit
git config --global user.email "youremail@example.com"
Check your settings:

bash
Copy
Edit
git config --list
Optional: Set a better editor & enable color output.

Always configure Git before starting any project so your contributions are tracked properly.

💡 Next Step: We will now learn Basic Git Commands like init, clone, status, add, commit, and log.
