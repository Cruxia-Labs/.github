# AGENTS.md

Org-wide conventions for Cruxia-Labs repositories — for the AI agents (and humans) who work here.
We scan this file with our own published linter on every push (see
[`.github/workflows/dogfood.yml`](.github/workflows/dogfood.yml)): we run the determinism we sell.

## Conventions

- attribution: commits are authored as Mars Ausili <mars@cruxia.ai>
- receipts: anything we certify ships as an ER1 receipt anyone can recompute offline, in two languages
- format-naming: ER1 is an "open format", not a "standard" — that word is earned only when a second party recomputes the vectors
- scope: coherence, not correctness — we certify that a verdict follows from the recorded inputs, never that an input is true
- determinism: the part we defend is deterministic and replayable; perception is measured, not asserted
- licensing: code is Apache-2.0

## What the linter anchors on

- `key: value` — a structured rule (like every line above)
- `- term — definition` — a bullet with an em-dash
