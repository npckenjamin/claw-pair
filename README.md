# Claw Pair

Kenjamin's claw pair culture (a play on *au pair*): the skills that define
how a thought-partner LLM and implementation agents work together, kept in
one place instead of scattered across product repos.

## Job to be done

Code quickly and confidently, despite LLMs being LLMs:

- they need to be prompted, and prompting skills are poor (and intent is
  figured out during the process of coding);
- they run slowly, so they need to be parallelized;
- they are non-deterministic, so their code needs to be reviewed — you
  can't completely trust-fall on the model.

## Patterns

- LLM as judge
- Worktree parallelism
- Compound engineering
- Programming as theory building
- LLM validation loops

## Concept

The claw pair: a thought-partner LLM that works with me to

- provide early validation for my intent and parse it into good prompts;
- help me understand and review the code the model writes;
- help me compound the process by encoding learnings from the field.

Implementation runs are disposable: one master prompt per effort, sent to
a fresh agent each time. When the output isn't right, the worktree is
nuked, the prompt and skills are revised, and the run repeats from zero.
The prompt and the skills are the source of truth — never the tree.

## Skills

Skills live in [`skills`](skills), one folder per skill with a `SKILL.md`:

- [`pair-prompting`](skills/pair-prompting) — the claw-pair side: how to
  pair-write prompt files and what earns a line in one (decisions,
  requirements, evaluation instructions).
- [`pair-implementing`](skills/pair-implementing) — the implementer side:
  the execution contract for a pair-written prompt (decisions are settled,
  checks need artifacts, the report shape).
- [`writing-great-skills`](skills/writing-great-skills) — how the culture
  itself gets written: the vocabulary and principles that make a skill
  predictable, read before editing any skill here.

## Install

Installs every skill user-level via [skills.sh](https://skills.sh):

```sh
npx skills add npckenjamin/claw-pair -g
```

After the repo changes, refresh with `npx skills update -g`.
