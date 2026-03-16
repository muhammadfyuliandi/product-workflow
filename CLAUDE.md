# CLAUDE.md
> Claude Code configuration. Read automatically by `claude` CLI on every invocation.

---

## Project type
Document-first product development workflow.
This is NOT primarily a coding repo — it is a spec and doc generation system.

## What Claude Code should do here

### Primary tasks
- Generate product and engineering docs from prompts in `.github/prompts/`
- Follow agent instructions in `.github/agents/`
- Validate generated docs have required sections
- Help engineers understand specs before writing code

### How to start a new feature
```
claude "Read .github/prompts/feature-brief.prompt.md and .github/agents/product-discovery.agent.md, then generate a discovery doc for: [your idea]"
```

### Full pipeline (run in sequence)
```bash
# Step 1 — Discovery
claude "Using .github/agents/product-discovery.agent.md, generate discovery doc for [idea]. Save to docs/product/[feature]-discovery.md"

# Step 2 — PRD
claude "Using .github/agents/prd-writer.agent.md and docs/product/[feature]-discovery.md, generate PRD. Save to docs/product/[feature]-prd.md"

# Step 3 — Roadmap
claude "Using .github/agents/roadmap-writer.agent.md and docs/product/[feature]-prd.md, generate roadmap. Save to docs/product/[feature]-roadmap.md"

# Step 4 — Tech Spec
claude "Using .github/agents/tech-spec-writer.agent.md and docs/product/[feature]-prd.md, generate tech spec. Save to docs/engineering/[feature]-tech-spec.md"

# Step 5 — Tasks
claude "Using .github/agents/task-breakdown.agent.md and docs/engineering/[feature]-tech-spec.md, generate task list. Save to docs/engineering/[feature]-tasks.md"
```

## Rules for Claude Code specifically
- Always read the relevant `.github/agents/*.agent.md` file before generating any doc
- Never write application code unless a tech spec and task list already exist in `docs/engineering/`
- When writing code, use the entity names, endpoint names, and component names exactly as defined in the tech spec
- If asked to do something that skips the workflow chain, warn the user and ask if they want to proceed

## Memory
Claude Code has no memory between sessions.
Always re-read the relevant docs at the start of each session.
The `## Handoff Summary` at the bottom of each doc is the fastest way to get context.

## Bash tools allowed
- `ls`, `cat`, `find`, `grep` — reading files
- `mkdir`, `touch` — creating doc directories
- No `npm install`, `pip install`, or deployment commands without explicit user approval

## Environment variables needed
```
ANTHROPIC_API_KEY=        # if the app itself calls Claude
```
