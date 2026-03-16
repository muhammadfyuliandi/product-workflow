# Instructions: Product Docs
> Scoped to: `docs/product/**`, `.github/prompts/**`
> Applied when: editing or generating discovery docs, PRDs, or roadmaps

---

## Formatting
- YAML frontmatter required on every file (title, date, owner, status)
- Headings in sentence case — never Title Case or ALL CAPS
- Status values: `draft` → `review` → `approved` → `deprecated`
- Dates: ISO 8601 (YYYY-MM-DD)

## Language & tone
- Write for a technical audience who hasn't read the discovery doc
- Use plain language — no buzzwords, no "leverage synergies"
- Passive voice is banned — "the system sends" not "a notification is sent"
- Avoid weasel words: "some", "various", "etc.", "and so on"

## Requirements writing rules
- Every requirement starts with "The system shall" or "The user can"
- Must be testable — if you cannot write a test case for it, rewrite it
- No compound requirements — one requirement per bullet
- Bad: "The system shall send an email and log the event"
- Good: REQ-001: The system shall send a confirmation email on signup
- Good: REQ-002: The system shall log all signup events

## What NOT to include in product docs
- No tech stack choices
- No database schema
- No API endpoint names
- No component names
- (All of the above belong in the tech spec)

## Tables
Use tables for: metrics, personas comparison, competitive analysis, requirement priority
Do not use tables for: prose explanations, lists of fewer than 3 items

## Every product doc must end with
1. `## Open Questions` — at least one item, or write "None — doc is complete"
2. `## Handoff Summary` — 3–5 bullets for the next agent
