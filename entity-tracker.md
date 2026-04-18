---
name: entity-tracker
preamble-tier: 2
version: 1.0.0
description: |
  Use when learning about people, projects, or making decisions.
  Tracks persistent entities across sessions: people, projects, decisions.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
---

# Entity Tracker

## Purpose
Tracks persistent entities across sessions: people, projects, decisions, and their relationships.

## What Gets Tracked

### People
- Names and roles
- Expertise areas
- Preferences and communication style
- Projects worked on together

### Projects
- Name and purpose
- Current status
- Key files and structure
- Active issues
- Decisions made

### Decisions
- What was decided
- Why approach was chosen
- Alternatives considered
- Date made
- Who approved

## Entity Files
```
~/.claude/memory/entities/
├── people/[name].md
├── projects/[project-name].md
└── decisions/[project-name]/YYYY-MM-DD_decision.md
```

## Person Template
```markdown
# Person: [Name]
**Role:** [job title]
**Since:** [when first met]

## Expertise
- [Skill 1]
- [Skill 2]

## Preferences
- Communication: [style]
- Technical: [preferences]

## Projects
- [[project-name]] - [role]
```

## Project Template
```markdown
# Project: [Name]
**Status:** [active/completed]
**Started:** YYYY-MM-DD

## Overview
[Description]

## Team
- [[person-name]] - [role]

## Key Decisions
- [[decision]] - [brief]
```

## Constraints
- Update on each interaction
- Link related entities
- Keep current with recent info
- Don't invent info - record only what user provides
