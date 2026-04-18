# DevOps Agent Skills

Transform Claude Code or OpenClaw into a **full development team** with 28 specialized skills.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## The Complete Skill Family

### Core Development Workflow (9 skills)
Transforms AI from code generator to development team.

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Architect** | `/architect` | Strategic vision, system design, Mermaid diagrams |
| **Planner** | `/plan` | Task breakdown, sprint backlogs, dependencies |
| **Designer** | `/design` | APIs, schemas, data models, interfaces |
| **Builder** | `/build` | Clean code from specs, tests, error handling |
| **Reviewer** | `/review` | Security, quality, BLOCK/WARN/SUGGEST |
| **Tester** | `/test` | TDD, 80%+ coverage, unit/integration/E2E |
| **Fixer** | `/fix` | Debugging, root cause analysis, reproducible bugs |
| **Risk Manager** | `/risk` | Risk identification, mitigation, contingencies |
| **Deployer** | `/deploy` | Blue/green, canary, rollback, monitoring |

### Memory & Context (6 skills)
Persistent knowledge across sessions.

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Context Smart** | auto | Loads project context before tasks |
| **Persistent Memory** | auto | Stores learnings, errors, discoveries |
| **Knowledge Librarian** | `/file` | Categorizes conversation insights |
| **Entity Tracker** | auto | Tracks people, projects, decisions |
| **Preference Memory** | `/preference` | Remembers user style, opinions |
| **Conversation Summarizer** | auto | Creates session summaries |

### Autonomous Operations (3 skills)
Continuous operation without user input.

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Autonomous Looper** | `/autonomous` | Continuous self-checking operation |
| **Scheduler** | `/schedule` | Time-based task execution |
| **Self-Monitor** | auto | Watches for issues, self-corrects |

### Thinking & Decision Making (3 skills)
Cognitive capabilities for complex problems.

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Deep Thinker** | `/think` | First-principles reasoning |
| **Decision Maker** | `/decide` | Structured decision framework |
| **Effort Adjuster** | auto | Scales effort to task complexity |

### Human Interaction (2 skills)
Natural, empathetic communication.

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Human Mode** | auto | Natural, casual communication |
| **Empathy Bridge** | auto | Acknowledges emotions, builds rapport |

### Self-Improvement (2 skills)
Continuous learning from mistakes.

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Self-Critic** | auto | Reviews own outputs, quality gates |
| **Error Archivist** | auto | Logs mistakes, creates anti-patterns |

### Bonus Skills (3 skills)
Security, performance, and research.

| Skill | Trigger | Purpose |
|-------|---------|---------|
| **Security Sense** | auto | Flags security concerns |
| **Performance Radar** | auto | Detects performance anti-patterns |
| **Research Navigator** | `/research` | Web search, documentation, fact-check |

---

## Development Workflow

```
┌─────────────┐
│  Architect  │ ← Strategic vision, system design
└──────┬──────┘
       ▼
┌─────────────┐
│   Planner   │ ← Task breakdown, sprints
└──────┬──────┘
       ▼
┌─────────────┐
│  Designer   │ ← API design, data models
└──────┬──────┘
       ▼
┌─────────────┐
│   Builder   │ ← Implementation
└──────┬──────┘
       ▼
┌─────────────┐
│  Reviewer   │ ← Code review
└──────┬──────┘
       ▼
┌─────────────┐
│   Tester    │ ← Test strategy
└──────┬──────┘
       ▼
┌─────────────┐
│   Fixer     │ ← Debugging
└──────┬──────┘
       ▼
┌─────────────┐
│  Deployer   │ ← Deployment
└─────────────┘
```

---

## Installation

### Download
Download `devops-agent-skills.zip` from this repo.

### Claude Code
```bash
unzip devops-agent-skills.zip
cp -r architect-skill/WORKFLOW/claude-code/* ~/.claude/skills/
cp -r architect-skill/MEMORY/claude-code/* ~/.claude/skills/
cp -r architect-skill/AUTONOMOUS/claude-code/* ~/.claude/skills/
cp -r architect-skill/THINKING/claude-code/* ~/.claude/skills/
cp -r architect-skill/HUMAN/claude-code/* ~/.claude/skills/
cp -r architect-skill/SELF/claude-code/* ~/.claude/skills/
cp -r architect-skill/BONUS/claude-code/* ~/.claude/skills/
```

