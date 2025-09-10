# Common Rebase Commands

## 🎯 Learning Objectives
By the end of this lesson, you will understand:
- The most commonly used git rebase commands
- When to use each command
- Command syntax and options
- Practical examples for each command
- Best practices for command usage

## 🚀 Essential Rebase Commands

### 1. Basic Rebase Command

#### `git rebase <branch>`

**Purpose**: Rebase your current branch onto another branch.

**Syntax**:
```bash
git rebase <target-branch>
```

**Examples**:
```bash
# Rebase current branch onto main
git rebase main

# Rebase current branch onto develop
git rebase develop

# Rebase feature branch onto main
git checkout feature-branch
git rebase main
```

**What it does**:
- Takes commits from your current branch
- Replays them on top of the target branch
- Creates new commits with new hashes

### 2. Interactive Rebase

#### `git rebase -i <commit>`

**Purpose**: Interactively edit, reorder, or combine commits.

**Syntax**:
```bash
git rebase -i <commit-hash>
git rebase -i HEAD~n  # Last n commits
```

**Examples**:
```bash
# Interactive rebase of last 3 commits
git rebase -i HEAD~3

# Interactive rebase from specific commit
git rebase -i abc123

# Interactive rebase from branch point
git rebase -i main
```

**Interactive Options**:
- `pick`: Use the commit as-is
- `reword`: Change commit message
- `edit`: Stop to edit the commit
- `squash`: Combine with previous commit
- `drop`: Remove the commit
- `fixup`: Like squash, but discard commit message

### 3. Rebase Onto Command

#### `git rebase --onto <new-base> <upstream> <branch>`

**Purpose**: Rebase a specific range of commits onto a different base.

**Syntax**:
```bash
git rebase --onto <new-base> <upstream> <branch>
```

**Examples**:
```bash
# Move commits from feature to main
git rebase --onto main feature~3 feature

# Rebase specific commits onto different branch
git rebase --onto develop main feature
```

**When to use**:
- Moving commits between branches
- Complex rebase scenarios
- Selective commit rebasing

### 4. Continue Rebase

#### `git rebase --continue`

**Purpose**: Continue a rebase after resolving conflicts.

**Syntax**:
```bash
git rebase --continue
```

**When to use**:
- After resolving merge conflicts
- When rebase was paused for manual intervention
- After editing commits in interactive mode

**Workflow**:
```bash
git rebase main
# Conflicts occur, resolve them
git add resolved-files
git rebase --continue
```

### 5. Abort Rebase

#### `git rebase --abort`

**Purpose**: Cancel a rebase and return to the original state.

**Syntax**:
```bash
git rebase --abort
```

**When to use**:
- When rebase becomes too complex
- When you want to start over
- When conflicts are overwhelming

**Example**:
```bash
git rebase main
# Too many conflicts, want to abort
git rebase --abort
# Returns to state before rebase started
```

### 6. Skip Commit

#### `git rebase --skip`

**Purpose**: Skip the current commit during rebase.

**Syntax**:
```bash
git rebase --skip
```

**When to use**:
- When a commit is no longer needed
- When a commit causes unresolvable conflicts
- When you want to drop a specific commit

**Example**:
```bash
git rebase main
# Conflict on commit abc123, want to skip it
git rebase --skip
```

## 🛠️ Advanced Rebase Commands

### 7. Rebase with Strategy

#### `git rebase -X <strategy> <branch>`

**Purpose**: Use specific merge strategy during rebase.

**Syntax**:
```bash
git rebase -X <strategy> <branch>
```

**Available Strategies**:
- `ours`: Prefer our version in conflicts
- `theirs`: Prefer their version in conflicts
- `patience`: More patient diff algorithm
- `ignore-space-change`: Ignore whitespace changes
- `ignore-all-space`: Ignore all whitespace

**Examples**:
```bash
# Prefer our version in conflicts
git rebase -X ours main

# Ignore whitespace changes
git rebase -X ignore-space-change main
```

### 8. Rebase with Preserve Committer

#### `git rebase -p <branch>`

**Purpose**: Preserve original committer information.

**Syntax**:
```bash
git rebase -p <branch>
```

**When to use**:
- When you want to keep original authorship
- When rebasing others' commits
- When maintaining attribution

### 9. Rebase with Autosquash

#### `git rebase --autosquash <branch>`

