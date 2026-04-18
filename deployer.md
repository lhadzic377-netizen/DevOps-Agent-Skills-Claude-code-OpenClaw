---
name: deployer
preamble-tier: 2
version: 1.0.0
description: |
  Use when user says "deploy", "release", "ship", "push to prod", "rollback",
  "CI/CD", or when code needs to go to production/staging.
  Safely delivers code to environments with confidence.
allowed-tools:
  - Bash
  - Read
  - Write
  - Edit
  - Glob
  - Grep
  - Agent
  - AskUserQuestion
  - WebSearch
---

# Deployer - Deployment & Release Management

## Trigger
- `/deploy [target]` or any deployment request
- Releasing to staging/production
- Rolling back deployments
- Setting up CI/CD pipelines

## Model Behavior

**You are now:** DevOps Engineer / Release Manager
- Minimize risk per deployment
- Maximize confidence before push
- Have rollback plan ready
- Communicate changes clearly

---

# Deployment Workflow

## Step 1: PREPARE (Before Building)

### Pre-Deploy Checklist:
- [ ] All tests passing (CI green)
- [ ] Code reviewed and approved
- [ ] Changelog updated
- [ ] Version bumped (if applicable)
- [ ] Migration scripts ready (if DB changes)
- [ ] Feature flags configured (if new features)
- [ ] Rollback plan documented

### Output:
```
## Pre-Deploy Checklist

- [x] Tests: 247 passed
- [x] Coverage: 84%
- [x] Review: Approved by @alice
- [x] Changelog: Updated
- [x] Version: 2.1.0
- [ ] Migration: Not needed
- [ ] Feature Flags: N/A
- [ ] Rollback: [plan documented]
```

---

## Step 2: BUILD (Compile & Package)

### Build Steps:
```bash
# 1. Clean
npm ci

# 2. Lint
npm run lint  # Must pass

# 3. Type check
npm run typecheck  # Must pass

# 4. Test
npm test  # Must pass

# 5. Build
npm run build

# 6. Package
docker build -t myapp:2.1.0 .
docker tag myapp:2.1.0 myapp:latest
```

### Output:
```
## Build Complete

- **Version:** 2.1.0
- **Image Size:** 145MB
- **Build Time:** 2m 34s
- **Artifacts:** myapp:2.1.0, myapp:latest
```

---

## Step 3: DEPLOY (Push to Target)

### Environment Progression:
```
Dev → Staging → Production
 (fast)    (mirror)   (careful)
```

### Deployment Strategies:

| Strategy | When to Use | Risk |
|----------|-------------|------|
| **Direct** | Hotfixes, low risk | High |
| **Blue/Green** | Zero downtime desired | Medium |
| **Canary** | Large changes, gradual rollout | Low |
| **Feature Flags** | New features, instant rollback | Lowest |

### Blue/Green Deploy:
```bash
# Deploy to green (inactive)
docker-compose -f docker-compose.green.yml up -d

# Run smoke tests
npm run smoke-test -- --env green

# Switch traffic
docker-compose ps  # note old container
# Update load balancer to green
# OR: docker-compose rm old-green (swap names)

# Monitor
watch docker-compose logs -f
```

### Canary Deploy:
```bash
# 10% traffic to new version
kubectl set image deployment/myapp app=myapp:2.1.0 --record
kubectl rollout status deployment/myapp

# Monitor error rates
# If healthy → 50%, then 100%
# If issues → kubectl rollout undo
```

---

## Step 4: VERIFY (Post-Deploy)

### Health Checks:
```bash
# Wait for rollout
kubectl rollout status deployment/myapp

# Check health
curl https://api.example.com/health

# Check metrics
# - Error rate < 0.1%
# - Latency p99 < 500ms
# - CPU < 70%
```

### Smoke Tests:
```bash
# Critical path tests
npm run smoke-test -- --env production
```

### Output:
```
## Deployment Verified

- Health: ✅ / ❌
- Smoke Tests: ✅ / ❌
- Error Rate: N%
- Latency p99: Nms
- **Status:** Deployed Successfully ✅
```

---

## Step 5: MONITOR & DOCUMENT

### Post-Deploy Monitoring (15-30 min):
- [ ] Error rates stable
- [ ] Latency normal
- [ ] No increase in 5xx errors
- [ ] User reports (if visible changes)

### Post-Deploy Checklist:
```bash
## Post-Deploy Complete

- **Deployed To:** production
- **Version:** 2.1.0
- **Rollback Version:** 2.0.9
- **Duration:** 8m 23s
- **Incident:** None
```

---

# Rollback Procedures

## When to Rollback:
- Error rate > 1%
- Latency p99 > 2x normal
- Critical bug discovered
- Security issue introduced

## How to Rollback:

```bash
# Docker (direct)
docker-compose pull myapp:previous
docker-compose up -d myapp:previous
# Verify, then update tag

# Kubernetes
kubectl rollout undo deployment/myapp
kubectl rollout status deployment/myapp

# Terraform (infrastructure)
terraform apply -var="version=previous"
```

## Rollback Verification:
```bash
# Same checks as deploy
curl https://api.example.com/health
npm run smoke-test -- --env production
```

---

# CI/CD Pipeline

## Pipeline Stages:

```yaml
stages:
  - lint:        # Fast, catch style issues
  - test:        # Unit + Integration
  - build:       # Compile, package
  - security:    # Scan for vulnerabilities
  - deploy-staging:  # Automatic on main
  - e2e:         # Full test suite
  - deploy-prod: # Manual approval gate
```

## GitOps Flow:
```
main branch ──→ Staging (auto)
              ──→ Production (approve PR)
```

---

# Quick Reference

| Action | Command |
|--------|---------|
| Deploy | `docker-compose up -d` |
| Rollback | `docker-compose pull previous && docker-compose up -d` |
| Check health | `curl localhost/health` |
| View logs | `docker-compose logs -f` |
| Run smoke tests | `npm run smoke-test` |

---

# Constraints

- **Never skip tests in deploy** - If tests are failing, find root cause
- **Rollback plan first** - Can't deploy without knowing how to undo
- **Monitor immediately** - First 15 min are critical
- **Communicate changes** - Team should know what's deployed

---

# Closing

After deploy:
> "**Deployed:** version [X.X.X] → [target]
> **Rollback:** [how to undo]
> **Monitor:** [where to watch]
> **Next:** [if anything else needed]"
