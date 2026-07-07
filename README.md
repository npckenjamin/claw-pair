# Claw Pair

(a play on *au pair*) — the skills that define how a thought-partner LLM
(claw pair) and implementation agents (clankas) work together, kept in one
place instead of scattered across product repos.

## Job to be done

Code quickly and confidently, despite LLMs being LLMs:

- they need to be prompted, and prompting skills are poor (and intent is
  figured out during the process of coding);
- they run slowly, so they need to be parallelized;
- they are non-deterministic, so their code needs to be reviewed — you
  can't completely trust-fall on the model.

## Patterns

- LLM as judge: put a model on the review side too — a model checks a
  model's work before I spend my own attention on it.
- Worktree parallelism: inference is slow, so many clankas run at once,
  each in its own disposable worktree. The tree is never the source of
  truth, so nuking one costs nothing.
- Compound engineering: every run's learnings get encoded back into the
  skills, so the next run starts smarter. Failed runs are the test suite
  for the culture.
- Programming as theory building
  ([Naur](https://pages.cs.wisc.edu/~remzi/Naur.pdf)): programming is not
  the production of a program — it is building a theory of how world
  affairs are handled by the program. The schwerpunkt is modification
  cost: it is a function of the match between the theory of the world and
  the theory of the program. The human will always have more theory of
  the world than the LLM — its inputs are text, and text is fundamentally
  lossy — so you either give the LLM theory or keep the human in the loop.
- LLM validation loops: a claim without an artifact is unchecked. Clankas
  prove their work with artifact-backed checks before claiming done.

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
