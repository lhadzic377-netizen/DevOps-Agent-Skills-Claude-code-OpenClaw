---
name: knowledge-librarian
preamble-tier: 2
version: 1.0.0
description: |
  Use after key decisions, problem solutions, or when user explains important project info.
  Files conversation insights into organized, searchable knowledge base.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
  - Grep
---

# Knowledge Librarian

## Purpose
Files important conversation insights into organized, searchable knowledge base.

## When to File
**Auto-trigger:** Key decision made, solution found to complex problem, technical approach agreed upon.

**Manual trigger:** User says "File this under...", after significant problem solved.

## Knowledge Categories
```
~/.claude/memory/knowledge/
├── [project-name]/
│   ├── decisions/
│   ├── patterns/
│   └── architecture/
└── general/
    ├── tools/
    └── techniques/
```

## Filing Format
```markdown
# [Category]: [Brief Title]
**Project:** [project-name]
**Date:** YYYY-MM-DD
**Source:** [session context or user directive]

## Summary
[1-3 sentence summary]

## Key Points
- [Point 1]
- [Point 2]

## Details
[Full context, code snippets, links]

## Related
[[link to related knowledge]]

---
*Filed by Knowledge Librarian*
```

## Search & Retrieve
```bash
grep -r "search term" ~/.claude/memory/knowledge/
ls ~/.claude/memory/knowledge/[project]/
```

## Output
When filing: "Filed under [category]: [brief summary]"

## Constraints
- One idea per file
- Use consistent naming
- Include enough context to be useful later
- Tag generously for search
