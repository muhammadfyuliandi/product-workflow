---
title: "Tech Spec: {Feature Name}"
date: YYYY-MM-DD
owner: ""
status: draft
---

# Tech Spec: {Feature Name}

> Copy this template. Rename to `{feature-slug}-tech-spec.md`.
> Or generate automatically: see `.github/agents/tech-spec-writer.agent.md`

## Scope
Phase 1 only (REQ-001, REQ-002, ...). Links to PRD: `docs/product/{feature}-prd.md`

## Tech stack decision
| Layer | Choice | Reason |
|-------|--------|--------|
| Runtime | | |
| Framework | | |
| Database | | |
| Auth | | |
| AI/LLM | claude-sonnet-4-20250514 | |
| Hosting | | |

## System diagram
```
[describe components and connections in ASCII]

Client → API Server → DB
              └──────→ Claude API
```

## Data models

### {EntityName}
```typescript
interface EntityName {
  id: string;        // UUID v4
  field1: string;    // description
  field2: number;    // description
  createdAt: Date;
  updatedAt: Date;
}
```

## API design

### POST /api/v1/{resource}
**Auth:** Bearer token required
**Purpose:** Satisfies REQ-001

Request:
```json
{
  "field1": "string"
}
```

Response 200:
```json
{
  "id": "uuid",
  "field1": "string",
  "createdAt": "ISO8601"
}
```

Response 400:
```json
{ "error": "validation_failed", "message": "field1 is required" }
```

## Environment variables
```
ANTHROPIC_API_KEY=
DATABASE_URL=
JWT_SECRET=
```

## Security decisions
- All routes require authentication except:
- Rate limiting: X req/min per user

## Scalability notes
-

## What is NOT in this spec
- (anything deferred to Phase 2+)

## Open Questions
- [ ] ⚠️ NEEDS REVIEW: Question — owner: TBD

## Handoff Summary
> For task-breakdown.agent — read this before generating tasks.
- Components to build:
- API endpoints:
- Data models:
- External services:
- Biggest technical risk:
- Suggested first task:
