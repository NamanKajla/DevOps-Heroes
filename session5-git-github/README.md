# Git Practice — Commit and Cherry-Pick

## Task 1: `git commit -a -m` vs `git commit -m`

### Practice Commands

```bash
# Create and initialize a practice repository
mkdir git-practice
cd git-practice
git init -b main

# Configure Git identity if not already configured
git config user.name "Your Name"
git config user.email "your-email@example.com"

# Create and commit a tracked file
echo "First version" > notes.txt
git add notes.txt
git commit -m "Add notes file"

# Modify the tracked file
echo "Second version" >> notes.txt

# Commit tracked file modifications
git commit -a -m "Update notes file"

# Create a new, untracked file
echo "Git practice" > newfile.txt

# Stage and commit the new file
git add newfile.txt
git commit -m "Add new practice file"

# View commit history
git log --oneline
```

### Observation

- `git commit -m "message"` commits changes that have already been staged using `git add`.
- `git commit -a -m "message"` automatically stages modifications and deletions of tracked files before committing.
- The `-a` option does not automatically include new, untracked files.

## Task 2: Git Cherry-Pick

Cherry-pick allows a specific commit from another branch to be applied to the current branch without merging the entire branch.

### Step 1: Create Commits on Main

```bash
echo "Main feature 1" > main1.txt
git add main1.txt
git commit -m "Add main feature 1"

echo "Main feature 2" > main2.txt
git add main2.txt
git commit -m "Add main feature 2"

git log --oneline
```

### Step 2: Create a New Branch

```bash
git switch -c feature-branch

echo "Feature A" > feature-a.txt
git add feature-a.txt
git commit -m "Add feature A"

echo "Feature B" > feature-b.txt
git add feature-b.txt
git commit -m "Add feature B"

echo "Feature C" > feature-c.txt
git add feature-c.txt
git commit -m "Add feature C"
```

### Step 3: Identify the Commit

```bash
git log --oneline
git log --oneline --all --graph
```

Identify the commit hash for `Add feature B` and copy it.

### Step 4: Cherry-Pick into Main

```bash
git switch main

# Replace <commit-hash> with the hash for Add feature B
git cherry-pick <commit-hash>
```

### Step 5: Verify the Result

```bash
git log --oneline
git show --stat HEAD
ls
cat feature-b.txt
```

The `feature-b.txt` file should now exist on `main`, and the latest commit should show the cherry-picked change. The other feature commits are not automatically brought over.

### Step 6: View the Branches

```bash
git log --oneline --all --graph
git branch
```

## Conclusion

Practiced Git commits with staged and unstaged changes, compared `git commit -a -m` with `git commit -m`, created commits on separate branches, and cherry-picked a specific commit into `main`.

