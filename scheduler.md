---
name: scheduler
preamble-tier: 2
version: 1.0.0
description: |
  Use to schedule time-based tasks or recurring jobs.
  Trigger: /schedule [time] [task] or /cron [expression] [task]
allowed-tools:
  - Bash
  - Read
  - Write
  - Glob
  - Grep
---

# Scheduler

## Usage
Schedules and executes time-based tasks. Handles recurring jobs and one-shot reminders.

## Trigger
- `/schedule [time] [task]` - Schedule one-shot
- `/cron [expression] [task]` - Set up recurring
- `/tasks` - List scheduled tasks
- `/cancel [task-id]` - Cancel scheduled task

## Time Formats
```
+5m     - 5 minutes from now
+2h     - 2 hours from now
+1d     - 1 day from now
09:30   - Today at 09:30
every 5m - Every 5 minutes
every 1h - Every hour
every day 09:00 - Daily at 9am
```

## Task Format
```markdown
## Scheduled Task: [unique-id]
**Type:** one-shot | recurring
**Schedule:** [time/cron]
**Status:** pending | running | completed | failed | cancelled

## Task
[What to do]

## Context
[Why this was scheduled]

## Execution Log
- YYYY-MM-DD HH:MM: Executed
```

## Storage
```
~/.claude/memory/scheduler/
├── tasks/[uuid].md
└── logs/YYYY-MM-DD.md
```

## Execution
### One-Shot
1. Wait until scheduled time
2. Load context
3. Execute task
4. Log result
5. Notify user if configured

### Recurring
1. Run at schedule
2. Check if still relevant
3. Execute if relevant
4. Skip if not (log reason)
5. Continue schedule

## Constraints
- Don't run missed tasks on catch-up
- Max 100 scheduled tasks
- Always verify before executing
- Never execute without context check
