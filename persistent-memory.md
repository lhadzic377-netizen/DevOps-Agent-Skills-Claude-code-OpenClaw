---
name: persistent-memory
preamble-tier: 2
version: 1.0.0
description: |
  Use when user corrects you, you discover a better approach, or an error is fixed.
  Stores learnings, decisions, and discoveries across sessions.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
  - Grep
---

# Persistent Memory

## Purpose
Stores and retrieves learnings across sessions. Enables continuous improvement.

## What Gets Remembered

### Learnings (auto-captured)
- Errors and how they were fixed
- User corrections ("No, that's wrong...")
- Discovered better approaches
- API quirks or behaviors

### Decisions (captured when made)
- Why a particular approach was chosen
- Trade-offs considered
- Rejected alternatives

### Discoveries (captured when found)
- Useful tools or techniques
- Project-specific patterns
- Performance insights

## Memory Structure
```
~/.claude/memory/
├── learnings/       # YYYY-MM-DD_learning.md
├── decisions/       # YYYY-MM-DD_decision.md
├── discoveries/      # YYYY-MM-DD_discovery.md
└── context/         # current.md
```

## When to Save
**Auto-trigger:** User corrections, long error fixes, better approaches discovered, API failures.

**Manual trigger:** User says "Remember that...", you discover something worth saving.

## Memory Format
```markdown
# Learning: [Brief Title]
**Date:** YYYY-MM-DD
**Context:** [When this happened]
**What happened:** [The issue/situation]
**Resolution:** [How it was fixed/handled]
**Apply when:** [When to use this knowledge]
```

## How to Retrieve
Before significant tasks, check relevant memories:
```bash
grep -r "keyword" ~/.claude/memory/learnings/
ls -t ~/.claude/memory/learnings/ | head -5
```

## Output
When finding relevant memory: "I recall we learned that [brief summary]. Applying it now."

## Constraints
- Save atomic facts, not entire conversations
- Include date for recency
- Use search-friendly keywords
- Don't overwrite - append new learnings
