---
name: deep-thinker
preamble-tier: 1
version: 1.0.0
description: |
  Use when facing complex, non-obvious problems or when conventional approaches fail.
  Trigger: /think [problem] or /analyze [situation]
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
  - Grep
---

# Deep Thinker

## Purpose
Applies first-principles reasoning to complex problems. Think through difficult problems systematically.

## Trigger
- `/think [problem]` - Apply deep thinking
- `/analyze [situation]` - Deep analysis
- When facing non-obvious solution
- When stuck on problem
- When conventional approaches fail

## First Principles Framework

### Step 1: DECONSTRUCT
Break problem into fundamental truths:
- What do we KNOW is true?
- What do we ASSUME is true?
- What do we NOT know?

### Step 2: CHALLENGE ASSUMPTIONS
For each assumption:
- Is this really true?
- What if the opposite is true?
- What evidence supports this?

### Step 3: REBUILD FROM TRUTH
```python
FACT_1 + FACT_2 = INSIGHT_A
INSIGHT_A + FACT_3 = INSIGHT_B
... → SOLUTION
```

### Step 4: PROVE WRONG TEST
Try to disprove reasoning:
- What evidence would falsify this?
- Find the weakest point
- Strengthen or abandon

## Thinking Template
```markdown
# Deep Thought: [Problem]
**Complexity:** High / Very High

## The Problem
[Restate in simplest terms]

## What We Know (Facts)
1. [Fact 1]
2. [Fact 2]

## Assumptions (Need to Verify)
1. [Assumption] → [What would prove false]

## Reasoning Chain
```
[FACT] + [FACT] = [INSIGHT]
```

## Conclusion
[What we believe to be true]

## What Would Change Our Mind
[Test conditions]
```

## When to Use
**High value:** Strategic decisions, architecture choices, unfamiliar domains, after failed conventional approaches.

**Lower value:** Simple questions, routine tasks, well-understood domains, time-pressured situations.

## Constraints
- Time-box to 10 minutes max
- Document reasoning for others
- Challenge own assumptions first
