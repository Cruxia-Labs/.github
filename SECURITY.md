# Security Policy

## Reporting a vulnerability

Please report security issues **privately** rather than opening a public issue:

- Open a private **GitHub security advisory** (repo → *Security* → *Report a vulnerability*), or
- email **mars@cruxia.ai**.

We'll acknowledge within a few days and work with you on a fix and a disclosure timeline.

## What matters most here

These tools are local and offline by design — they make no network calls and never transmit your
files. The most security-relevant surface is the **ER1 receipt** verification path: Ed25519 signature
checking, the canonical-JSON serialization, and the conflict predicate. The highest-priority issues
are ones that let a **tampered receipt verify**, or that break **cross-language agreement** on the
frozen `golden_vectors.json`.

The Ed25519 key pinned in `golden_vectors.json` is a **test key** — never sign a production receipt
with it. Key trust is the relying party's policy, not ours (see each repo's
`SCOPE_OF_CERTIFICATION.md`).
