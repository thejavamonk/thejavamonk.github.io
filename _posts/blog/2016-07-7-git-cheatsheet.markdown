---
layout: post
title:  "Git Cheat Sheet - Essential Commands for Developers"
date:   2016-05-09
categories: blog
tags: git
---

A comprehensive guide to the most commonly used Git commands that every developer should know. This cheat sheet covers everything from basic operations to advanced workflows.

## Configuration

**Set your identity**
{% highlight unix %}
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
{% endhighlight %}

**View configuration**
{% highlight unix %}
git config --list
git config user.name
{% endhighlight %}

**Set default editor**
{% highlight unix %}
git config --global core.editor "code --wait"  # VS Code
git config --global core.editor "vim"          # Vim
{% endhighlight %}

**Set default branch name**
{% highlight unix %}
git config --global init.defaultBranch main
{% endhighlight %}

## Repository Setup

**Initialize a new repository**
{% highlight unix %}
git init
git init project-name
{% endhighlight %}

**Clone an existing repository**
{% highlight unix %}
git clone https://github.com/user/repo.git
git clone https://github.com/user/repo.git custom-name
git clone -b branch-name https://github.com/user/repo.git
{% endhighlight %}

## Basic Commands

**Check repository status**
{% highlight unix %}
git status
git status -s  # Short format
{% endhighlight %}

**Add files to staging**
{% highlight unix %}
git add filename.txt
git add .                    # Add all files
git add *.js                 # Add all JS files
git add -A                   # Add all changes
git add -p                   # Interactive staging
{% endhighlight %}

**Commit changes**
{% highlight unix %}
git commit -m "Commit message"
git commit -am "Add and commit"  # Add and commit tracked files
git commit --amend               # Modify last commit
git commit --amend -m "New message"  # Change last commit message
{% endhighlight %}

**View differences**
{% highlight unix %}
git diff                     # Unstaged changes
git diff --staged            # Staged changes
git diff HEAD                # All changes since last commit
git diff branch1..branch2    # Differences between branches
{% endhighlight %}

## Branching

**Create and manage branches**
{% highlight unix %}
git branch                   # List local branches
git branch -a                # List all branches (local + remote)
git branch branch-name       # Create new branch
git branch -d branch-name    # Delete branch (safe)
git branch -D branch-name    # Force delete branch
git branch -m old-name new-name  # Rename branch
{% endhighlight %}

**Switch branches**
{% highlight unix %}
git checkout branch-name
git checkout -b new-branch   # Create and switch
git switch branch-name       # Modern alternative
git switch -c new-branch     # Create and switch (modern)
{% endhighlight %}

**Merge branches**
{% highlight unix %}
git merge branch-name
git merge --no-ff branch-name    # Create merge commit
git merge --squash branch-name   # Squash commits
git merge --abort                # Abort merge
{% endhighlight %}

**Rebase**
{% highlight unix %}
git rebase main
git rebase -i HEAD~3         # Interactive rebase last 3 commits
git rebase --continue        # Continue after resolving conflicts
git rebase --abort           # Abort rebase
{% endhighlight %}

## Remote Operations

**View remotes**
{% highlight unix %}
git remote
git remote -v                # Show URLs
git remote show origin       # Detailed info
{% endhighlight %}

**Add/remove remotes**
{% highlight unix %}
git remote add origin https://github.com/user/repo.git
git remote remove origin
git remote rename old-name new-name
git remote set-url origin https://github.com/user/repo.git
{% endhighlight %}

**Fetch and pull**
{% highlight unix %}
git fetch origin
git fetch --all              # Fetch all remotes
git pull                     # Fetch and merge
git pull origin main
git pull --rebase            # Fetch and rebase
{% endhighlight %}

**Push changes**
{% highlight unix %}
git push origin branch-name
git push -u origin branch-name   # Set upstream
git push --all                   # Push all branches
git push --tags                  # Push tags
git push --force                 # Force push (dangerous!)
git push --force-with-lease      # Safer force push
{% endhighlight %}

**Pull from remote and override local changes**
{% highlight unix %}
git fetch origin
git reset --hard origin/main
{% endhighlight %}

## Stashing

**Save and restore changes**
{% highlight unix %}
git stash                    # Stash changes
git stash save "message"     # Stash with message
git stash -u                 # Include untracked files
git stash list               # List all stashes
git stash show               # Show latest stash
git stash show -p            # Show latest stash with diff
git stash show -p stash@{1}  # Show specific stash
{% endhighlight %}

**Apply and remove stashes**
{% highlight unix %}
git stash apply              # Apply latest stash
git stash apply stash@{1}    # Apply specific stash
git stash pop                # Apply and remove latest
git stash drop               # Remove latest stash
git stash drop stash@{1}     # Remove specific stash
git stash clear              # Remove all stashes
{% endhighlight %}

**Create branch from stash**
{% highlight unix %}
git stash branch branch-name
{% endhighlight %}

## Undoing Changes

**Unstage files**
{% highlight unix %}
git reset HEAD -- path/to/file
git reset HEAD -- .          # Unstage all
git restore --staged file    # Modern alternative
{% endhighlight %}

**Discard changes**
{% highlight unix %}
git checkout -- file         # Discard working directory changes
git restore file             # Modern alternative
git clean -fd                # Remove untracked files/directories
git clean -fdn               # Dry run
{% endhighlight %}

**Reset commits**
{% highlight unix %}
git reset --soft HEAD~1      # Keep changes staged
git reset --mixed HEAD~1     # Keep changes unstaged (default)
git reset --hard HEAD~1      # Discard changes completely
git reset --hard commit-hash # Reset to specific commit
{% endhighlight %}

