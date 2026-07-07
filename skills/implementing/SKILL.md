---
name: implementing
description: Execution contract for a master prompt — read the registers, gate on artifact-backed checks, assemble the evaluation packet.
disable-model-invocation: true
---

# Implementing

The contract for executing a master prompt. The user provides it with
the invocation — if they didn't, ask for one. The prompt was
pair-written and every line in it is deliberate; this is how you hold
up your side.

## Reading the file

- **Decisions** are settled. Do not re-litigate them or clean up around
  them, even where your judgment disagrees — especially there.
- **Requirements** are outcomes. The mechanism is yours to discover in
  the codebase.
- A **premise break** — the file asserts something the code or runtime
  disproves — does not void the requirement: pursue the stated outcome
  by whatever mechanism is actually true, and report the break.

## Checks gate completion

Prove the change per the repo's validation skill, if it has one. Then:

- Every check in the prompt's evaluation packet needs its artifact —
  screenshot, UI snapshot, command output. A claim without an artifact
  is unchecked.
- A blocked check is a problem to solve (provision, seed, sign in) or a
  blocker to surface — never a caveat under a done-claim.

## The evaluation packet

The worktree may be nuked after review; the packet and the report are
the run's only survivors.

- **The deck** — an HTML slide deck at `.packet/index.html`, untracked,
  one slide per check: the check, its outcome, its evidence. The review
  walks through it. A check's caveats live on its slide, never deferred
  to the report — the deck must stand alone.
- **The report** — your final message. It carries every discovery,
  deviation, premise break, and side effect beyond the diff — data
  seeded, deployments touched, helpers shipped. Text, because it gets
  quoted into the next prompt revision. An omitted discovery is not
  lost to a future run; it is just lost.

Repo brevity rules are for conversation; they do not apply to the
report.

## The worktree

- The run ends as a single commit holding the entire change and the
  master prompt that drove it.
- Skill-file fixes discovered mid-run may be written but never
  committed — they ride the report back.
