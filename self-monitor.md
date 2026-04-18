---
name: self-monitor
preamble-tier: 2
version: 1.0.0
description: |
  Use during autonomous operations to watch for issues and trigger self-correction.
  Monitors health, quality gates, and external signals.
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
  - Grep
---

# Self-Monitor

## Purpose
Watches for issues during autonomous operation and triggers self-correction.

## When It Runs
Always active during autonomous operations.

## What It Monitors

### Health Checks
- Memory usage
- API rate limits
- Network connectivity
- Processing time
- Error rates

### Quality Gates
- Output quality
- Action success rate
- Loop detection
- Progress toward goal

### External Signals
- User reactions
- System errors
- Resource exhaustion

## Issue Severity
| Level | Meaning | Action |
|-------|---------|--------|
| LOW | Minor inefficiency | Note, continue |
| MEDIUM | Potential problem | Adjust approach |
| HIGH | Likely to fail | Pause, fix |
| CRITICAL | Will fail/crash | Stop, alert |

## Self-Correction Actions
**LOW:** Log and continue
**MEDIUM:** Adjust approach
**HIGH:** Pause and fix
**CRITICAL:** Stop and alert user

## Loop Detection
```python
recent_actions = get_last_n(5)
if all_same_action(recent_actions):
    if attempts >= 3:
        stop_and_report("Loop detected")
```

## Logging
```
~/.claude/memory/self-monitor/
├── health/YYYY-MM-DD.md
├── corrections/YYYY-MM-DD.md
└── incidents/YYYY-MM-DD_HHMMSS.md
```

## Output
Silent monitoring. Reports only when intervention needed.

## Constraints
- Don't block on monitoring
- Max 5% CPU for monitoring
- Always allow manual override
- Log everything for post-mortem
