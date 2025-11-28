<em>
  
## Configuration & Setup

```bash
git config --global user.name "Mihir Rathod"           # Configure author name
git config --global user.email "mihir.rathod23@gmail.com"  # Configure author email
git init                                    # Create a new local repository
git clone <link_of_repo>                    # Clone repository
```

## Branch Operations

```bash
git branch                                  # List all branches
git branch -b <branch_name>                 # Create branch
git checkout <branch_name>                  # Switch to branch
git checkout -b <branch_name>               # Create and switch to branch
git branch -d <branch_name>                 # Delete local branch
git push origin <branch_name>               # Push branch to remote
git push --all origin                       # Push all branches
git push origin :<branch_name>              # Delete remote branch
```

## Commit & Push

```bash
git add .                                   # Add all files
git add <file1> <file2>                     # Add specific files
git commit -m "message"                     # Commit changes
git push origin <branch_name>               # Push to remote
```

## Viewing Changes

```bash
git status                                  # Check status
git diff                                    # View all conflicts
git diff --base <filename>                  # View conflicts against base
git diff <source_branch> <target_branch>    # Preview changes before merge
git log --oneline                           # View commit history
git log --oneline -n 10                     # View last 10 commits
git log --all --full-history -- <file>      # View file history
```

## Reverting Changes

```bash
git checkout -- <filename>                  # Discard local changes
git fetch origin && git reset --hard origin/master  # Reset to remote
git reset --hard <commit_id>                # Reset to specific commit
git revert <commit_id>                      # Create undo commit
git revert -n <commit_id>                   # Revert without committing
```

## Tags

```bash
git tag <tag_name> <commit_id>              # Create tag
git push --tags origin                      # Push all tags
```

</em>
