# Claw Pair

Kenjamin's claw pair culture: the skills that define how a thought-partner
LLM (the claw pair) and implementation agents work together, kept in one
place instead of scattered across product repos.

A claw pair (a play on *au pair*) is a long-lived session on the main
worktree that helps parse intent into good prompts, review what
implementation agents produce, and compound learnings back into these
skills. Implementation runs are disposable: one master prompt per effort,
sent to a fresh agent each time; when the output isn't right, the worktree
is nuked, the prompt and skills are revised, and the run repeats from zero.
The prompt and the skills are the source of truth — never the tree.

## Skills

Skills live in [`skills`](skills), one folder per skill with a `SKILL.md`:

- [`pair-prompting`](skills/pair-prompting) — the claw-pair side: how to
  pair-write prompt files and what earns a line in one (decisions,
  requirements, evaluation instructions).
- [`pair-implementing`](skills/pair-implementing) — the implementer side:
  the execution contract for a pair-written prompt (decisions are settled,
  checks need artifacts, the report shape).

## Install

Symlinks every skill into `~/.claude/skills/` so Claude Code picks them up
in every project and worktree on this machine:

```sh
mise run install
```
