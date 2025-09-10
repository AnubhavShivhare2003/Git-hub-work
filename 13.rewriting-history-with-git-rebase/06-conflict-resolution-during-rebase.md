# Conflict Resolution During Rebase

## 🎯 Learning Objectives
By the end of this lesson, you will understand:
- How conflicts occur during rebase
- How to identify and resolve conflicts
- Step-by-step conflict resolution process
- Different types of conflicts and their solutions
- Best practices for handling rebase conflicts

## 🚨 Understanding Rebase Conflicts

### What Causes Conflicts During Rebase?

Conflicts occur when Git cannot automatically merge changes because:
- The same lines were modified in both branches
- One branch deleted a file that the other modified
- Both branches added different content to the same location

### Visual Example of Conflict

#### Before Rebase:
```
main:     A---B---C (modified file.txt)
feature:      D---E---F (also modified file.txt)
```

#### During Rebase:
```
main:     A---B---C
feature:      D---E---F (conflict on commit D)
```

## 🔍 Identifying Conflicts

### Git's Conflict Messages

When conflicts occur, Git will show messages like:

```bash
$ git rebase main
Auto-merging file.txt
CONFLICT (content): Merge conflict in file.txt
error: could not apply abc123... Your commit message
Resolve all conflicts manually, mark them as resolved with
"git add/rm <conflicted_files>", then run "git rebase --continue".
You can instead skip this commit with "git rebase --skip".
```

### Checking Conflict Status

```bash
# See which files have conflicts
git status

# See detailed conflict information
git diff

# See conflicts in specific file
git diff file.txt
```

## 🛠️ Step-by-Step Conflict Resolution

### Step 1: Identify Conflicted Files

```bash
git status
```

**Example Output**:
```
On branch feature
You are currently rebasing.
  (fix conflicts and then run "git rebase --continue")
  (use "git rebase --skip" to skip this patch)
  (use "git rebase --abort" to check out the original branch)

Unmerged paths:
  (use "git add <file>..." to mark resolution)
        both modified:   file.txt
        both modified:   src/app.js
```

### Step 2: Examine the Conflicts

Open the conflicted files in your editor. You'll see conflict markers:

```text
<<<<<<< HEAD
This is the content from the target branch (main)
=======
This is the content from your branch (feature)
>>>>>>> abc123... Your commit message
```

**Conflict Markers Explained**:
- `<<<<<<< HEAD`: Start of content from target branch
- `=======`: Separator between the two versions
- `>>>>>>> abc123...`: End of content from your branch

### Step 3: Resolve Conflicts Manually

Edit the file to resolve conflicts. You have several options:

#### Option 1: Keep Your Changes
```text
This is the content from your branch (feature)
```

#### Option 2: Keep Their Changes
```text
This is the content from the target branch (main)
```

#### Option 3: Combine Both Changes
```text
This is the content from the target branch (main)
This is the content from your branch (feature)
```

#### Option 4: Create New Content
```text
This is completely new content that combines both ideas
```

### Step 4: Mark Conflicts as Resolved

```bash
# Add resolved files
git add file.txt
git add src/app.js

# Or add all resolved files at once
git add .
```

### Step 5: Continue the Rebase

```bash
git rebase --continue
```

## 🎨 Types of Conflicts and Solutions

### 1. Content Conflicts

**What it is**: Same lines modified differently in both branches.

**Example**:
```text
<<<<<<< HEAD
function calculateTotal(price, tax) {
    return price * (1 + tax);
}
=======
function calculateTotal(price, tax) {
    return price + (price * tax);
}
>>>>>>> abc123... Fix calculation
```

**Resolution**: Choose the correct implementation or combine both approaches.

### 2. File Deletion Conflicts

**What it is**: One branch deleted a file, the other modified it.

**Example**:
```bash
CONFLICT (modify/delete): file.txt deleted in HEAD and modified in abc123... Your commit
```

**Resolution Options**:
```bash
# Keep the file (your changes)
git add file.txt

# Delete the file (their changes)
git rm file.txt
```

### 3. Add/Add Conflicts

**What it is**: Both branches added different content to the same location.

**Example**:
```text
<<<<<<< HEAD
import { ComponentA } from './components/ComponentA';
=======
import { ComponentB } from './components/ComponentB';
>>>>>>> abc123... Add component
```

**Resolution**: Include both imports or choose the appropriate one.

### 4. Binary File Conflicts

**What it is**: Conflicts in binary files (images, videos, etc.).

**Resolution**: Choose one version or manually merge if possible.

```bash
# Choose your version
git checkout --ours image.png
git add image.png

# Choose their version
git checkout --theirs image.png
git add image.png
```

## 🔧 Advanced Conflict Resolution Techniques