**Purpose**: Automatically squash commits marked with `fixup!` or `squash!`.

**Syntax**:
```bash
git rebase --autosquash <branch>
```

**Example**:
```bash
# Create commits with fixup markers
git commit -m "Add new feature"
git commit -m "fixup! Add new feature"  # This will be squashed
git commit -m "fixup! Add new feature"  # This will be squashed

# Rebase with autosquash
git rebase --autosquash main
```

## 📋 Command Reference Table

| Command | Purpose | When to Use |
|---------|---------|-------------|
| `git rebase <branch>` | Basic rebase | Most common use case |
| `git rebase -i <commit>` | Interactive rebase | Edit commit history |
| `git rebase --onto <base> <upstream> <branch>` | Rebase onto | Complex scenarios |
| `git rebase --continue` | Continue rebase | After resolving conflicts |
| `git rebase --abort` | Abort rebase | Cancel operation |
| `git rebase --skip` | Skip commit | Drop problematic commit |
| `git rebase -X <strategy>` | Strategy rebase | Handle conflicts automatically |
| `git rebase -p <branch>` | Preserve committer | Keep authorship |
| `git rebase --autosquash` | Auto squash | Automatic commit squashing |

## 🎯 Practical Examples

### Example 1: Basic Feature Branch Rebase

```bash
# You're on feature branch, main has new commits
git checkout feature-branch
git fetch origin
git rebase origin/main

# If conflicts occur:
git add resolved-files
git rebase --continue

# Push the rebased branch
git push --force-with-lease origin feature-branch
```

### Example 2: Interactive Rebase for Clean History

```bash
# Clean up last 5 commits
git rebase -i HEAD~5

# In the editor:
pick abc123 Initial feature
squash def456 Fix typo
squash ghi789 Add tests
pick jkl012 Update documentation
squash mno345 Fix formatting

# This will combine commits 2, 3, and 5 with commit 1
```

### Example 3: Moving Commits Between Branches

```bash
# Move commits from feature1 to feature2
git checkout feature2
git rebase --onto feature2 feature1~3 feature1

# This moves the last 3 commits from feature1 to feature2
```

### Example 4: Handling Conflicts with Strategy

```bash
# Rebase with automatic conflict resolution
git rebase -X ours main

# This will prefer your changes in conflicts
```

## ⚠️ Important Notes

### Command Safety:

1. **Always backup first**:
   ```bash
   git branch backup-branch
   ```

2. **Use `--force-with-lease`** for pushing:
   ```bash
   git push --force-with-lease origin branch-name
   ```

3. **Test after rebasing**:
   ```bash
   npm test  # or your test command
   ```

### Common Mistakes:

1. **Rebasing shared branches** without coordination
2. **Using `--force`** instead of `--force-with-lease`
3. **Not resolving conflicts** properly
4. **Aborting rebase** when conflicts are simple to resolve

## 🔍 Troubleshooting Commands

### Check Rebase Status:
```bash
git status
git rebase --show-current-patch
```

### See Rebase History:
```bash
git reflog
git log --oneline --graph
```

### Reset to Before Rebase:
```bash
git reset --hard HEAD@{1}  # From reflog
```

## 📝 Quick Reference Card

```bash
# Basic rebase
git rebase main

# Interactive rebase
git rebase -i HEAD~3

# Continue after conflicts
git add .
git rebase --continue

# Abort rebase
git rebase --abort

# Skip problematic commit
git rebase --skip

# Rebase with strategy
git rebase -X ours main

# Safe force push
git push --force-with-lease origin branch-name
```

## 🎯 Best Practices

### ✅ Do:
- **Always backup** before rebasing
- **Use interactive rebase** for clean history
- **Resolve conflicts carefully**
- **Test after rebasing**
- **Use `--force-with-lease`** for pushing

### ❌ Don't:
- **Rebase shared branches** without coordination
- **Use `--force`** without `--force-with-lease`
- **Rush through conflict resolution**
- **Rebase without understanding the impact**

## 🎯 Key Takeaways

- **`git rebase <branch>`** is the most common command
- **Interactive rebase** (`-i`) is powerful for editing history
- **Always backup** before rebasing
- **Use `--continue`** after resolving conflicts
- **Use `--abort`** when things go wrong
- **Test thoroughly** after any rebase operation

---

**Next**: Learn about conflict resolution during rebase!
