# Theory

Why we believe the claw pair concept solves the job to be done (terms —
claw pair, clanka, master prompt — live in the README).

## The job, restated

Code quickly and confidently. LLMs are the fastest way to produce code,
but three flaws stand between a raw model and confidence:

1. they need to be prompted to carry out my intent — and neither the
   prompt nor the intent starts out right;
2. they run slowly;
3. they are non-deterministic — their code needs to be reviewed.

## Flaw 1: prompting

The prompt that reaches a clanka is the one with consequences — it is
what actually shapes the codebase. The concept arranges for me to never
write that prompt.

LLMs are the best prompters, so the master prompt is written by one. My
job is only to convey intent in conversation, and the claw pair is built
for exactly that: its trajectory — the whole session of riffing — has
attuned it to my lingo and my speaking style through in-context
learning. I get to be a bad prompter; an expert writes the prompt.

Intent itself is often wrong, and a lot of wrong intent is cheap to
catch: it can be invalidated just by reading the codebase. The claw pair
does that check before any code exists.
Clearly wrong intent dies in the riff instead of in a run.

Downstream benefit: I review with the same LLM that
extracted my intent so the review starts primed to be fruitful.

## Flaw 2: slow inference

Inference speed is not something we control so clankas run in parallel worktrees;

Nuke-and-rerun leans on the same fact from the other side: because the
tree is never the source of truth, a worktree is free to destroy, and
parallelism has no coordination cost. a worktree's output will always be
an all or nothing commit so rebasing is cheap.

## Flaw 3: non-determinism

Non-determinism means the output must be checked — and there are two
different things to check: that the code works, and that the code is
good.

Feedback loops handle the first. A clanka that can validate its work
against reality can at least produce code that works. A claim without an
artifact is unchecked.

Working code is not enough — it also needs to be good code: tasteful,
simple, maintainable. The LLM judge handles that. Models tunnel-vision
when they're coding; the judge is the extra lens outside the tunnel. It
provides the non-functional feedback loop — the taste feedback loop —
since it is more closely connected to me, the human, than a clanka
mid-implementation is.

## Compounding

Every mechanism above produces learnings: a prompt phrasing that
worked, a check clankas keep skipping, a register rule. Encoding them
into the skills is what makes run N+1 cheaper than run N.

## The meta feedback loop

Compounding only works if the loop is honest: we keep writing changes
into the skills — how do we know they're actually impactful? That
question needs a feedback loop of its own. Feedback loopability comes in
two layers:

1. **The codebase.** Playgrounds and harnesses make the code itself
   feedback loopable — this is how a clanka validates its work against
   reality.
2. **The process.** Nuke-and-rerun makes agentic engineering itself
   feedback loopable. A run starts from zero with exactly two inputs —
   the master prompt and the skills — so a run is a clean measurement of
   them. Change a skill, rerun, read the difference. A hand-fixed tree
   would pollute the measurement: the run would be measuring the prompt,
   the skills, and whatever my fingers did to the tree.

## What would falsify this

The concept is a bet, and it loses if:

- runs get expensive enough (time or money) that nuking feels wasteful
  and hand-fixing creeps back in;
- the master prompt grows past what a clanka can faithfully hold, and
  parts of my intent start falling out the bottom;
- the claw pair's theory doesn't persist — if each session starts cold,
  the human is the only memory, and the compounding claim weakens.

Watch for these; each one is a signal to revise the concept, not to
quietly abandon the discipline.
