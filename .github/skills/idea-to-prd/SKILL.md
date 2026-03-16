# SKILL: idea-to-prd
> Full pipeline skill. One invocation generates Discovery + PRD + Roadmap in sequence.
> For Copilot Extensibility / agent skill runners.

---

## What this skill does
Takes a raw idea (from a feature brief or inline text) and runs it through:
1. product-discovery.agent → generates discovery doc
2. prd-writer.agent → generates PRD from discovery
3. roadmap-writer.agent → generates roadmap from PRD

All three docs are saved to `docs/product/`.

---

## Inputs required
| Input | Source | Required |
|-------|--------|----------|
| `feature_slug` | user provides (e.g. `slack-digest`) | ✅ |
| `idea_text` | inline or from a `.prompt.md` file | ✅ |
| `constraints` | optional, from brief | ❌ |

---

## Steps

### Step 1 — Discovery
```
Agent: product-discovery.agent.md
Input: idea_text, constraints
Output: docs/product/{feature_slug}-discovery.md
Validation: file exists AND contains "## Handoff Summary"
```

### Step 2 — PRD
```
Agent: prd-writer.agent.md
Input: docs/product/{feature_slug}-discovery.md (Handoff Summary section)
Output: docs/product/{feature_slug}-prd.md
Validation: file exists AND contains "## Functional Requirements"
```

### Step 3 — Roadmap
```
Agent: roadmap-writer.agent.md
Input: docs/product/{feature_slug}-prd.md (Handoff Summary section)
Output: docs/product/{feature_slug}-roadmap.md
Validation: file exists AND contains "## Phase 1"
```

---

## Invoke via Copilot Chat
```
@workspace Run the .github/skills/idea-to-prd/SKILL.md pipeline for this idea:
[paste your idea here]
Feature slug: my-feature-name
```

## Invoke via Claude Code
```bash
claude "Read .github/skills/idea-to-prd/SKILL.md and run the full pipeline for this idea: [your idea]. Feature slug: my-feature-name. Save all docs to docs/product/"
```

---

## Failure handling
- If Step 1 fails or produces an empty doc, stop and ask the user to clarify the idea
- If the discovery doc has more than 3 unresolved open questions, warn before proceeding to PRD
- If PRD contains `⚠️ BLOCKED` requirements, warn before proceeding to roadmap
- Never skip a step — each doc depends on the previous one's Handoff Summary

---

## Output checklist
After running this skill, you should have:
- [ ] `docs/product/{feature_slug}-discovery.md` — status: draft
- [ ] `docs/product/{feature_slug}-prd.md` — status: draft
- [ ] `docs/product/{feature_slug}-roadmap.md` — status: draft

Next step: review docs, update status to `review`, then run `tech-spec-writer.agent.md`
