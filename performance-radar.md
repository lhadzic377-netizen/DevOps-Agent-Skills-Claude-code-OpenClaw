---
name: performance-radar
preamble-tier: 2
version: 1.0.0
description: |
  Use when writing database queries, loops, API endpoints, or handling data processing.
  Detects performance anti-patterns before they cause issues.
allowed-tools:
  - Bash
  - Read
  - Grep
---

# Performance Radar

## Purpose
Detects performance anti-patterns before they cause issues.

## When It Triggers
- Writing database queries
- Loops and iterations
- API endpoints
- File operations
- Memory allocations
- Network calls

## Performance Checklist

### Database
```
□ Query complexity (N+1?)
□ Missing indexes on WHERE/JOIN
□ SELECT * when limited columns
□ Unbounded result sets
```

### Loops
```
□ Nested loops (O(n²))
□ Unnecessary iterations
□ Early exit not used
□ Cache-friendly access patterns
```

### Memory
```
□ Unbounded arrays/lists
□ Memory leaks
□ Large allocations in loops
□ String concatenation in loops
```

## Performance Flags

### CRITICAL (Fix before merge)
- N+1 query loops
- Memory leak
- Unbounded allocation

### HIGH (Optimize soon)
- Missing database index
- Inefficient algorithm
- No pagination

### MEDIUM (Consider improving)
- Redundant API calls
- No caching
- String concatenation in loop

## Common Fixes

### N+1 Query
```javascript
// BAD: N+1
for (const user of users) {
  user.posts = db.query('...', user.id)
}

// GOOD: Batch
const userIds = users.map(u => u.id)
user.posts = db.query('... WHERE user_id IN (?)', userIds)
```

### Missing Index
```sql
CREATE INDEX idx_orders_user_status ON orders(user_id, status)
```

## Performance Budget
- API response: < 200ms (p95)
- DB query: < 50ms
- Memory per request: < 100MB

## Constraints
- Don't optimize prematurely
- Measure before fixing
- Consider readability tradeoffs
