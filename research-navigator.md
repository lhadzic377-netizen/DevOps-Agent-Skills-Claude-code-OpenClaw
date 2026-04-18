---
name: research-navigator
preamble-tier: 2
version: 1.0.0
description: |
  Use when user asks to research, search, lookup, or verify information.
  Trigger: /research [topic], /search [query], /lookup [term], /verify [claim]
allowed-tools:
  - Bash
  - WebSearch
  - WebFetch
---

# Research Navigator

## Purpose
Efficient web search, documentation lookup, and fact verification.

## Trigger
- `/research [topic]` - Research topic
- `/search [query]` - Quick search
- `/lookup [term]` - Documentation lookup
- `/verify [claim]` - Verify fact

## Research Workflow

### Step 1: CLARIFY RESEARCH GOAL
- What specifically do we need to know?
- Why do we need this?
- How current does this need to be?

### Step 2: IDENTIFY SOURCES
1. Official documentation
2. Academic papers
3. Authoritative guides
4. Well-vetted blog posts

### Step 3: SEARCH STRATEGY
```bash
# Official docs first
site:docs.example.com [topic]

# Specific library
[library] documentation

# Quality blog
[topic] best practices guide
```

### Step 4: VERIFY & SYNTHESIZE
- Cross-reference multiple sources
- Check publication date
- Note consensus vs debate
- Prioritize actionable info

## Research Output Template
```markdown
# Research: [Topic]
**Confidence:** High / Medium / Low
**Sources:** N verified

## Executive Summary
[1-2 sentence answer]

## Key Findings
1. [Finding with citation]
2. [Finding with citation]

## Source Quality
| Source | Reliability | Date |
|--------|-------------|------|
| [source] | High | YYYY |

## Actionable Recommendations
1. [Recommendation]

## Sources
- [Source 1](url)
```

## Search Tips
```
# Finding best practices
"[technology]" best practices 2024

# Finding troubleshooting
"[error]" fix

# Finding comparisons
"[A] vs [B]" comparison
```

## Constraints
- Always cite sources
- Note confidence level
- Don't make up information
- Verify before stating as fact
- 5 min max for simple, 15 min for deep
