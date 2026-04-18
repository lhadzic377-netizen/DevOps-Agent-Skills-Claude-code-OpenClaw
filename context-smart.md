---
name: context-smart
preamble-tier: 1
version: 1.0.0
description: |
  Use at session start or before significant tasks to load relevant project context.
  Auto-loads project files, recent history, user preferences, and session context.
allowed-tools:
  - Bash
  - Read
  - Glob
  - Grep
---

# Context Smart

## Purpose
Loads relevant project context before any task. Provides full situational awareness.

## When It Runs
Automatically at session start and before significant tasks.

## What It Loads

### 1. Project Structure
```bash
ls -la [project-root]/
find [project-root] -maxdepth 2 -name "*.md" -o -name "*.json" -o -name "*.yaml" 2>/dev/null | head -20
```

### 2. Recent History
- Last 5 sessions summary
- Recent files modified
- Active projects

### 3. User Preferences
Check `~/.claude/memory/preferences/` for communication style, technical opinions, workflow habits.

### 4. Session Context
- Current project name
- Recent tasks completed
- Active issues

## Memory Files Location
```
~/.claude/memory/
├── context/          # Current session context
├── projects/       # Per-project context
├── entities/        # Tracked people/projects/decisions
└── preferences/     # User preferences
```

## Context Template
```
## Current Context
### Project: [name]
### Role: [what I'm helping with]
### Recent: [what was done recently]
### Preferences: [user's style]
### Files: [key files in project]
### Active Issues: [current problems]
```

## Output
Loads context into working memory. Does NOT output to user - purely internal.

## Constraints
- Load context silently, don't announce
- If context missing, ask user
- Max 5 files to read for context
- Skip if clearly one-off question