**Revert commits**
{% highlight unix %}
git revert commit-hash       # Create new commit that undoes changes
git revert HEAD              # Revert last commit
git revert HEAD~3..HEAD      # Revert range of commits
{% endhighlight %}

## Viewing History

**View commit history**
{% highlight unix %}
git log
git log --oneline            # Compact view
git log --graph              # Show branch graph
git log --all --graph --oneline  # Visual branch history
git log -n 5                 # Last 5 commits
git log --author="Name"      # Filter by author
git log --since="2 weeks ago"
git log --until="2023-01-01"
git log --grep="keyword"     # Search commit messages
git log -- file.txt          # Commits affecting file
{% endhighlight %}

**Show commit details**
{% highlight unix %}
git show commit-hash
git show HEAD                # Show last commit
git show HEAD~2              # Show commit 2 steps back
{% endhighlight %}

**View file history**
{% highlight unix %}
git blame file.txt           # Show who changed each line
git log -p file.txt          # Show changes to file
git log --follow file.txt    # Follow renames
{% endhighlight %}

**Reference log**
{% highlight unix %}
git reflog                   # Show all reference updates
git reflog show branch-name
{% endhighlight %}

## Tagging

**Create tags**
{% highlight unix %}
git tag v1.0.0               # Lightweight tag
git tag -a v1.0.0 -m "Version 1.0.0"  # Annotated tag
git tag -a v1.0.0 commit-hash  # Tag specific commit
{% endhighlight %}

**View and manage tags**
{% highlight unix %}
git tag                      # List tags
git tag -l "v1.*"            # Filter tags
git show v1.0.0              # Show tag details
git tag -d v1.0.0            # Delete local tag
git push origin --delete v1.0.0  # Delete remote tag
{% endhighlight %}

**Push tags**
{% highlight unix %}
git push origin v1.0.0
git push origin --tags       # Push all tags
{% endhighlight %}

## Advanced Commands

**Cherry-pick commits**
{% highlight unix %}
git cherry-pick commit-hash
git cherry-pick commit1 commit2
git cherry-pick --continue
git cherry-pick --abort
{% endhighlight %}

**Search in repository**
{% highlight unix %}
git grep "search-term"
git grep -n "search-term"    # Show line numbers
git grep "search-term" main  # Search in specific branch
{% endhighlight %}

**Bisect (find bugs)**
{% highlight unix %}
git bisect start
git bisect bad               # Current commit is bad
git bisect good commit-hash  # Known good commit
git bisect reset             # End bisect session
{% endhighlight %}

**Submodules**
{% highlight unix %}
git submodule add https://github.com/user/repo.git path
git submodule init
git submodule update
git submodule update --remote
{% endhighlight %}

**Work with patches**
{% highlight unix %}
git format-patch -1 HEAD     # Create patch from last commit
git apply patch-file.patch   # Apply patch
git am patch-file.patch      # Apply patch with commit
{% endhighlight %}

## Troubleshooting

**Resolve merge conflicts**
{% highlight unix %}
git status                   # See conflicted files
# Edit files to resolve conflicts
git add resolved-file.txt
git commit                   # Complete merge
git merge --abort            # Abort merge if needed
{% endhighlight %}

**Error: You have not concluded your merge (MERGE_HEAD exists)**
{% highlight unix %}
# Either complete the merge:
git add .
git commit -m "Resolved merge conflicts"

# Or abort the merge:
git merge --abort
{% endhighlight %}

**Uncommit last changes but keep files**
{% highlight unix %}
git reset --soft HEAD~1
{% endhighlight %}

**Remove file from Git but keep locally**
{% highlight unix %}
git rm --cached filename
git rm -r --cached directory/
{% endhighlight %}

**Change remote URL**
{% highlight unix %}
git remote set-url origin https://new-url.git
{% endhighlight %}

**Sync fork with upstream**
{% highlight unix %}
git remote add upstream https://github.com/original/repo.git
git fetch upstream
git checkout main
git merge upstream/main
{% endhighlight %}

**Fix "detached HEAD" state**
{% highlight unix %}
git checkout -b new-branch   # Create branch from current state
# Or return to a branch:
git checkout main
{% endhighlight %}

**Recover deleted commits**
{% highlight unix %}
git reflog
git checkout -b recovery-branch commit-hash
{% endhighlight %}

## Useful Aliases

Add these to your `.gitconfig` file or use `git config --global alias.name 'command'`:

{% highlight unix %}
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.st status
git config --global alias.unstage 'reset HEAD --'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual 'log --all --graph --oneline --decorate'
{% endhighlight %}

## Best Practices

1. **Commit often** with clear, descriptive messages
2. **Pull before push** to avoid conflicts
3. **Create feature branches** for new work
4. **Review changes** before committing (`git diff`)
5. **Don't force push** to shared branches
6. **Use .gitignore** to exclude unnecessary files
7. **Keep commits atomic** - one logical change per commit
8. **Write meaningful commit messages** - explain why, not what

## Common Workflows

**Feature branch workflow**
{% highlight unix %}
git checkout main
git pull origin main
git checkout -b feature/new-feature
# Make changes
git add .
git commit -m "Add new feature"
git push -u origin feature/new-feature
# Create pull request, then after merge:
git checkout main
git pull origin main
git branch -d feature/new-feature
{% endhighlight %}

**Hotfix workflow**
{% highlight unix %}
git checkout main
git checkout -b hotfix/critical-bug
# Fix the bug
git add .
git commit -m "Fix critical bug"
git checkout main
git merge hotfix/critical-bug
git push origin main
git branch -d hotfix/critical-bug
{% endhighlight %}

This cheat sheet covers the essential Git commands you'll use daily as a developer. Keep it handy for quick reference!