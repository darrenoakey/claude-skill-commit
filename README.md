![](banner.jpg)

# Commit

A complete git workflow skill for Claude Code that ensures a clean repository state after every commit.

## Purpose

The `/commit` skill provides a streamlined, all-in-one git workflow that handles the entire commit process from staging to pushing. It eliminates the need to run multiple git commands manually and ensures your repository stays clean and synchronized.

## Features

- Initializes a git repository if one doesn't exist
- Stages all changes automatically
- Generates intelligent commit messages or uses your custom message
- Verifies the repository is completely clean after committing
- Pushes to remote if configured
- Runs `/improve` for knowledge capture
- Runs `/compact` to compress conversation context

## Installation

No installation required. This skill is available as a built-in Claude Code skill.

## Usage

### Basic Usage (Auto-generated Message)

```
/commit
```

Claude will analyze your staged changes and generate an appropriate commit message.

### Custom Commit Message

```
/commit -m "Add user authentication feature"
```

Provide your own commit message using the `-m` flag.

## Examples

### Starting a New Project

```
/commit -m "Initial commit: project scaffolding"
```

If the directory isn't a git repo yet, `/commit` will initialize it first.

### Quick Checkpoint

```
/commit
```

Stage everything, auto-generate a message based on the changes, commit, and push.

### Feature Completion

```
/commit -m "Add dark mode support with system preference detection"
```

Commit your feature with a descriptive message and push to your remote.

## What Happens

1. **Git Init** - Creates a repo if needed
2. **Stage** - Runs `git add -A` to stage all changes
3. **Commit** - Creates the commit (never bypasses pre-commit hooks)
4. **Verify** - Ensures `git status --porcelain` returns empty
5. **Push** - Pushes to remote if one is configured
6. **Improve** - Captures learnings from the session
7. **Compact** - Compresses conversation context

## Notes

- Pre-commit hooks always run (never uses `--no-verify`)
- If no remote is configured, push is skipped silently
- Works with any git hosting service (GitHub, GitLab, etc.)