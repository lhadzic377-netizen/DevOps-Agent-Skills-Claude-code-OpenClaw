---
name: self-critic
preamble-tier: 2
version: 1.0.0
description: |
  Use after completing significant output or before reporting completion.
  Reviews own outputs and suggests improvements. Quality gates on own work.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
---

# Self-Critic

## Purpose
Reviews own outputs and suggests improvements. Quality gates on own work.

## When It Runs
- After completing significant output
- Before reporting completion
- When quality concerns arise
- Before sending response to user

## Self-Review Checklist

### CORRECTNESS
```
□ Are the facts accurate?
□ Is the logic sound?
□ Are there any errors?
□ Did I verify assumptions?
```

### COMPLETENESS
```
□ Did I answer the question?
□ Is there missing context?
□ Are edge cases covered?
□ What would user need next?
```

### CLARITY
```
□ Is it easy to understand?
□ Are there ambiguous terms?
□ Is it too verbose or too terse?
```

### APPROPRIATENESS
```
□ Does it match user's style?
□ Is the tone right?
□ Is it helpful, not just correct?
```

## Quality Thresholds
| Task Type | Min Quality | Must Have |
|----------|------------|-----------|
| Casual answer | 3/5 | Correct, friendly |
| Technical explanation | 4/5 | Accurate, complete |
| Code implementation | 4/5 | Correct, tested |
| Security/critical | 5/5 | Thorough review |

## Self-Critique Template
```markdown
## Self-Critique
### Output Quality: [1-5]
### Issues Found
1. [Issue] → [Fix]
### What Went Well
- [Positive 1]
### Revision
[If issues found, improved version]
```

## Critical Self-Check Questions
1. Would I trust this advice?
2. Is this my best work?
3. Would a senior engineer approve this?
4. Am I avoiding saying something important?

## Output
Internal review. If issues found: "Let me improve that..." then revise.

## Constraints
- Be honest with self-assessment
- Fix before moving on when possible
- Don't second-guess unnecessarily
