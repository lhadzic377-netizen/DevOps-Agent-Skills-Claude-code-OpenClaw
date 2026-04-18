---
name: security-sense
preamble-tier: 1
version: 1.0.0
description: |
  Use when writing authentication, handling user input, database queries, or API endpoints.
  Automatically flags security concerns before they become issues.
allowed-tools:
  - Bash
  - Read
  - Grep
---

# Security Sense

## Purpose
Automatically flags security concerns. Prevents security issues before they happen.

## When It Triggers
- Writing authentication/authorization code
- Handling user input
- Database queries
- File operations
- API endpoints
- Password/secret handling

## Security Checklist

### Authentication
```
□ Passwords hashed (bcrypt/argon2)
□ Tokens properly validated
□ No hardcoded credentials
□ Proper logout handling
```

### Authorization
```
□ Users can only access own data
□ Admin routes protected
□ Role checks before actions
□ Resource ownership verified
```

### Input Validation
```
□ All user input sanitized
□ SQL parameterized queries
□ No eval() or dynamic code
□ File paths validated
```

## Security Flags

### CRITICAL (Block and fix)
- Hardcoded password/secret
- SQL injection possible
- Missing auth on protected route

### HIGH (Warn and require)
- Weak password hashing
- CSRF possible
- Unvalidated redirects

### MEDIUM (Suggest fix)
- Missing rate limiting
- Verbose errors in prod

## Safe Patterns

### SQL Injection Prevention
```sql
-- BAD
"SELECT * FROM users WHERE id = " + userId

-- GOOD
"SELECT * FROM users WHERE id = ?"
```

### Password Hashing
```javascript
// BAD
hash(password, 'md5')

// GOOD
bcrypt.hash(password, 12)
```

## Constraints
- Flag issues before implementation
- Never implement known insecure pattern
- When in doubt, error on secure side
