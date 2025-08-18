# Unit 1 – Answers (Tests and Command-Based Questions)

This README contains suggested answers for:
- `unit1-test-questions.md` (10 questions)
- `unit1-command-based-questions.md` (5 command scenarios)

Use these to review and self-check your understanding.

---

## A) Answers: unit1-test-questions.md (10)

1) What is version control?  
**Answer:** B — A system that tracks changes to files over time and lets you revert or collaborate

2) Git as a distributed VCS  
**Answer:** B — Each developer has a full copy of the repository history locally

3) Initialize a new repository  
**Answer:** C — `git init`

4) Show unstaged changes  
**Answer:** B — `git diff`

5) “Prep table” area in Git workflow  
**Answer:** B — Staging area (index)

6) Set global Git username  
**Answer:** B — `git config --global user.name "Your Name"`

7) Working directory vs staging area vs repository (Short Answer)  
**Answer (sample):**
- **Working directory:** Your real files on disk where you edit and create content.
- **Staging area (index):** A preparation zone where you mark which changes will go into the next commit.
- **Repository (history):** Permanent, versioned history of commits saved by Git.

8) Two benefits of using Git (Short Answer)  
**Answer (examples):**
- Never lose work; you can revert to earlier versions easily.
- Collaborate safely; track who changed what and when.
- Maintain a clear history to learn from your progress.

9) Commit only README.md (Short Answer)  
**Answer (example commands):**
```bash
git add README.md
git commit -m "Update README"
```
(Optional) Verify before committing:
```bash
git status
```

10) Compact history and last changes (Short Answer)  
**Answer (commands):**
```bash
# (a) Compact history
git log --oneline

# (b) Exact changes introduced by latest commit
git show HEAD
```

---

## B) Answers: unit1-command-based-questions.md (5)

1) Initialize and First Commit  
Create folder, enter it, init Git, create README, stage, commit:
```bash
mkdir codingGita-journal
cd codingGita-journal

git init
echo "# My codingGita Learning Journey" > README.md

git add README.md
git commit -m "Created initial README"
```
(Windows PowerShell equivalent for the echo line works the same.)

2) Configure Git (Global)  
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@college.edu"
git config --global init.defaultBranch main
git config --global color.ui auto
```

3) Selective Staging and Commit  
Stage only README.md and style.css, verify, then commit:
```bash
git add README.md style.css
git status
git commit -m "Update docs and styles"
```

4) Inspect History and Last Changes  
```bash
# Compact, one-line list
git log --oneline

# Exact changes introduced by most recent commit
git show HEAD
```

5) Compare and Review Changes  
Unstaged diff for a single file, then staged-only diff:
```bash
# Unstaged changes for style.css
git diff style.css

# Stage it
git add style.css

# Diff of staged changes only
git diff --staged
```

---

Tip: When writing commands, always run `git status` before and after key steps to validate what’s staged and what will be committed.
