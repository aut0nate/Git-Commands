# Git Commands Cheatsheet

This repository contains a comprehensive list of Git commands, organised into categories for ease of reference.

---

## Table of Contents

- [General Information Commands](#general-information-commands)
- [Configuration Commands](#configuration-commands)
- [Repository Management Commands](#repository-management-commands)
- [Staging and Commit Commands](#staging-and-commit-commands)
- [Branch Management Commands](#branch-management-commands)
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
```

## Repository Management Commands

```bash
# Initialise local git repository
git init 

# Check status of current repository
git status

# Check status of current repository (compact)
git status --short

# Check the logs of all commits
git log

# Check the logs of all commits and returns the output on one line
git log --oneline
```

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

## Branch Management Commands

```bash
# Create a new branch
git branch <nameofbranch>

# Renames a branch
git branch -m <newbranchname>

# Deletes a branch
git branch -d <nameofbranch>

# Force deletes a branch
git branch -D <nameofbranch>

# Switches branch
git switch <nameofbranch>

# Creates and switches to a new branch
git switch -c <nameofbranch>

# Select a branch
git checkout <nameofbranch>

# Creates and switches to a new branch
git checkout -b <nameofbranch>

# Merge a branch
git merge <nameofbranch>

# Merge a branch with a message
git merge -m "<message>" <nameofbranch>

# Deletes the local and remote branch
git branch -d --remote <nameofbranch>
```

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
git push origin --delete <oldbranchname>
```

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
