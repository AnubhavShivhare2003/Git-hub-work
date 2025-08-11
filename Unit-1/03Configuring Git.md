# ⚙️ Configuring Git – CodingGita Guide  
*A beginner‑friendly setup tutorial for Git*  

---

## 📍 Why Configure Git?  
Git needs to know **who you are** so it can record your changes properly.  
If you skip this, Git won’t know who made the commits — like getting an unsigned note in your hostel room!

---

## 🛠 Step 1 – Set Your Username  
git config --global user.name "Your Name"

text
**Example:**  
git config --global user.name "Aman Sharma - CodingGita"

text

---

## 📧 Step 2 – Set Your Email  
git config --global user.email "youremail@example.com"

text
**Example:**  
git config --global user.email "aman.codinggita@gmail.com"

text

---

## 🔍 Step 3 – Check Your Settings  
git config --list

text
**Expected Output:**  
user.name=Aman Sharma - CodingGita
user.email=aman.codinggita@gmail.com

text

---

## 📝 Step 4 – Change the Default Editor *(Optional)*  
- **VS Code:**  
git config --global core.editor "code --wait"

text
- **Notepad (Windows):**  
git config --global core.editor notepad

text

---

## 🎨 Step 5 – Enable Color Output *(Optional)*  
git config --global color.ui auto

text

---

## 💡 Hostel Analogy  
Inside the **CodingGita hostel**:  
If you don’t configure Git, it’s like finding an open milk carton in the fridge —  
everyone blames each other, but no one knows who did it! 😅

With configuration, Git can show:  
- **Aman Sharma** → Added a feature  
- **Priya Singh** → Fixed a bug  
- **Rohit Kumar** → Broke something 🤭  

---

## 🎥 Recommended Learning  
- *How to Configure Git* – Corey Schafer  
- *Git Configuration for Beginners* – ProgrammingKnowledge  
- *Git Basics in Hindi* – CodeWithHarry  

*(Search these titles on YouTube — or add clickable links if you like)*

---

## ✅ Quick Summary Table  

| Step | Command | Purpose |
|------|---------|---------|
| 1 | `git config --global user.name "Your Name"` | Set username |
| 2 | `git config --global user.email "you@example.com"` | Set email |
| 3 | `git config --list` | Check settings |
| 4 | `git config --global core.editor "code --wait"` | Set default editor |
| 5 | `git config --global color.ui auto` | Enable colors |

---

**📢 Next Up:** Learn `git init`, `git clone`, `git status`, `git add`, `git commit`, and `git log`.

---
