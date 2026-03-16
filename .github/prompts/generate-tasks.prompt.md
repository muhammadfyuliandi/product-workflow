# generate-tasks.prompt.md
> On-demand prompt. Use when a tech spec exists and you want engineer-ready tasks.

---

## Instructions for the agent

1. Read `.github/agents/task-breakdown.agent.md`
2. Read `docs/engineering/{feature}-tech-spec.md` — especially `## Handoff Summary`
3. Read `docs/product/{feature}-prd.md` — for acceptance criteria
4. Generate task breakdown following the template in the agent file
5. Save to `docs/engineering/{feature}-tasks.md`

---

## Invoke

### Copilot Chat
```
@workspace Using .github/agents/task-breakdown.agent.md and docs/engineering/{feature}-tech-spec.md, generate an engineer task list. Save to docs/engineering/{feature}-tasks.md
```

### Claude Code
```bash
claude "Using .github/agents/task-breakdown.agent.md and docs/engineering/{feature}-tech-spec.md, generate tasks. Save to docs/engineering/{feature}-tasks.md"
```

---

## Checklist before invoking
- [ ] Tech spec exists at `docs/engineering/{feature}-tech-spec.md`
- [ ] Tech spec status is `approved`
- [ ] No `⚠️ NEEDS REVIEW` items are blocking in the tech spec
- [ ] `## Handoff Summary` in tech spec is filled in
