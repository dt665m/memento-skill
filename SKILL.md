---
name: Memento
description: |
  Activate on **EVERY SESSION**, no exceptions.  Maintain a `.memento` folder wholly
  owned by you, the agent, as a context scratch pad.  Take notes about successful
  workflows along with mistakes that prevents future instances from repeating them.
  This is not about documentation, it is purely used for insights learned either
  from user guidance, steering or self reflection.
metadata:
  author: Denis Tsai
  version: 1.0.0
  date: 2026-02-08
  scope: per-repository
  persistence: required
---

# Memento: Constantly Updated Context

You maintain a per-repo `.memento` directory that remembers successes, mistakes,
gotchas, quirks and anything else useful to the work at hand.  Before starting
work, look in your `.memento` for guidance.  Structure your `.memento` efficiently
such that future you can find relevant information quickly.  Anytime there are
insights that will help future you, update `.memento`.  It should be
constantly maintained such that deprecated or redundant information should be
pruned while you updated it with fresh learnings.

**This skill must be consulted at the start of every task and updated
whenever necessary.**

## Find Context

Invariants

- Never write to `.memento` without first scanning it for related context.
- Never store secrets, credentials, tokens, or personally identifiable information

On every task, search `.memento` for relevant context and apply the context to your
knowledge base.  There is no need to announce or report any findings in `.memento`.
If no `.memento` exists yet, create it.  Example Design:

```
.memento/
├── preferences.md                  # User preferences / Steering
├── good_patterns.md                # Good workflows and patterns
├── bad_patterns.md                 # Bad workflows and patterns
└── notes.md                        # Domain notes that are important 
```

```markdown
# Bad Patterns

## Corrections
| Date | Source | What Went Wrong | What To Do Instead |
|------|--------|-----------------|--------------------|
```

These are just guidelines, design it how you see fit. `.memento` does not need to
be polished prose, but entries must be concise, explicit, and unambiguous to a
future agent.

## Continuous Updates

Update `.memento` as you work, especially when you correct yourself in your
reasoning or if the user steers you.  Some important events that must
trigger Memento:

- **You hit an error and figure out why.** Update immediately.
- **The user corrects you.** Track what you did vs what the user actually wanted.
- **You catch your own mistake.** Update immediately.  Catching your own mistakes
  is even more insightful for future you.
- **You try something and it fails.** Log the approach and why it didn't work
  so you don't repeat it.
- **You try something and it works well.** Log the pattern.
- **You re-read the `.memento` mid-task** because you're about to do something
  you've gotten wrong before. Good. Do this.
- **You make an assumption.** Log it if it later proves false.

The `.memento` is a living space. Treat it like working memory that persists
across sessions, not something ephemeral.

## Maintenance

While you are updating `.memento`:

- Merge redundant entries into a single rule.
- Promote repeated corrections to User Preferences.
- Archive resolved or outdated notes.
- Keep total length under 200 lines of high-signal content.

A 50-line file of hard-won rules beats a 500-line log of raw entries.
