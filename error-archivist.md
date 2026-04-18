---
name: error-archivist
preamble-tier: 2
version: 1.0.0
description: |
  Use when making mistakes, failures, or discovering anti-patterns.
  Logs mistakes, failures, and anti-patterns for institutional memory.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
---

# Error Archivist

## Purpose
Logs mistakes, failures, and anti-patterns. Creates institutional memory.

## What Gets Archived

### Errors Made
- Factual mistakes
- Logic errors
- Misunderstanding of requirements
- Missed edge cases

### Failures
- Approaches that didn't work
- Over-engineered solutions
- Wrong assumptions

### Anti-Patterns
- What not to do in this codebase
- Common mistakes in domain
- Deprecated approaches

## Archive Structure
```
~/.claude/memory/errors/
├── YYYY-MM-DD/
│   ├── error.md
│   └── anti-pattern.md
├── by-type/
│   ├── logic-errors/
│   └── anti-patterns/
└── by-project/
    └── [project-name]/
```

## Error Template
```markdown
# Error: [Brief Title]
**Date:** YYYY-MM-DD
**Severity:** Low / Medium / High / Critical
**Project:** [project]

## What Happened
[Description]

## Root Cause
[Why it happened]

## Correction
[How I fixed it]

## Prevention
- [ ] Don't do [this]
- [ ] Always check [that]

## Tags
#error #type #project
```

## Failure Template
```markdown
# Failure: [Brief Title]
**Date:** YYYY-MM-DD
**Approach:** [what I tried]

## Why It Failed
[Specific reasons]

## Lessons Learned
1. [Lesson 1]
2. [Lesson 2]

## Don't Do This
[Clear anti-pattern statement]
```

## How to Use Archives
```bash
grep -r "similar situation" ~/.claude/memory/errors/
```

## Constraints
- Be specific, not vague
- Include actionable prevention
- Categorize correctly
- Review anti-patterns quarterly
