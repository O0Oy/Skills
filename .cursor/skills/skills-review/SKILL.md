---
name: skills-review
description: >-
  Review and optimize installed skills based on usage experience. Use when the
  user wants to improve a skill, reports a skill didn't work well, says
  "review skills", "optimize skills", or after completing a significant
  workflow using mattpocock skills.
---

# Skills Review — Continuous Improvement Loop

A feedback loop for evolving skills based on real usage. Run this after completing a significant workflow, or when a skill underperformed.

## The Loop

```
USE → OBSERVE → RECORD → ANALYZE → IMPROVE → USE
```

### 1. Observe — What happened?

Ask the user:
- Which skill(s) did you use?
- What went well?
- What friction did you experience?
- Did the agent misunderstand anything?
- Was any step missing or unnecessary?

### 2. Record — Capture the feedback

Append to `docs/skills-changelog.md` (create lazily):

```markdown
## YYYY-MM-DD — [skill-name]

**Context**: What you were doing
**Worked**: What the skill did well
**Friction**: What didn't work or felt wrong
**Action**: What to change (or "observe more")
```

### 3. Analyze — Diagnose the issue

Use the `/writing-great-skills` vocabulary to diagnose:

| Symptom | Diagnosis | Fix |
|---------|-----------|-----|
| Agent skipped steps | **Premature completion** — completion criterion too vague | Sharpen the criterion |
| Agent did too much/wrong thing | **Negation** or **No-op** — instructions fighting defaults | Rewrite as positive target |
| Skill too long to be effective | **Sprawl** | Progressive disclosure — push reference behind pointers |
| Same info repeated | **Duplication** | Single source of truth |
| Skill fires when it shouldn't | **Description** too broad | Narrow trigger phrases |
| Skill doesn't fire when it should | **Description** too narrow or missing | Add trigger phrases or leading words |
| Agent uses wrong terminology | Missing **leading word** | Add the right term, repeat it |
| Steps feel unnatural | Wrong **granularity** | Split or merge steps |

### 4. Improve — Make the change

Edit the skill's `SKILL.md` in `.agents/skills/<name>/`.

Rules:
- **One change at a time** — don't rewrite the whole skill
- **Test by using** — the next workflow is the test
- **Keep a diff** — `git diff` shows exactly what changed
- **Record the rationale** — why you changed it, in the changelog

### 5. Patterns to watch for over time

After several cycles, look for:
- **Skill you never use** → consider removing (reduces context load)
- **Skill you always customize the same way** → bake the customization in
- **Two skills always used together** → consider merging or creating a compound workflow
- **A gap** — work where no skill helps → create a new skill
- **A skill that keeps getting longer** → it's sprawling, split it

## Quick Actions

### "This skill was perfect"
Record it. Knowing what works is as valuable as knowing what doesn't.

### "This skill was useless"
Don't delete immediately. Record why. After 3 "useless" marks with no "worked" marks, consider removing.

### "I need a skill that doesn't exist"
Use `/writing-great-skills` to design it. Start minimal — 3-5 steps max. Let usage shape it.

### "The whole flow felt wrong"
Step back to the meta level. Edit `WORKFLOWS.md` in the meta-skill, or create a new recipe.
