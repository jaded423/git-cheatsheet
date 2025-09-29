# Git Workflow Cheat Sheet - Command Line

## Quick Reference: Creating a New Project and Pushing to GitHub

### Step 1: Create Project Directory
```bash
# Navigate to projects folder
cd ~/projects

# Create new project folder (use hyphens, not spaces!)
mkdir my-new-project

# Navigate into it
cd my-new-project

# Verify location
pwd
```

---

### Step 2: Initialize Git Repository
```bash
# Initialize Git (creates hidden .git folder)
git init

# Check status (should show "No commits yet")
git status
```

---

### Step 3: Create Your Files
```bash
# Create a README file
nvim README.md
# Press 'i' to insert, write content, ESC then :wq to save

# Create other files as needed
nvim myfile.txt

# List files to verify
ls -la
```

---

### Step 4: Stage Files (Prepare for Commit)
```bash
# Check what files exist
git status

# Stage all files
git add .

# Or stage specific files
git add README.md myfile.txt

# Check status again (files should be green)
git status
```

**Vocabulary:**
- **Staging** = Preparing files to be committed
- **Staged files** = Files ready to be committed (shown in green)
- **Untracked files** = Files Git sees but isn't tracking yet (shown in red)

---

### Step 5: Commit (Save Snapshot)
```bash
# Commit with a descriptive message
git commit -m "Initial commit: Add README and project files"

# View commit history
git log --oneline
```

**Vocabulary:**
- **Commit** = A snapshot/checkpoint of your project at this moment
- **Commit message** = Description of what changed in this commit
- Use present tense: "Add feature" not "Added feature"

---

### Step 6: Create GitHub Repository (Command Line Method)
```bash
# Create public repo and push in one command
gh repo create my-new-project --public --source=. --remote=origin --push

# Or create private repo
gh repo create my-new-project --private --source=. --remote=origin --push

# With description
gh repo create my-new-project --public --description "Project description here" --source=. --remote=origin --push
```

**What this does:**
- Creates repository on GitHub
- Adds GitHub as a remote named "origin"
- Pushes your commits to GitHub

**Vocabulary:**
- **Remote** = A version of your repository hosted elsewhere (like GitHub)
- **Origin** = Default name for the main remote repository
- **Push** = Send your local commits to the remote (GitHub)

---

### Step 7: Verify It Worked
```bash
# Check remote connection
git remote -v

# View repo in browser
gh repo view --web
```

---

## Daily Workflow: Making Changes and Pushing

### After You Make Changes to Files

```bash
# 1. Check what changed
git status
git diff                    # See exact line changes

# 2. Stage changes
git add .                   # Stage all changes
git add file1.txt file2.txt # Stage specific files

# 3. Commit changes
git commit -m "Add new feature X"

# 4. Push to GitHub
git push
```

**That's it!** After the initial setup, it's just these 4 steps.

---

## Complete Workflow Example

```bash
# Create project
cd ~/projects
mkdir todo-app
cd todo-app

# Initialize Git
git init

# Create files
echo "# Todo App" > README.md
echo "print('Hello World')" > app.py

# Stage and commit
git add .
git commit -m "Initial commit: Add README and app skeleton"

# Create GitHub repo and push
gh repo create todo-app --public --source=. --remote=origin --push

# Verify
gh repo view --web
```

---

## Useful Commands Reference

### Checking Status
```bash
git status              # See what's changed
git diff                # See line-by-line changes
git log                 # See commit history
git log --oneline       # Compact commit history
```

### Staging
```bash
git add .               # Stage all changes
git add filename        # Stage specific file
git add *.py            # Stage all Python files
```

### Committing
```bash
git commit -m "message"           # Commit with message
git commit -am "message"          # Stage and commit tracked files
git log --oneline                 # View commits
```

### Remote Operations
```bash
git remote -v                     # See remote connections
git push                          # Push commits to GitHub
git pull                          # Get latest from GitHub
```

### GitHub CLI
```bash
gh repo create <name> --public    # Create public repo
gh repo create <name> --private   # Create private repo
gh repo view --web                # Open repo in browser
gh repo list                      # List your repositories
```

---

## Common Mistakes to Avoid

❌ **Don't:**
- Commit without a meaningful message
- Use spaces in folder names (use hyphens: `my-project` not `my project`)
- Forget to check `git status` before committing
- Push sensitive data (passwords, API keys)

✅ **Do:**
- Write clear commit messages
- Commit often (small logical chunks)
- Check `git status` frequently
- Use `.gitignore` for sensitive files

---

## Git Vocabulary Quick Reference

| Term | Meaning |
|------|---------|
| **Repository (repo)** | A project folder tracked by Git |
| **Initialize** | Start Git tracking (`git init`) |
| **Stage** | Prepare files for commit (`git add`) |
| **Commit** | Save a snapshot of staged changes |
| **Remote** | External repository (like on GitHub) |
| **Origin** | Default name for main remote |
| **Push** | Upload commits to remote |
| **Pull** | Download commits from remote |
| **Clone** | Copy a repository from remote to local |
| **Branch** | Parallel version of your code |
| **Main/Master** | Default primary branch name |

---

## Troubleshooting

### "Nothing to commit"
- You haven't made any changes since last commit
- Create or modify a file first

### "No remote configured"
```bash
git remote add origin git@github.com:username/repo-name.git
```

### "Remote origin already exists"
```bash
git remote remove origin
git remote add origin git@github.com:username/repo-name.git
```

### "Failed to push"
- Check internet connection
- Verify SSH is working: `ssh -T git@github.com`
- Check remote exists: `gh repo view --web`

---

## Practice Exercise

Try creating 3 practice repos to build muscle memory:

1. **practice-1**: Just a README
2. **practice-2**: README + a code file
3. **practice-3**: README + multiple files in folders

Run through the complete workflow for each one!

---

## Next Level: Working with Branches

Once comfortable with the basics, learn branching:

```bash
# Create new branch
git checkout -b feature-name

# Switch branches
git checkout main

# List branches
git branch

# Merge branch into main
git checkout main
git merge feature-name
```

---

## Save This Cheat Sheet

Want to keep this handy? Save it to your projects:

```bash
cd ~/projects
mkdir git-cheatsheets
cd git-cheatsheets
git init

# Create the cheat sheet file
nvim git-workflow-cheatsheet.md
# Paste this content

git add .
git commit -m "Add Git workflow cheat sheet"
gh repo create git-cheatsheets --public --source=. --remote=origin --push
```

Now you'll always have it available on GitHub!