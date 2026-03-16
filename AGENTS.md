# AGENTS.md
> Multi-agent root config. Recognized by GitHub Copilot, Claude Code, Gemini CLI, and other AI coding agents.
> This file is self-contained. Do not rely on other files being read first.

---

## Identity & Purpose

This repo uses a document-first, multi-agent product development workflow.

**No code is written before these docs exist:**
1. Discovery → 2. PRD → 3. Roadmap → 4. Tech Spec → 5. Task Breakdown

Agents are responsible for generating, validating, and handing off these documents.

---

## Core Rules (apply to all agents)

- Every generated doc must have YAML frontmatter: `title`, `date`, `owner`, `status`
- Every generated doc must include `## Open Questions`
- Never mix product intent with engineering implementation in the same doc
- Default to smallest viable scope when the feature description is ambiguous
- If critical information is missing, ask exactly one clarifying question before proceeding
- File names use kebab-case: `my-feature-prd.md`
- Never overwrite an existing doc — append a new version or create a new file

---

## Workflow Chain

```
[Idea / Prompt]
      │
      ▼
[product-discovery.agent]  →  docs/product/{feature}-discovery.md
      │
      ▼
[prd-writer.agent]         →  docs/product/{feature}-prd.md
      │
      ▼
[roadmap-writer.agent]     →  docs/product/{feature}-roadmap.md
      │
      ▼
[tech-spec-writer.agent]   →  docs/engineering/{feature}-tech-spec.md
      │
      ▼
[task-breakdown.agent]     →  docs/engineering/{feature}-tasks.md
```

### Handoff protocol
Each agent reads the output of the previous agent before generating its doc.
Pass-forward data (minimum required context for the next agent):
- Discovery → PRD: problem statement, personas, top 3 pain points
- PRD → Roadmap: feature list, P0/P1/P2 priority, success metrics
- Roadmap → Tech Spec: Phase 1 feature list, constraints, dependencies
- Tech Spec → Tasks: component list, API endpoints, data models

---

## File Ownership

| Path | Owner agent | Do not edit with |
|------|-------------|-----------------|
| `docs/product/` | product-discovery, prd-writer, roadmap-writer | engineering agents |
| `docs/engineering/` | tech-spec-writer, task-breakdown | product agents |
| `AGENTS.md` | human | any agent |
| `CLAUDE.md` | human | any agent |

---

## Tool Permissions

| Agent | Read files | Write files | Run commands | Call APIs |
|-------|-----------|-------------|--------------|-----------|
| product-discovery | ✅ prompts/, docs/ | ✅ docs/product/ | ❌ | ❌ |
| prd-writer | ✅ docs/product/ | ✅ docs/product/ | ❌ | ❌ |
| roadmap-writer | ✅ docs/product/ | ✅ docs/product/ | ❌ | ❌ |
| tech-spec-writer | ✅ docs/product/, docs/engineering/ | ✅ docs/engineering/ | ❌ | ❌ |
| task-breakdown | ✅ docs/engineering/ | ✅ docs/engineering/ | ❌ | ❌ |

---

## Conflict Resolution

If two docs contradict each other, priority order is:
1. PRD (product intent wins)
2. Tech Spec (implementation detail wins over roadmap)
3. Roadmap
4. Discovery

Flag the conflict in `## Open Questions` of the newer doc. Do not silently resolve it.

---

## Memory & Context

All agents are **stateless by default**.
To pass context between agents, each doc ends with a `## Handoff Summary` section.
The next agent reads this section first.

---

## Detailed rules → `.github/copilot-instructions.md`
