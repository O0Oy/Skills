# Workflow Recipes

Concrete step-by-step recipes for common scenarios. Each recipe tells you exactly which skills to invoke and in what order.

## Recipe 1: Build a New Feature (Standard)

```
Step 1: /grill-with-docs    → Sharpen the idea, build shared language
Step 2: /to-spec            → Synthesize into a spec with user stories
Step 3: /to-tickets          → Break into vertical-slice tickets
Step 4: /implement           → Build each ticket (auto-drives /tdd + /code-review)
```

**Context rule**: Steps 1–3 in one session. Step 4 starts fresh per ticket.

## Recipe 2: Build a Small Feature (One Session)

```
Step 1: /grill-with-docs    → Quick alignment
Step 2: /implement           → Build it right here
```

Skip /to-spec and /to-tickets when the work fits in one context window.

## Recipe 3: Fix a Hard Bug

```
Step 1: /diagnosing-bugs     → Build feedback loop → Reproduce → Minimise
                              → Hypothesise → Instrument → Fix + regression test
Step 2: /improve-codebase-architecture  → If the bug revealed missing seams
```

## Recipe 4: Fix a Simple Bug

```
Step 1: /tdd                 → Write failing test for the bug
                              → Fix until green
```

## Recipe 5: Greenfield / Huge Effort

```
Step 1: /wayfinder           → Chart destination + decision tickets
Step 2: (per ticket)         → Resolve decisions one at a time
Step 3: /to-spec             → Collapse decisions into buildable plan
Step 4: /to-tickets          → Break into implementation tickets
Step 5: /implement           → Build each ticket
```

## Recipe 6: Triage Incoming Issues

```
Step 1: /triage              → "Show me anything that needs attention"
Step 2: /triage #42          → Categorize, verify, grill if needed
Step 3: /implement           → Pick up ready-for-agent issues
```

## Recipe 7: Improve Architecture

```
Step 1: /improve-codebase-architecture  → Get HTML report of candidates
Step 2: Pick a candidate               → Grilling loop to design the deepening
Step 3: /grill-with-docs               → Sharpen the refactoring plan
Step 4: /implement                      → Execute the refactor
```

## Recipe 8: Research Then Build

```
Step 1: /research             → Background agent reads primary sources
Step 2: /grill-with-docs      → Incorporate findings into plan
Step 3: (continue main flow)
```

## Recipe 9: Prototype a Design Question

```
Step 1: /handoff              → Save current context
Step 2: (new session) /prototype → Build throwaway code
Step 3: /handoff              → Bring learnings back
Step 4: (original session)    → Continue with the answer
```

## Recipe 10: Code Review

```
Step 1: /code-review          → Provide the fixed point (branch, commit, tag)
                              → Two parallel sub-agents: Standards + Spec
                              → Aggregated report
```

## Recipe 11: Learn a New Topic

```
Step 1: /teach "topic"        → Establish mission
Step 2: (agent finds resources, creates lessons)
Step 3: (repeat across sessions — stateful workspace persists)
```

## Recipe 12: Hand Off Between Sessions

```
Step 1: /handoff "what the next session should focus on"
Step 2: (new session) Reference the handoff file
```
