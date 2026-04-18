---
name: autonomous-looper
preamble-tier: 2
version: 1.0.0
description: |
  Use when user wants continuous autonomous operation with self-checking and self-correction.
  Trigger: /autonomous [task] or /loop [interval] [task]
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
  - Grep
---

# Autonomous Looper

## Usage
Runs continuous autonomous operation with self-checking and self-correction.

## Trigger
- `/autonomous [task]` - Start autonomous loop
- `/loop [interval] [task]` - Run with interval
- `/stop` - Stop autonomous mode

## How It Works
```
START → CHECK → ACT → VERIFY → (LOOP) → CHECK → ...
         ↓
      PROBLEM? → FIX or ESCALATE
```

## Loop Structure

### 1. CHECK (Before each action)
- Is task still relevant?
- Any new user requests?
- Environment changed?
- Resources available?

### 2. ACT (Execute)
- Perform single atomic action
- Log action taken
- Note expected outcome

### 3. VERIFY (After each action)
- Did it work?
- Expected outcome achieved?
- Side effects?
- Time within budget?

### 4. DECIDE (Loop or Exit)
- Continue if: task relevant, within limits, no issues
- Stop if: done, blocked, time limit, user request

## Self-Correction Triggers
**Stop and ask when:**
- User explicitly requests stop
- Repeated failure (3x same action)
- New error not seen before
- Side effects detected
- User priority shift

**Self-correct silently:**
- Typo in command
- Minor environmental change
- Known fix available

## Logging
```markdown
# Autonomous Loop Log: YYYY-MM-DD HH:MM
**Task:** [what to accomplish]
**Start:** HH:MM

## Actions Taken
| Time | Action | Result |
|------|--------|--------|
| HH:MM | Did X | Success |

## Issues
- [Issue 1] → [Resolution]

## Final State
**Completed:** Yes/No
```

## Constraints
- Never act without verification step
- Max 50 iterations before reporting
- Stop immediately on user interrupt
- Log everything for debugging
- Ask if unclear on 3rd failure
- Respect resource limits
