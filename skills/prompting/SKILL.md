---
name: prompting
description: Pair-write an effort's master prompt with the user — riff, revise the one document, stop for the agent run, riff on its report.
disable-model-invocation: true
---

# Prompting

Pair programming where the deliverable is the master prompt: the one
markdown document per effort that a fresh coding agent executes from a
clean worktree. The session itself runs in the main worktree, but the
master prompt is written into the worktree the user provisioned for the
effort, at `docs/plans/<effort>.md` unless the user says otherwise.

## The loop

1. **Riff** — discuss the effort until its decisions are settled,
   grounded in the actual code. Read the codebase to invalidate intent
   here, in conversation, where it is cheap — before it costs a run.
2. **Revise the master prompt** — draft in chat first if the shape is
   still contested, otherwise write it. The one document absorbs every
   settled decision; it opens with its pointer line —
   `Execute this per ~/.agents/skills/implementing/SKILL.md.` —
   and every line survives the register test below.
3. **Stop** — end the turn. The user sends the master prompt to a fresh
   coding agent in a fresh worktree. Do not draft ahead: the run's report
   is input to the next revision.
4. **Riff on the run** — review the report and the output together.
   Findings become edits to the master prompt or to the skills — never
   to the tree, which gets nuked. Back to 1 until a run is accepted.

## Prompt register

The coding agent is intelligent and reads the codebase itself. A line
earns its place only as one of these:

- **Decision** — a choice already made in our heads, invisible in the
  code. Sharpest case: guardrails where the agent's intelligence works
  *against* us ("leave the unreachable moments code; do not clean it
  up").
- **Requirement** — a constraint stated as an outcome ("must cover the
  outside pane"), never the mechanism; the agent discovers the how.
- **Evaluation packet** — the observable checks by which the run is
  judged, each written so an artifact can back it. The agent evaluates
  its own work against them, then assembles the evidence into a packet —
  an HTML slide deck — that the review works from. The enforcement —
  artifact rule, completion gating, validation entry point, packet
  shape — lives in the implementing skill, which the pointer line
  already invokes; never restate it in the prompt.

Everything else — discoverable codebase facts, rename tables, variable
naming, build mechanics the repo docs already carry — is noise; cut it.
