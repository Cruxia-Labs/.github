# Cruxia-Labs — what we're building

We think intelligence is less about capability than the **governance of belief** — holding a belief, revising it correctly when the evidence changes, and proving the change. Today's models mostly *regenerate* rather than *revise*: they re-assert beliefs they were told to drop. We don't claim to have solved this; we build the parts that are deterministic, and we measure the rest.

## The gap

Model reasoning isn't reproducible: the same prompt, run twice, can yield different conclusions — and a model will confidently re-assert a belief it was told to drop. Some of this is a formal limit on a single forward pass. We've machine-checked a small core of it and will publish those proofs as we go — only the proven ones. We treat that boundary as a **spear, not a wall**: we publish only what's proven and name where the proof stops.

## What we build

A deterministic operator that revises a belief (or a constraint state) under new evidence and emits a proof of the change — replayable, and recomputable offline by someone who doesn't trust us. The shipped verb today is the narrowest one: catch a rule you retracted that came back. The direction is a family of verbs — *curate, revise, prove*, and further out *branch, compare, compose* — over your own storage. *(Most of that family is build-direction, not a shipped feature yet.)*

## What we don't solve yet

We certify **coherence, not correctness** — garbage in, certified garbage out. The revision operator is deterministic and guaranteed; reading beliefs out of free prose is honest-and-improving, not solved, and a prose-extracted belief never gates a HALT. We measure perception; we don't assert it. The honest edge is the point: a proof is only worth anything if it admits exactly what it cannot see.

---

*A claim about an AI's behavior should be something you can recompute yourself, offline, without trusting whoever made it. Run the command. The bytes either agree or they don't.*

Built by Mars Ausili. See it run: [sagrada-linter](https://github.com/Cruxia-Labs/sagrada-linter) · [er1-spec](https://github.com/Cruxia-Labs/er1-spec).
