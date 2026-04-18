---
name: decision-maker
preamble-tier: 1
version: 1.0.0
description: |
  Use when facing multiple options or uncertain what to do.
  Trigger: /decide [question] or /compare [option1] vs [option2]
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
---

# Decision Maker

## Purpose
Structured framework for making decisions. Evaluates options with clarity.

## Trigger
- `/decide [question]` - Make a decision
- `/compare [option1] vs [option2]` - Compare
- When facing multiple options
- When uncertain what to do

## Decision Framework

### Step 1: FRAME THE DECISION
**Define clearly:**
- What exactly needs to be decided?
- When does it need to be decided?
- Who decides if disagreement?

### Step 2: IDENTIFY OPTIONS
Always include "do nothing" as baseline.

### Step 3: EVALUATE CRITERIA
| Criteria | Weight |
|----------|--------|
| Cost (time/money) | High/Med/Low |
| Risk | High/Med/Low |
| Benefit | High/Med/Low |
| Reversibility | Easy/Hard |

### Step 4: PROS & CONS
```markdown
## Option A: [Name]
### Pros
- [Benefit 1]
### Cons
- [Drawback 1]
```

### Step 5: COMPARE
```markdown
## Comparison Matrix
| Criteria | Weight | A | B |
|----------|--------|---|---|
| Cost | 20% | 3/5 | 4/5 |
| Risk | 30% | 2/5 | 4/5 |
| **Total** | 100% | 2.6 | 3.4 |
```

### Step 6: DECIDE
- Choose highest score if clear winner
- Choose simplest if scores close
- Escalate if can't decide

### Step 7: VALIDATE
```markdown
## Validation
### What we decided: [option]
### Expected outcome: [what happens]
### How we'll know if wrong: [metrics]
```

## Decision Types
| Type | Approach |
|------|----------|
| Reversible | Favor speed |
| Irreversible | Favor caution |
| High stakes | More analysis |

## Constraints
- Never decide without clear question
- Always compare 2+ real options
- Include "do nothing" baseline
- Document reasoning
