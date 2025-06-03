# Git Commands Cheatsheet

![Git](https://img.shields.io/badge/git-%23F05033.svg?style=for-the-badge&logo=git&logoColor=white)

This repository contains a collection of Git commands that I’ve found particularly useful as part of my learning process. I have grouped this into categories for easy reference.

---

## Contents

- [General Information Commands](#general-information-commands)
- [Configuration Commands](#configuration-commands)
- [Repository Management Commands](#repository-management-commands)
- [Staging and Commit Commands](#staging-and-commit-commands)
- [Branch Management Commands](#branch-management-commands)
- [Diff and Comaparison Commands](#diff-and-comparison-commands)
- [Stash Commands](#stash-commands)
- [Remote Repository Commands](#remote-repository-commands)
- [Rebase and Reset Commands](#rebase-and-reset-commands)
  
---

## General Information Commands

```bash
# Get all available git commands
git help --all 

# Get help about a specific command
git help <command>

# Get current version of git
git --version
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)

## Configuration Commands

```bash
# Get configuration information about git
git config --list

# Configure a user name for commits
git config --global user.name "<name>"

# Configure an email address for commits
git config --global user.email "<emailaddress>"

# Configure the default branch
git config --global init.defaultBranch main

# Enable autocorrect for Git commands
git config --global help.autocorrect 1
# Automatically correct minor typos in Git commands, e.g., "git staus" -> "git status"

# Set the default editor for Git
git config --global core.editor "code --wait"
git config --global core.editor "nano -w"
# Set the default editor to Visual Studio Code (or your preferred editor)
# Run git config --global -e to open in your editor of choice

# Enable color output in Git
git config --global color.ui true
# Enable colorful output for Git commands, making it easier to read and understand

# Enable Git to ignore file mode changes
git config --global core.fileMode false
# Ignore file mode changes (e.g., executable bits) to avoid unnecessary commits

# Set the default push behavior
git config --global push.default simple
# Set the default push behavior to "simple", which pushes the current branch to its upstream counterpart

# Enable Git to use the credential manager
git config --global credential.helper manager
# Enable Git to use the credential manager to store and retrieve credentials

# Set the default commit message format
git config --global commit.template ~/.gitmessage
# Set the default commit message format using a template file (~/.gitmessage)
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)

## Repository Management Commands

```bash
# Initialise local git repository
git init 

# Check status of current repository
git status

# Check status of current repository (compact)
git status --short

# Show the commit history
git log

# Show the commit history in a compact, one-line-per-commit format
git log --oneline

# Show the commit history in a compact, one-line-per-commit format, output directly to the terminal (not paged)
git --no-pager log --oneline

# Display the commit history as a graph, with each commit on one line, showing all branches and references (great for visualising branch structure)
git log --oneline --graph --all --decorate

# Show only commits authored by a specific user
git log --author="name"

# Show only commits committed by a specific user
git log --committer="name"

# Show commits by a specific user in the last hour
git log --author="name" --since="1 hour"

# Show commits by a specific user in the last day 
git log --author="name" --since="1 day"

# Show commits by a specific user in the last week  
git log --author="name" --since="1 week"

# Show commits by a specific user in the last month 
git log --author="name" --since="1 month"

# Show the parent commits of a given commit (useful for merge commits)
git log --pretty="format:%P" -n 1 <hash>

# Show only the names of the files changed in a specific commit
git show --pretty="format:" --name-only <hash>

# Show the changes (diff) for a specific file in a specific commit
git show <hash> -- <file>

# Show the details and changes of the most recent commit
git show HEAD

# Show the diff with word-level highlighting (useful for spotting small changes)
git show --word-diff <hash>
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)

## Staging and Commit Commands

```bash
# Add file to the staging area
git add <file>

# Renames files
git mv <oldfile> <newfile>

# Remove files from index
git rm <file>

# Remove files from staging
git restore --staged <file>

# Restore a file to its state at the last commit
git restore <file>

# Restore a file to a specific commit
git restore --source <commithash> <file>

# Restore a file to a specific commit based on the value at 'n'
git restore --source HEAD~n <file>

# Commit changes to index
git commit -m "<message>"

# Commit changes to index without staging
git commit -a -m "<message>"

# Amend the last commit (this will open your commit editor to modify the commit message)
git commit --amend

# Amend the last commit (modify commit message)
git commit --amend -m "New commit message"

# Amend the last commit and change the author details
git commit --amend --author "name <email>"

```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)

## Branch Management Commands

```bash
# List all local branches  
git branch

# Create a new branch
git branch <nameofbranch>

# Renames a branch
git branch -m <newbranchname>

# Deletes a branch
git branch -d <nameofbranch>

# Force deletes a branch
git branch -D <nameofbranch>

# List all remote branches  
git branch -r  
  
# List all branches, local and remote  
git branch -a

# Switches branch
git switch <nameofbranch>

# Creates and switches to a new branch
git switch -c <nameofbranch>

# Select a branch
git checkout <nameofbranch>

# Creates and switches to a new branch
git checkout -b <nameofbranch>

# Switch to a specific commit in the repository's history (detached HEAD state)
git checkout <commithash>

# Switch to the 'main' branch, or use '-' to switch to your previous branch
git switch main
git switch -

# Merge a branch
git merge <nameofbranch>

# Merge a branch with a message
git merge -m "<message>" <nameofbranch>
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)

## Diff and Comparison Commands

```bash
# Show unstaged changes in your working directory  
git diff

# Show staged changes (what will be committed)  
git diff --cached
git diff --staged

# Compare two branches  
git diff main <branch>
  
# Compare a specific file between two branches  
git diff main <branch> -- <file>

# Compare between two commits 
git diff <commit1> <commit2>

# Compare a specific file between two commits 
git diff <commit1> <commit2> -- <file>

# See all changes since last commit (both staged and unstaged)  
git diff HEAD
  
# Word-level diff (more readable for prose)
git diff --color-words
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)

## Stash Commands

```bash
# Temporarily save changes that are not ready to be committed
git stash

# Stash changes with a descriptive message  
git stash -m "<Message>"

# List all stashes  
git stash list

# Apply the most recent stash and remove it from the stash list  
git stash pop

# Apply a specific stash by index and remove it from the stash list  
git stash pop stash@{0}
git stash pop 0

# Apply a specific stash without removing it from the stash list  
git stash apply stash@{0}
git stash apply 0

# Delete a specific stash without applying it  
git stash drop stash@{0}
git stash drop 0

# Include untracked files in the stash  
git stash -u
git stash --include-untracked

# Clear all stashes  
git stash clear

# Create a new branch from a stash  
git stash branch stash@{0}
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)


## Remote Repository Commands

```bash
# Clone repository into a new directory
git clone <repositoryurl>

# Fetch updates from the remote repository
git fetch

# Fetch and merge updates
git pull

# Show remote repository URLs
git remote -v

# Add remote repository
git remote add origin <remoteurl>

# Remove remote repository
git remote remove origin

# Push local repository to remote repository
git push origin <nameofbranch>

# Pushes a renamed branch to the remote repo
git push origin -u <newbranchname>

# Push the local 'main' branch to the remote repository named 'origin'
# and set it as the upstream branch, establishing a link for future pushes and pulls
git push --set-upstream origin <nameofbranch>

# Delete a branch on the remote repo
git push origin --delete <nameofbranch>

# Force push the amended commit whilst checking the remote hasn't changed unexpectedly
git push --force-with-lease
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)

## Rebase and Reset Commands

```bash
# Rebase the current branch on top of the specified branch
git rebase <branch>

# Start an interactive rebase for the last n commits
git rebase -i HEAD~n

# Rebase your feature branch onto the tip of the master branch
git fetch origin
git rebase origin/master

# Reset the current HEAD to the specified commit, keeping all changes in the staging area
git reset --soft <commit-hash>

# Soft reset (moves HEAD to another commit, but keeps the index and working directory)
git reset --soft HEAD~n

# Mixed reset (moves HEAD and updates the index with the contents of the reset commit)
git reset --mixed HEAD~n

# Hard reset (moves HEAD and makes the index and working directory exactly match the reset commit)
git reset --hard HEAD~n
```

[⬆ ʀᴇᴛᴜʀɴ ᴛᴏ ᴄᴏɴᴛᴇɴᴛꜱ](#contents)
