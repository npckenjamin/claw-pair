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

## Flaw 1: prompting, and emergent intent

Prompting is usually treated as translation: I know what I want, I write
it down, the model does it. But intent doesn't exist upfront — it emerges
while the code takes shape. So prompting is not translation, it is a
loop: run, look, discover what I actually meant, run again.

That loop needs somewhere to store what it discovers. Storing it in the
tree — patching the clanka's output — puts the discovery in a place that
decays: per Naur, program text modified without the theory rots, and a
patched tree is exactly that. Storing it in the master prompt puts the
discovery where it regenerates: the next run is born already knowing it.

This is why the master prompt is one document that absorbs every
discovery, and why the worktree gets nuked instead of fixed. The
discipline is absolute — the moment I hand-fix a tree, the prompt stops
being the full record of intent, and the next run silently loses what
the fix knew.

The claw pair's role in this loop is early validation: intent gets
pressure-tested in conversation before it costs a run. Riffing is cheap;
runs are less cheap; shipped misunderstandings are expensive. The claw
pair moves the discovery of "that's not what I meant" as far upstream as
it can go.

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

Non-determinism means the output must be checked. The concept stacks
three checks, cheapest first:

- **Feedback loops.** A clanka that can validate its work against
  reality catches its own misses before anyone else spends attention on
  them. A claim without an artifact is unchecked.
- **LLM as judge.** LLMs are a little inaccurate; throwing another LLM
  at the output pushes that inaccuracy down to even more negligible
  values.
- **Review with the claw pair.** The residue lands on me — but not
  alone, and not cold. Reviewing with the claw pair is also how the
  theory of the program gets into my head without me having written the
  code. This is the Naur point: modification cost is a function of the
  match between the theory of the world and the theory of the program,
  and the human always holds more theory of the world than the model,
  because the model's inputs are text and text is fundamentally lossy.
  The review conversation is where the two theories get matched.

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
born with the current culture; nothing propagates, nothing drifts. And
because runs restart from zero, every run regression-tests the culture
itself: a bad skill edit shows up as a bad run, fast.

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
