# generate-prd.prompt.md
> On-demand prompt. Use when a discovery doc already exists and you want to generate a PRD.

---

## Instructions for the agent

1. Read `.github/agents/prd-writer.agent.md`
2. Read `docs/product/{feature}-discovery.md` — especially the `## Handoff Summary`
3. Read `.github/instructions/product-docs.instructions.md`
4. Generate a PRD following the template in the agent file
5. Save to `docs/product/{feature}-prd.md`

---

## Invoke

### Copilot Chat
```
@workspace Using .github/agents/prd-writer.agent.md and docs/product/{feature}-discovery.md, generate a PRD and save it to docs/product/{feature}-prd.md
```

### Claude Code
```bash
claude "Using .github/agents/prd-writer.agent.md and docs/product/{feature}-discovery.md, generate a PRD. Save to docs/product/{feature}-prd.md"
```

---

## Checklist before invoking
- [ ] Discovery doc exists at `docs/product/{feature}-discovery.md`
- [ ] Discovery doc status is `review` or `approved`
- [ ] `## Handoff Summary` in discovery doc is filled in
- [ ] Open questions in discovery doc are resolved or acceptable to carry forward
