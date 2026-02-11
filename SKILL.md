---
name: Memento
description: |
  Activate on **EVERY SESSION**. Maintain a per-repo `.memento/` directory as an
  agent-owned, high-signal context scratchpad.

  **Always consult** `.memento` at the start of work.
  **Only update** `.memento` when the insight is high-signal, repo-specific, and
  likely to matter again.

  This is not documentation. It is a curated set of durable, project-shaping
  learnings from user steering, reversals, mistakes, and discoveries.
metadata:
  author: Denis Tsai
  version: 1.1.0
  date: 2026-02-12
  scope: per-repository
  persistence: required
---

# Memento: Durable Project Context (Curated)

You maintain a per-repo `.memento/` directory that captures **durable, high-signal**
context: architecture constraints, invariants, non-obvious workflows, gotchas,
and “how this repo *really* works”.

**Consult Memento at the start of every task.**  
**Update Memento only when it clears the Signal Gate (below).**

## Retrieval (Mandatory)

Invariants:

- Never write to `.memento` without first scanning it for related context.
- Never store secrets, credentials, tokens, or personally identifiable information.

Before starting any task, you MUST:

1. Extract task-specific keywords (symbols, systems, subsystems, error strings).
2. Search across `.memento/`.
3. Apply relevant constraints, patterns, and prior decisions silently.

If `.memento/` does not exist yet, create it.

Recommended structure:

```
.memento/
├── overview.md          # “How this repo works” (invariants, architecture, ethos)
├── workflows.md         # Non-obvious repo workflows (deploy, release, local dev)
├── gotchas.md           # Sharp edges + fixes (repo-specific, recurring)
├── decisions.md         # Decisions + rationale + alternatives considered
└── preferences.md       # User steering for this repo/workstream
```

## The Signal Gate (Updates are Conditional)

**Do NOT update `.memento` unless ALL of these are true:**

1. **Repo-specific**: tied to this codebase, its tooling, its architecture,
or its ops.
2. **Non-obvious**: not generic language/tool knowledge or something easily googled.
3. **Durable**: likely relevant again in ≥2 weeks or across sessions.
4. **Actionable**: can be written as a rule, invariant, or “if X then do Y”.

**Hard exclusions (do not record):**

- Generic Programming language style tips, linting “silencing” patterns, etc.
- Routine commands for formatting, compiling, build warnings and errors.
- Anything you could paste into a general best-practices blog post.

**Allowed examples (good candidates):**

- “This repo pins nightly because macro X breaks on stable; do not upgrade
without Y.”
- “CI uses feature flags A/B; local tests must mirror with ENV var Z.”
- “DB migrations must run in this order because of lock contention in prod.”
- “This service expects ids to be canonicalized in layer N, not at the edge.”

## Update Triggers (When the Gate Passes)

Update `.memento` when a high-signal event occurs **and passes the Signal Gate**:

- You hit a recurring error and learn the real cause in this repo.
- The user corrects an assumption about architecture/intent.
- You discover a hidden invariant (ordering, state model, naming, version pinning).
- A workflow differs from “standard” in a meaningful way (deploy, build, test, release).
- You reverse a decision after learning constraints (record why).

## Writing Rules (Keep It Sharp)

When you do write:

- Prefer **rules/invariants** over narratives.
- Include the **why** in 1 line, and the **do this instead** in 1 line.
- Date entries only if it helps track drift.
- If something becomes repeated, promote it into `overview.md` or `workflows.md`.

Example entry format:

```md
### Invariant: <short name>
- Context: <where this bites>
- Rule: <what to do / not do>
- Why: <one-line reason>
- Symptoms: <error strings or failure modes>
```

## Maintenance (Always Curated)

- Merge duplicates into one rule.
- Delete stale notes aggressively.
- Keep .memento/ small: high-signal only (target: <200 lines total across files).
- If you find yourself logging “tips”, you’re drifting—stop and re-apply the
Signal Gate.
