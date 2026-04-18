---
name: effort-adjuster
preamble-tier: 1
version: 1.0.0
description: |
  Use automatically on every task to scale effort based on complexity.
  Avoids over-engineering simple tasks and under-investing in complex ones.
allowed-tools:
  - Bash
  - Read
---

# Effort Adjuster

## Purpose
Scales effort based on task complexity. Avoids over-engineering simple tasks.

## Effort Levels

| Level | When to Use | Example |
|-------|-------------|---------|
| **XS** | 30 seconds | Fix typo, answer simple question |
| **S** | 5 minutes | Simple function, one file edit |
| **M** | 30 minutes | Small feature, typical bug fix |
| **L** | 2 hours | Significant feature, code review |
| **XL** | Full day+ | Complex feature, architecture |
| **XXL** | Multi-day | Major project, system design |

## Effort Detection

### XS (Trivial)
- Single word/sentence response
- Clearly defined answer
- One file, few lines

### S (Simple)
- Simple function/class
- Well-understood domain
- < 1 hour typical

### M (Moderate)
- New feature with spec
- Non-trivial bug
- Multiple files

### L (Large)
- Complex feature
- Multiple components
- API design involved

### XL+ (Major)
- System-wide change
- New architecture
- Complex coordination

## Effort Calibration
```markdown
## Effort: [Level]
### Task Complexity: [1-5]
### Code Scope: [Lines estimate]
### Requirements: [Clear/vague]
### Reasoning: [Why this level]
```

## Effort Capping
- If user says "quick fix" → cap at S
- If user says "simple" → cap at M
- If unclear → start S, scale up
- If task grows → stop and report

## Speed vs Quality
| Task | Speed | Checkpoints |
|------|-------|-------------|
| XS-S | Fast | User confirms |
| M | Normal | Test, review |
| L | Careful | Multiple reviews |
| XL+ | Gradual | Phase gates |

## Output
Internal calibration. Reports level if asked.

## Constraints
- Start lower, scale up - never over-engineer
- Ask if unclear constraint
- Respect "quick" requests
