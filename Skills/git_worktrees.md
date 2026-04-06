```markdown
# Git Worktrees Guide

Git worktrees allow you to check out multiple branches simultaneously in different directories.

---

## Why Use Worktrees?

- Work on multiple features/branches at the same time
- Keep one branch "clean" while experimenting in another
- Avoid stashing changes when you need to switch contexts quickly

---

## Common Commands

### List all worktrees

```bash
git worktree list
```

### Add a worktree (from existing branch)

```bash
git worktree add <path> <branch-name>
```

### Add a worktree (create new branch)

```bash
git worktree add <path> -b <new-branch-name>
```

### Add a worktree (from specific commit)

```bash
git worktree add <path> <commit-sha>
```

### Remove a worktree

```bash
git worktree remove <path>
```

### Remove a worktree (with uncommitted changes)

```bash
git worktree remove --force <path>
```

### Clean up stale worktree references

```bash
git worktree prune
```

---

## Examples

### Create a new branch worktree

```bash
git worktree add .claude/worktrees/feature-a -b feature-a
```

### Create worktree from existing branch

```bash
git worktree add ../playtest-v2 main
```

---

## Delete Worktree + Branch

To fully remove a worktree and its associated branch:

```bash
# 1. Remove the worktree
git worktree remove .claude/worktrees/feature-a

# 2. Delete the branch
git branch -D feature-a
```

---

## Notes

- The main repo is stored at `.git` (not a regular directory)
- Worktrees share the same `.git` database but have their own working directory
- Avoid moving worktree directories manually—use `git worktree move` instead
- Use `git worktree list` to verify your setup

```