### Using Merge Tools

```bash
# Configure a merge tool
git config --global merge.tool vscode

# Use merge tool for conflicts
git mergetool
```

### Resolving Multiple Conflicts

When you have multiple conflicts:

1. **Resolve one file at a time**
2. **Test after each resolution**
3. **Use `git add` after each file**
4. **Continue with `git rebase --continue`**

### Skipping Problematic Commits

```bash
# Skip the current commit entirely
git rebase --skip

# Use this when:
# - Commit is no longer needed
# - Conflicts are too complex
# - Commit was experimental
```

## 📋 Conflict Resolution Workflow

### Complete Workflow Example

```bash
# 1. Start rebase
git rebase main

# 2. Conflicts occur
CONFLICT (content): Merge conflict in file.txt

# 3. Check status
git status

# 4. Open conflicted file and resolve
# Edit file.txt to remove conflict markers

# 5. Stage resolved file
git add file.txt

# 6. Continue rebase
git rebase --continue

# 7. Repeat for each conflicted commit
# 8. Verify final result
git log --oneline --graph
```

## ⚠️ Common Mistakes and How to Avoid Them

### Mistake 1: Forgetting to Add Resolved Files

**Problem**: You resolve conflicts but forget to `git add` the files.

**Solution**: Always check `git status` and add resolved files.

### Mistake 2: Leaving Conflict Markers

**Problem**: You forget to remove conflict markers from files.

**Solution**: Search for `<<<<<<<`, `=======`, and `>>>>>>>` in your files.

### Mistake 3: Rushing Through Conflicts

**Problem**: You resolve conflicts too quickly without understanding them.

**Solution**: Take time to understand what each change does.

### Mistake 4: Not Testing After Resolution

**Problem**: You don't test your changes after resolving conflicts.

**Solution**: Always run tests after conflict resolution.

## 🎯 Best Practices for Conflict Resolution

### ✅ Do:

1. **Read conflict markers carefully**
   ```text
   <<<<<<< HEAD
   Their changes
   =======
   Your changes
   >>>>>>> abc123... Your commit
   ```

2. **Understand the context** of each change

3. **Test your resolution**
   ```bash
   npm test  # or your test command
   ```

4. **Commit one conflict at a time**
   ```bash
   git add resolved-file.txt
   git rebase --continue
   ```

5. **Use meaningful commit messages** after resolution

### ❌ Don't:

1. **Don't rush through conflicts**
2. **Don't leave conflict markers in files**
3. **Don't resolve conflicts without understanding them**
4. **Don't skip testing after resolution**
5. **Don't resolve multiple conflicts at once** (unless simple)

## 🔍 Troubleshooting Common Issues

### Issue: "No changes were made to the commit"

**Cause**: You didn't actually resolve the conflicts.

**Solution**: 
```bash
# Check if conflicts still exist
git status
# Resolve conflicts properly
# Add resolved files
git add .
```

### Issue: "Cannot continue rebase"

**Cause**: You have unresolved conflicts.

**Solution**:
```bash
# Check status
git status
# Resolve remaining conflicts
# Add resolved files
git add .
git rebase --continue
```

### Issue: "Rebase is in progress"

**Cause**: Previous rebase was interrupted.

**Solution**:
```bash
# Continue the rebase
git rebase --continue

# Or abort and start over
git rebase --abort
```

## 📝 Quick Reference Commands

```bash
# Check conflict status
git status

# See conflicts in detail
git diff

# Resolve conflicts manually
# Edit files to remove conflict markers

# Stage resolved files
git add resolved-file.txt

# Continue rebase
git rebase --continue

# Skip problematic commit
git rebase --skip

# Abort rebase
git rebase --abort

# Use merge tool
git mergetool
```

## 🎯 Conflict Resolution Checklist

### Before Starting:
- [ ] Backup your branch
- [ ] Ensure working directory is clean
- [ ] Understand what you're rebasing onto

### During Conflicts:
- [ ] Read conflict markers carefully
- [ ] Understand both versions of changes
- [ ] Resolve conflicts thoughtfully
- [ ] Remove all conflict markers
- [ ] Test your resolution

### After Resolution:
- [ ] Stage all resolved files
- [ ] Continue the rebase
- [ ] Test the final result
- [ ] Verify commit history

## 🎯 Key Takeaways

- **Conflicts are normal** during rebase operations
- **Read conflict markers carefully** to understand changes
- **Resolve conflicts one at a time** for better control
- **Always test** after resolving conflicts
- **Use `git add`** to stage resolved files
- **Use `git rebase --continue`** to proceed
- **Don't rush** through conflict resolution

---

**Next**: Practice with detailed exercises for each subtopic!