### OpenClaw
```bash
unzip devops-agent-skills.zip
cp -r architect-skill/WORKFLOW/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
cp -r architect-skill/MEMORY/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
cp -r architect-skill/AUTONOMOUS/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
cp -r architect-skill/THINKING/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
cp -r architect-skill/HUMAN/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
cp -r architect-skill/SELF/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
cp -r architect-skill/BONUS/openclaw/* ~/.openclaw/agents/YOUR_AGENT/agent/skills/
openclaw gateway restart
```

### Memory Directory Setup
```bash
mkdir -p ~/.claude/memory/{context,learnings,decisions,discoveries,entities,preferences,projects,knowledge,summaries,scheduler/{tasks,logs},self-monitor/{health,corrections,incidents},errors/by-type,errors/by-project}
```

---

## Directory Structure

```
devops-agent-skills/
├── README.md
├── devops-agent-skills.zip
├── WORKFLOW/
│   ├── claude-code/         # 9 skills
│   └── openclaw/            # 9 skills
├── MEMORY/
│   ├── claude-code/         # 6 skills
│   └── openclaw/            # 6 skills
├── AUTONOMOUS/
│   ├── claude-code/         # 3 skills
│   └── openclaw/            # 3 skills
├── THINKING/
│   ├── claude-code/         # 3 skills
│   └── openclaw/            # 3 skills
├── HUMAN/
│   ├── claude-code/         # 2 skills
│   └── openclaw/            # 2 skills
├── SELF/
│   ├── claude-code/         # 2 skills
│   └── openclaw/            # 2 skills
└── BONUS/
    ├── claude-code/         # 3 skills
    └── openclaw/            # 3 skills
```

**Total: 28 skills × 2 formats = 56 skill files**

---

## Skill Categories Summary

| Category | Skills | Auto | Manual | Total |
|----------|--------|------|--------|-------|
| Workflow | Dev process | 0 | 9 | 9 |
| Memory | Context | 6 | 0 | 6 |
| Autonomous | Loops | 3 | 0 | 3 |
| Thinking | Decisions | 1 | 2 | 3 |
| Human | Communication | 2 | 0 | 2 |
| Self | Improvement | 2 | 0 | 2 |
| Bonus | Utilities | 2 | 1 | 3 |
| **Total** | | **16** | **12** | **28** |

---

## Memory Storage Structure

```
~/.claude/memory/
├── context/              # Current session
├── learnings/           # Error fixes, corrections
├── decisions/          # Architectural decisions
├── discoveries/        # Useful findings
├── entities/
│   ├── people/        # Tracked people
│   ├── projects/       # Tracked projects
│   └── decisions/      # Decision logs
├── preferences/        # User preferences
├── projects/          # Per-project context
├── knowledge/         # Categorized insights
├── summaries/         # Session summaries
├── scheduler/
│   ├── tasks/         # Scheduled tasks
│   └── logs/          # Execution logs
├── self-monitor/
│   ├── health/        # Health checks
│   ├── corrections/   # Self-corrections
│   └── incidents/      # Issue incidents
└── errors/
    ├── by-type/       # Errors by category
    └── by-project/    # Errors by project
```

---

## Quick Reference

### Development Lifecycle
```
/architect → /plan → /design → /build → /review → /test → /fix → /deploy
```

### Memory & Context
```
(context-smart loads at start)
(persistent-memory saves learnings)
(knowledge-librarian files insights)
(conversation-summarizer saves session)
```

### Autonomous
```
/autonomous [task]  # Start loop
/schedule [time]    # Schedule task
/stop               # Stop loop
```

### Thinking
```
/think [problem]     # Deep analysis
/decide [question]  # Make decision
(auto: effort-adjuster scales effort)
```

### Human
```
(auto: human-mode for casual tone)
(auto: empathy-bridge for emotional awareness)
```

### Self
```
(auto: self-critic reviews output)
(auto: error-archivist logs mistakes)
```

---

## Requirements

- **Claude Code:** Claude Code CLI
- **OpenClaw:** OpenClaw CLI with configured agent
- Mermaid.js (for diagrams in compatible environments)

## License

MIT License - feel free to use, modify, and distribute.
