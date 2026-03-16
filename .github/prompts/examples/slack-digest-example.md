# Example: Slack Digest Bot
> This is a filled example of feature-brief.prompt.md — use it as a reference.

---

## Your idea
A Slack bot that summarizes unread messages in any channel when a user types `/catchup`.
It shows a bullet-point summary of the last N messages, highlights action items and decisions,
and lets the user ask follow-up questions in a thread.

---

## Context

**Who has this problem?**
PMs, engineering leads, and anyone who is async or in multiple time zones.
They miss important context after being away for a day or joining a channel late.

**What do they do today instead?**
Manually scroll back through Slack, ask colleagues to catch them up, or just stay lost.

**Why now?**
Claude API makes this feasible at low cost. Slack has a mature Bolt SDK.
Our team is remote-first and this is a recurring pain point.

**Any hard constraints?**
- Must use Slack Bolt SDK (Node.js)
- Must use Anthropic Claude API
- Should not store message content outside of the LLM call (privacy)
- Needs to ship MVP in 4 weeks with 1 engineer

**What does success look like in 90 days?**
- Used by 50+ people in our Slack workspace
- Average session saves 10+ minutes of scrolling
- NPS > 40 from active users

---

## Docs to generate
- [x] Discovery doc  →  `docs/product/slack-digest-discovery.md`
- [x] PRD            →  `docs/product/slack-digest-prd.md`
- [x] Roadmap        →  `docs/product/slack-digest-roadmap.md`
- [x] Tech Spec      →  `docs/engineering/slack-digest-tech-spec.md`
- [x] Task Breakdown →  `docs/engineering/slack-digest-tasks.md`

---

## How to invoke

### Run discovery first (Copilot Chat)
```
@workspace Read .github/prompts/examples/slack-digest-example.md and .github/agents/product-discovery.agent.md, then generate a discovery doc. Save to docs/product/slack-digest-discovery.md
```

### Then generate PRD
```
@workspace Using .github/agents/prd-writer.agent.md and docs/product/slack-digest-discovery.md, generate a PRD. Save to docs/product/slack-digest-prd.md
```

### Full pipeline via Claude Code
```bash
claude "Read CLAUDE.md. Run the full doc pipeline for the idea in .github/prompts/examples/slack-digest-example.md. Feature slug: slack-digest"
```
