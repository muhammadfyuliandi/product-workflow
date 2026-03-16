# Instructions: Engineering Docs
> Scoped to: `docs/engineering/**`, `src/**`
> Applied when: editing or generating tech specs, task lists, or writing code

---

## Tech spec formatting
- YAML frontmatter required (title, date, owner, status)
- All data models must be typed (TypeScript interfaces preferred)
- All API endpoints must have request + response JSON examples
- All environment variables must be listed in the spec

## Code generation rules
- Match entity names exactly as defined in the tech spec data models
- Match API paths exactly as defined in the tech spec
- Do not introduce dependencies not listed in the tech stack table
- Every function must have a JSDoc / docstring comment
- No hardcoded values — use constants or environment variables

## File naming conventions
- Components: `PascalCase.tsx`
- Utilities / services: `kebab-case.ts`
- Tests: `{filename}.test.ts` co-located with source
- Migrations: `{timestamp}_{description}.sql`

## Error handling
- All API routes must handle and return structured errors:
  ```json
  { "error": "error_code", "message": "human readable" }
  ```
- Never return stack traces to the client
- Log errors server-side with request ID

## Security rules (non-negotiable)
- Never commit secrets, API keys, or credentials
- All user-facing routes require authentication unless explicitly listed as public in the tech spec
- SQL queries must use parameterized inputs — no string concatenation
- Validate all inputs at the API boundary

## AI / LLM code rules
- System prompts live in `src/prompts/` — never inline in business logic
- Model name comes from env var or config — never hardcoded
- Always handle API errors and timeout gracefully
- Log token usage per request for cost tracking

## Testing expectations
- Unit tests for all utility functions
- Integration tests for all API endpoints
- Test file must exist before a task can be marked done
- Test coverage target: 80% on new code

## Every engineering doc must end with
1. `## Open Questions` — flag any `⚠️ NEEDS REVIEW` items
2. `## Handoff Summary` — bullet list for the next agent or engineer
