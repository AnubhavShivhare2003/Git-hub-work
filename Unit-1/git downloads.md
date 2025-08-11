# 🛠 Installing Git (Windows, macOS, Linux) – CodingGita Hostel Guide  

Before we start working on our hostel projects at **CodingGita**, we need to install **Git**.  
Git is our tool for tracking changes, working together without overwriting each other’s work, and keeping our hostel coding projects safe.  

This guide will walk you through installing Git on **Windows**, **macOS**, and **Linux**, step-by-step, along with **YouTube videos** for visual learners.  

---

## 📌 Step 1: Installing Git on Windows  

Windows does not have Git pre-installed, so we’ll download it.  

### 🖥 Installation Steps:  
1. Visit → [https://git-scm.com/](https://git-scm.com/)  
2. Click **"Download for Windows"** — the site will detect your OS version automatically.  
3. Run the downloaded `.exe` file.  
4. In the setup wizard:  
   - Accept the license agreement.  
   - Choose the default installation path.  
   - Keep default settings unless you have a specific reason to change them.  
   - Select **"Git from the command line and also from 3rd-party software"**.  
   - Click **Next** until you reach **Install**.  
5. Wait for the installation to complete.  
6. Open **Command Prompt** or **Git Bash** and type:  
   ```bash
   git --version


📺 YouTube Tutorials for Windows Installation
Here are three beginner-friendly videos for hostel students:

Git Installation on Windows (Corey Schafer)
🔗 https://www.youtube.com/watch?v=2j7fD92g-gE

How to Install Git on Windows 10/11 (ProgrammingKnowledge)
🔗 https://www.youtube.com/watch?v=4ZtZ_nFutD8

Git & GitHub Setup for Beginners (CodeWithHarry - Hindi)
🔗 https://www.youtube.com/watch?v=Ez8F0nW6S-w

📌 Step 2: Installing Git on macOS
macOS often comes with Git pre-installed, but it may be outdated.

🖥 Installation Steps:
Check if Git is already installed:

bash
Copy
Edit
git --version
If Git is not installed, use Homebrew (recommended method):

bash
Copy
Edit
brew install git
Or download the macOS installer from → https://git-scm.com/download/mac

Once installed, verify with:

bash
Copy
Edit
git --version
📺 YouTube Tutorials for macOS Installation
Install Git on macOS (Traversy Media)
🔗 https://www.youtube.com/watch?v=USjZcfj8yxE

Installing Git on Mac using Homebrew (The Net Ninja)
🔗 https://www.youtube.com/watch?v=H2qPeJQGgDw

How to Install Git on Mac (ProgrammingKnowledge)
🔗 https://www.youtube.com/watch?v=8JJ101D3knE

📌 Step 3: Installing Git on Linux
Linux users can install Git directly from the terminal.

🖥 Installation Commands:
For Ubuntu/Debian:

bash
Copy
Edit
sudo apt update
sudo apt install git
For Fedora:

bash
Copy
Edit
sudo dnf install git
For Arch Linux:

bash
Copy
Edit
sudo pacman -S git
Verify installation:

bash
Copy
Edit
git --version
📺 YouTube Tutorials for Linux Installation
Installing Git on Ubuntu/Debian (ProgrammingKnowledge)
🔗 https://www.youtube.com/watch?v=4XpnKHJAok8

How to Install Git on Linux (Techno Tim)
🔗 https://www.youtube.com/watch?v=QzZKhvtbTwM

Git Installation on Ubuntu (The Net Ninja)
🔗 https://www.youtube.com/watch?v=r63f51ce84A

💡 Hostel Life Example – Why Learn Installation?
Imagine you’re in the CodingGita hostel and Wi-Fi only works in the common room.
If you already downloaded the Git installer beforehand, you can help your friends install Git in their rooms without needing internet.

You instantly become the tech hero of your block! 🦸‍♂️
Also, being able to install Git on different OS means you can help seniors, juniors, or even hostel staff set up Git on their machines.

📝 Summary
Windows: Download from git-scm.com → Install via wizard → Verify with git --version.

macOS: Use Homebrew or download from git-scm.com → Verify.

Linux: Install via package manager → Verify.

Always run:

bash
Copy
Edit
git --version
after installation to confirm success.

Use YouTube tutorials if you get stuck — they’re beginner-friendly and easy to follow.

💡 Next Step: We’ll configure Git with your username and email so it knows who is making changes in the hostel projects for CodingGita.
