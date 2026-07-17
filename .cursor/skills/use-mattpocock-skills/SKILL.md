---
name: use-mattpocock-skills
description: >-
  Navigate and orchestrate mattpocock/skills. Use when the user mentions any
  skill name (/grill-me, /tdd, /implement, etc.), asks "which skill should I
  use", wants to start a new feature/fix/refactor, or needs help choosing a
  workflow. Router over 41 installed skills.
---

# Use Mattpocock Skills

A router and quick-reference for the 41 skills installed from `mattpocock/skills`. Read this skill to decide which skill to invoke, then read and follow that skill's `SKILL.md`.

All skills live at `.agents/skills/<name>/SKILL.md` in the workspace root.

## Decision Tree — What Do You Want To Do?

### "I have a new idea / feature to build"

1. **Have a codebase?** → `/grill-with-docs` (sharpens the idea + builds CONTEXT.md)
2. **No codebase / just thinking?** → `/grill-me` (stateless interview)
3. **Idea is huge, multi-session?** → `/wayfinder` (charts a map of decision tickets)
4. After grilling → `/to-spec` (synthesize into a spec) → `/to-tickets` (break into vertical slices) → `/implement` (build each ticket)
5. **Small enough for one session?** → Skip to-spec/to-tickets, go straight to `/implement`

### "I need to fix a bug"

- **Hard bug / regression / flaky test?** → `/diagnosing-bugs` (reproduce → minimise → hypothesise → instrument → fix)
- **Simple fix you already understand?** → `/tdd` (write failing test, then fix)

### "I want to improve the codebase"

- `/improve-codebase-architecture` — scan for deepening opportunities, get an HTML report, then grill through the chosen one
- `/codebase-design` — vocabulary for designing deep modules (used by other skills automatically)

### "I need to review code"

- `/code-review` — two-axis review: Standards + Spec, run as parallel sub-agents

### "I want to manage issues / triage"

- `/triage` — move issues through needs-triage → needs-info → ready-for-agent → ready-for-human → wontfix
- `/to-spec` — turn conversation into a spec
- `/to-tickets` — break spec into tracer-bullet tickets

### "I need to prototype something"

- `/prototype` — throwaway code that answers a design question
  - Logic question → terminal app
  - UI question → multiple variations on one route

### "I need to research something"

- `/research` — background agent investigates against primary sources, leaves a cited Markdown file

### "I'm switching sessions / handing off"

- `/handoff` — compact conversation into a handoff document for next session

### "I want to learn something"

- `/teach` — multi-session teaching with stateful workspace (lessons, learning records, reference docs)

### "I want to write or improve a skill"

- `/writing-great-skills` — the vocabulary and principles for predictable skills

### "I need to resolve merge conflicts"

- `/resolving-merge-conflicts` — hunk-by-hunk resolution traced to intent

### "I don't know where to start"

- `/ask-matt` — detailed router with the main flow, on-ramps, and standalone skills explained

## The Main Flow: idea → ship

```
  /grill-with-docs ──→ /to-spec ──→ /to-tickets ──→ /implement
        │                                               │
        │ (need prototype?)                    (per ticket, uses)
        ├── /handoff → /prototype → /handoff back       ├── /tdd
        │                                               └── /code-review
        │ (huge effort?)
        └── /wayfinder → (resolve tickets) → /to-spec
```

### On-ramps that merge into the main flow

- **Bugs piling up** → `/triage` → produces agent-ready issues → `/implement`
- **Something broken** → `/diagnosing-bugs` → fix → maybe `/improve-codebase-architecture`
- **Huge foggy effort** → `/wayfinder` → charts decision tickets → when clear → `/to-spec`

## Skill Categories Quick Reference

### Engineering (daily code work)

| Skill | Type | Purpose |
|-------|------|---------|
| `/ask-matt` | user | Router — which skill fits your situation |
| `/grill-with-docs` | user | Interview + build CONTEXT.md and ADRs |
| `/to-spec` | user | Synthesize conversation into a spec |
| `/to-tickets` | user | Break spec into vertical-slice tickets |
| `/implement` | user | Build from spec/tickets, drives /tdd and /code-review |
| `/wayfinder` | user | Plan huge multi-session work as a decision map |
| `/triage` | user | Move issues through triage state machine |
| `/improve-codebase-architecture` | user | Scan for deepening opportunities |
| `/setup-matt-pocock-skills` | user | One-time repo setup (tracker, labels, docs) |
| `/prototype` | model | Throwaway code to answer design questions |
| `/diagnosing-bugs` | model | Disciplined diagnosis loop for hard bugs |
| `/research` | model | Background agent for primary-source research |
| `/tdd` | model | Red-green-refactor loop |
| `/domain-modeling` | model | Build/sharpen project domain model |
| `/codebase-design` | model | Deep module vocabulary and principles |
| `/code-review` | model | Two-axis review (Standards + Spec) |
| `/resolving-merge-conflicts` | model | Hunk-by-hunk merge conflict resolution |

### Productivity (workflow tools)

| Skill | Type | Purpose |
|-------|------|---------|
| `/grill-me` | user | Stateless interview (no codebase needed) |
| `/handoff` | user | Compact conversation for next session |
| `/teach` | user | Multi-session learning workspace |
| `/writing-great-skills` | user | Reference for writing skills well |
| `/grilling` | model | The reusable interview loop primitive |

## Preconditions

Before using engineering skills for the first time in a repo, run `/setup-matt-pocock-skills`. It configures:
- Issue tracker (GitHub, GitLab, or local markdown)
- Triage labels
- Domain doc layout (CONTEXT.md + ADRs)

## Context Hygiene Rules

1. Keep `/grill-with-docs` → `/to-spec` → `/to-tickets` in **one context window** — don't compact until after tickets are created.
2. Each `/implement` starts in a **fresh context**, working from the ticket.
3. If approaching the smart zone (~120k tokens), use `/handoff` and continue in a fresh thread.
4. Never resolve more than one wayfinder ticket per session (except research tickets).
