# Theory

Why we believe the claw pair concept solves the job to be done.

## The job, restated

Code quickly and confidently. LLMs are the fastest way to produce code,
but three flaws stand between a raw model and confidence:

1. they need to be prompted, and intent is figured out during the
   process of coding — I don't fully know what I want until I see
   something;
2. they run slowly;
3. they are non-deterministic — their code needs to be reviewed.

Each flaw gets its own argument below. The claim is that the claw pair
concept doesn't just patch each flaw; the same few mechanisms answer all
three at once.

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
does that check before any code exists — an LLM that isn't writing the
code, reading the code, telling me my intent doesn't survive contact.
Wrong intent dies in the riff instead of in a run.

Downstream, review compounds this: I review with the same LLM that
extracted my intent, thought through the decisions, and invalidated the
wrong ones — so the review starts primed to be fruitful, not cold.

## Flaw 2: slow inference

Inference speed is not something we control, so the answer is to stop
waiting on it. Clankas run in parallel worktrees; my time goes into the
claw pair conversation, which overlaps with the runs instead of blocking
on them.

Nuke-and-rerun leans on the same fact from the other side: because the
tree is never the source of truth, a worktree is free to destroy, and
parallelism has no coordination cost. Nothing needs merging, syncing, or
cherry-picking between trees — the prompt and the skills are the only
shared state, and they live outside every tree.

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

Non-determinism also has an upside the concept exploits: a rerun is a
fresh sample. When a run goes wrong, the fix is a better prompt or a
better skill, and the rerun tests that fix end-to-end from zero — not
just the patch in isolation.

## Compounding

Every mechanism above produces learnings: a prompt phrasing that
worked, a check clankas keep skipping, a register rule. Encoding them
into the skills is what makes run N+1 cheaper than run N — the
compound-engineering bet.

The skills live in this repo, installed at the user level, so culture
sits outside every product repo and every worktree. A fresh clanka is
born with the current culture; nothing propagates, nothing drifts.

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
  discoveries start falling out the bottom;
- the claw pair's theory doesn't persist — if each session starts cold,
  the human is the only memory, and the compounding claim weakens.

Watch for these; each one is a signal to revise the concept, not to
quietly abandon the discipline.
