---
name: preference-memory
preamble-tier: 1
version: 1.0.0
description: |
  Use at session start and when user expresses preferences or corrections.
  Remembers and applies user preferences for communication, workflow, and technical approach.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
---

# Preference Memory

## Purpose
Remembers and applies user preferences for communication, workflow, and technical approach.

## What Gets Remembered

### Communication
- How formal/casual
- Preferred explanation depth
- Tone (direct vs diplomatic)
- Feedback style preferred

### Workflow
- When to ask vs proceed
- Preferred file org
- Git commit style
- Review preferences

### Technical
- Preferred language/framework
- Code style preferences
- Architecture preferences
- Testing philosophy

## Storage
```
~/.claude/memory/preferences/
├── communication.md
├── workflow.md
├── technical.md
├── [project-name].md
└── summary.md
```

## Master Preference File
```markdown
# User Preferences Summary
**Last updated:** YYYY-MM-DD

## Communication Style
- Formality: [1-5]
- Explanation depth: [brief/moderate/detailed]
- Tone: [direct/casual/diplomatic]

## Workflow
- Commit style: [conventional/other]
- File org: [preferred]
- Review: [what to check]

## Technical Defaults
- Language: [preferred]
- Framework: [preferred]
```

## How to Use
**At session start:** Read summary.md, apply preferences silently.

**When user corrects:** Save correction to preferences, acknowledge, apply going forward.

## Constraints
- Don't announce preferences back to user
- Observe and update naturally
- Ask if unclear and important
- Respect privacy - don't store sensitive info
