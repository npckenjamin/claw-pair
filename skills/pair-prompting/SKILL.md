---
name: pair-prompting
description: Pair-write prompt files for other coding agents, one at a time — riff, write one file, stop for the agent run, riff on its output.
disable-model-invocation: true
---

# Pair Prompting

Pair programming where the deliverable is prompts, not code: the session's
artifacts are markdown prompt files Kenjamin feeds to other coding agents.
Files go in `docs/plans/<effort-name>/` unless he says otherwise, and are
written strictly one at a time. Name them `<step><take>-slug.md`: the number
is the step, the letter the take — `a` opens a step, and each fix file its
runs earn increments the letter (`1a`, `1b`, `2a`, …).

## The loop

1. **Riff** — discuss the next change until its decisions are settled. Ground
   the riff in the actual code, and surface load-bearing findings (layering,
   dependency direction, who calls what) as things to react to together — most
   never belong in the prompt itself.
2. **Write one file** — draft in chat first if the shape is still contested,
   otherwise write it. Done when one file is on disk, opening with its one
   pointer line — `Execute this per .agents/skills/pair-implementing/SKILL.md.`
   — and every line survives the register test below.
3. **Stop** — end the turn. Kenjamin validates the file and runs a coding
   agent with it. Do not start the next file, even as a chat draft: the run's
   output is input to it.
4. **Riff on the run** — review what the agent produced together. The
   findings often *are* the next file: a fixes prompt for that run's output
   ranks ahead of any new step. A file's subject is whatever the riff
   settles on — feature step, fix-up, cleanup, revert. Back to 1.

## Prompt register

The target agent is intelligent and reads the codebase itself. A line earns
its place only as one of these:

- **Decision** — a choice already made in our heads, invisible in the code.
  Sharpest case: guardrails where the agent's intelligence works *against*
  us ("leave the unreachable moments code; do not clean it up").
- **Requirement** — a constraint stated as an outcome ("must cover the
  outside pane"), never the mechanism; the agent discovers the how.
- **Evaluation instruction** — the observable checks by which the run is
  judged, each written so an artifact can back it. The enforcement —
  artifact rule, completion gating, validation entry point, report shape —
  lives in the pair-implementing skill
  (`.agents/skills/pair-implementing/SKILL.md`), which the pointer line
  already invokes; never restate it per file.

Everything else — discoverable codebase facts, rename tables, variable
naming, build mechanics the repo docs already carry — is noise; cut it.
