# feature-brief.prompt.md
> Fill this in when you have a new idea. This is the starting point for the entire workflow.
> Save a copy as `.github/prompts/{your-feature}-brief.prompt.md`

---

## Your idea
Write it as raw as you want. One sentence or ten, doesn't matter.

```
[WRITE YOUR IDEA HERE]
```

---

## Context (answer what you know, leave blank what you don't)

**Who has this problem?**
```
[e.g. PMs at startups, solo developers, customer support teams...]
```

**What do they do today instead?**
```
[e.g. spreadsheets, Slack messages, nothing...]
```

**Why now? What's changed?**
```
[e.g. new API available, competitor launched, user research revealed...]
```

**Any hard constraints?**
```
[e.g. must integrate with Slack, must ship in 4 weeks, no new infra...]
```

**What does success look like in 90 days?**
```
[e.g. 100 active users, X% retention, replaces spreadsheet for team...]
```

---

## Docs to generate
Check what you need:

- [ ] Discovery doc  →  `docs/product/{feature}-discovery.md`
- [ ] PRD            →  `docs/product/{feature}-prd.md`
- [ ] Roadmap        →  `docs/product/{feature}-roadmap.md`
- [ ] Tech Spec      →  `docs/engineering/{feature}-tech-spec.md`
- [ ] Task Breakdown →  `docs/engineering/{feature}-tasks.md`

---

## How to invoke (pick your tool)

### GitHub Copilot Chat (VS Code)
```
@workspace Read .github/prompts/{this-file}.prompt.md and .github/agents/product-discovery.agent.md, then generate a discovery doc for this feature. Save to docs/product/{feature}-discovery.md
```

### Claude Code (terminal)
```bash
claude "Read .github/prompts/{this-file}.prompt.md and .github/agents/product-discovery.agent.md, generate a discovery doc. Save to docs/product/{feature}-discovery.md"
```

### Run full pipeline (Claude Code)
```bash
claude "Read CLAUDE.md and run the full doc pipeline for the idea in .github/prompts/{this-file}.prompt.md"
```
