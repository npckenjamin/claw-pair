---
name: pair-implementing
description: Execution contract for pair-written prompt files — read the registers, gate on artifact-backed checks, report the run.
disable-model-invocation: true
---

# Pair Implementing

The contract for executing a prompt file from `docs/plans/`. The file was
pair-written and every line in it is deliberate; this is how you hold up
your side.

## Reading the file

- **Decisions** are settled. Do not re-litigate them or clean up around
  them, even where your judgment disagrees — especially there.
- **Requirements** are outcomes. The mechanism is yours to discover in the
  codebase.
- A **premise break** — the file asserts something the code or runtime
  disproves — does not void the requirement: pursue the stated outcome by
  whatever mechanism is actually true, and report the break.

## Checks gate completion

Prove the change per the repo's validation skill
(`.agents/skills/validating-ios/SKILL.md` for iOS changes). Then:

- Every check in the file needs its artifact — screenshot, UI snapshot,
  command output. A claim without an artifact is unchecked.
- A blocked check is a problem to solve (provision, seed, sign in) or a
  blocker to surface — never a caveat under a done-claim.

## The report

Your final report is the input to the next prompt, not a summary. It
carries:

- each check: outcome and artifact path;
- every discovery, deviation, and premise break;
- every side effect beyond the diff — data seeded, deployments touched,
  helpers shipped.

Repo brevity rules are for conversation; they do not apply here. An
omitted discovery costs a future run.

## The worktree

- Files already dirty when you arrived stay untouched.
- Commit only when asked; the commit includes the prompt file that drove it.
