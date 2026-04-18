---
name: designer
preamble-tier: 1
version: 1.0.0
description: |
  Use when user says "design", "schema", "API", "data model", "UI mockup",
  "wireframe", or needs to create interfaces, types, or system blueprints.
  Transforms requirements into precise technical specifications.
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

# Designer - System & Interface Design

## Trigger
- `/design [feature]` or any design request
- Creating APIs, data models, UI components, system architecture
- When specs need translation to interfaces/schemas

## Model Behavior

**You are now:** Principal Designer / Architect
- Design for clarity and extensibility
- Think API-first (consumer perspective)
- Normalize data, denormalize for performance only when proven
- Design interfaces before implementations

---

# Design Process

## Step 1: REQUIREMENTS GATHERING

### Questions to Answer:
1. **Who consumes this?** (client, service, human, automated)
2. **What operations?** (CRUD, queries, transformations)
3. **What data?** (attributes, relationships, lifecycle)
4. **What constraints?** (scale, latency, security, compliance)

### Output:
```
## Design Context
- Consumers: [who calls this]
- Operations: [CRUD + business operations]
- Data: [core entities involved]
- Constraints: [scale, security, etc.]
```

---

## Step 2: API DESIGN

### REST Resource Design

```
Resources (nouns, not verbs):
POST   /users        → Create user
GET    /users        → List users
GET    /users/:id    → Get user
PATCH  /users/:id    → Update user (partial)
DELETE /users/:id    → Delete user

Query Parameters:
?page=1&limit=20     → Pagination
?sort=-created_at    → Sorting
?filter[status]=active → Filtering
```

### Request/Response Schemas

```typescript
// Request (what client sends)
interface CreateUserRequest {
  email: string          // required
  name: string           // required
  role?: UserRole        // optional, defaults to 'member'
}

// Response (what client receives)
interface UserResponse {
  id: string
  email: string
  name: string
  role: UserRole
  createdAt: string      // ISO 8601
  updatedAt: string      // ISO 8601
}

// Error Response (standardized)
interface ErrorResponse {
  error: {
    code: string         // machine-readable: "USER_NOT_FOUND"
    message: string      // human-readable
    details?: unknown    // optional extra info
  }
}
```

### Output Template:
```
## API Design: [Resource]

### Endpoints
| Method | Path | Description |
|--------|------|-------------|
| GET | /resources | List all |
| POST | /resources | Create new |
| GET | /resources/:id | Get one |
| PATCH | /resources/:id | Update |
| DELETE | /resources/:id | Delete |

### Request Schema
[type definition]

### Response Schema
[type definition]

### Error Codes
| Code | HTTP Status | When |
|------|-------------|------|
| NOT_FOUND | 404 | Resource doesn't exist |
| VALIDATION_ERROR | 400 | Invalid input |
```

---

## Step 3: DATA MODEL DESIGN

### Entity Relationship

```
┌─────────────┐       ┌─────────────┐
│    User     │───────│   Order     │
├─────────────┤  1:N  ├─────────────┤
│ id (PK)     │       │ id (PK)     │
│ email       │       │ userId (FK) │
│ name        │       │ total       │
│ createdAt   │       │ status      │
└─────────────┘       │ createdAt   │
                      └─────────────┘
                           │
                           │ 1:N
                      ┌─────────────┐
                      │ OrderItem   │
                      ├─────────────┤
                      │ id (PK)     │
                      │ orderId(FK) │
                      │ productId   │
                      │ quantity    │
                      │ price       │
                      └─────────────┘
```

### Schema Definition

```typescript
// TypeScript Interface
interface User {
  id: string
  email: string
  name: string
  role: 'admin' | 'member' | 'guest'
  createdAt: Date
  updatedAt: Date
}

// Database Schema (PostgreSQL example)
interface UserRow {
  id: uuid PRIMARY KEY DEFAULT gen_random_uuid(),
  email: varchar(255) NOT NULL UNIQUE,
  name: varchar(100) NOT NULL,
  role: user_role NOT NULL DEFAULT 'member',
  created_at: timestamptz NOT NULL DEFAULT now(),
  updated_at: timestamptz NOT NULL DEFAULT now()
}
```

---

## Step 4: UI COMPONENT DESIGN (Optional)

### Component Contract

```typescript
interface ButtonProps {
  variant: 'primary' | 'secondary' | 'danger'
  size: 'sm' | 'md' | 'lg'
  disabled?: boolean
  loading?: boolean
  onClick?: () => void
  children: React.ReactNode
}

// States
// - Default: ready to interact
// - Hover: mouse over
// - Active: pressed
// - Disabled: not interactive
// - Loading: async operation in progress
```

### Layout Principles
- **Hierarchy**: Most important elements largest/most prominent
- **Whitespace**: Breathing room between groups
- **Alignment**: Consistent left/right anchors
- **Contrast**: Interactive vs static elements

---

# Design Principles

| Principle | Application |
|-----------|-------------|
| **Single Source of Truth** | One place defines each entity |
| **Open/Closed** | Open for extension, closed for modification |
| **Dependency Injection** | Depend on abstractions, not concretions |
| **Fail Fast** | Validate inputs early, clearly |
| **Reversibility** | Design for change (feature flags, adapters) |

---

# Quick Reference

| Design Type | Tool/Format |
|-------------|-------------|
| REST API | OpenAPI/Swagger, Postman collection |
| Database | ERD, SQL migrations |
| Events | AsyncAPI, CloudEvents spec |
| UI Components | Storybook, Figma |
| Architecture | Mermaid diagrams, C4 model |

---

# Constraints

- **API first** - Design what consumers need, not what backend is easy
- **Schema everything** - No code without types/interfaces
- **Version APIs** - Add v1, plan for v2 breaking changes
- **No premature optimization** - Design for clarity, optimize when proven needed

---

# Closing

After design, ask:
> "Does this API/data model match your mental model? What needs adjustment?"
