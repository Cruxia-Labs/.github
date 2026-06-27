# We index how facts *changed*, not facts

> A flat long-context model and a deterministic operator read the **same** `CLAUDE.md` from the real **yazelix** repo. The model narrates a plausible story — and even gets the gist right — but it can't tell you which version each change happened in, and it misses a rule that was retracted then quietly re-added. The operator recomputes the real change-graph: every reversal anchored to the exact commit, each proved by a receipt you re-verify offline, in two languages, without trusting us.

**This is an ablation, not a contest.** The baseline is the *same local model* doing the *same read* with the operator removed — the question isn't "operator vs. an 8B model," it's whether reading a project's change-graph needs the deterministic operator at all. (It does: the model narrates; the operator anchors and proves.)

## The history — the real `CLAUDE.md` history of yazelix (18 recorded versions)

| version | commit subject |
|---|---|
| `986f46c2` | docs: add Claude Code context file with project conventions |
| `fb0d350f` | docs: improve Zellij configuration guidance and remove unnec |
| `7157bd7d` | docs: add comprehensive development principles to CLAUDE.md |
| `c1f468dd` | feat: add zjstatus plugin with vivid custom theme |
| `7b1f3b58` | feat: add yzx doctor command for comprehensive health diagno |
| `f6b4385f` | feat: add full-stack terminal integration with nixGL acceler |
| `d325c337` | docs: note to use 'python3' in commands/scripts; avoid ambig |
| `92d91ddc` | feat: modernize terminal configuration and fix Nushell error |
| `b5b42403` | feat: implement safe terminal config system with backup prot |
| `73643a58` | fix: correct parentheses escaping in Nushell string interpol |
| `21c010d0` | docs: update references to yazelix.toml |
| `fdcd5548` | Update docs and test output formatting |
| `f80f1d63` | fix versioning instructions |
| `efcd7dd1` | feat: display dynamic version in zjstatus from constants.nu |
| `6cd3023d` | Document verification requirement |
| `c585b087` | docs: adopt beads workflow guidance |
| `4854a0fa` | bd init: initialize beads issue tracking |
| `1b8ea730` | Migrate issue tracking to beads_rust |

## LEFT — flat long-context baseline (real `llama3.1:8b`, reading the whole history)

> The project's decisions evolved significantly over time, with a shift from following conventions blindly to analyzing fundamental requirements and constraints. This change in approach led to more robust and reliable code.

**Scoreboard:** of 2 reversals it claimed — 0 right, 1 mis-anchored, 1 unverifiable; and it missed 7 real reversal(s).

**Reversals it claims:**

- ✗ claims *Following conventions blindly* — **UNVERIFIABLE — no matching reversal in the change-graph**
- ≈ claims *Not considering user expectations and system behavior as fundame* — **MIS-ANCHORED — really at `1b8ea730`, the baseline says `d325c337`**

**Reversals it MISSED entirely** (real, in the change-graph, absent from its account):
- `base_directory` → ~/.config/yazelix/ (at `fb0d350f`)
- `configuration_handling` → handled via yazelix.toml (user) and yazelix_defaul (at `21c010d0`)
- `synchronization_requirements` → Always sync Home Manager module with default confi (at `21c010d0`)
- `issue_tracker_tool` → br (beads_rust) (at `1b8ea730`)
- `mandatory_workflow_steps` → 1. File issues for remaining work - Create issues  (at `1b8ea730`)
- `session_completion_protocol` → When ending a work session, complete the steps bel (at `1b8ea730`)
- `task_tracking_instructions` → Use `br` for ALL task tracking — do NOT use TodoWr (at `1b8ea730`)

## RIGHT — the deterministic operator over the recorded change-graph

Every row is the real `diff_claimsets` engine over the recorded claim-sets — anchored to the exact commit, in order. The operator surfaces **every** value change deterministically and ranks none: judging which changes *matter* is perception, which we measure (below), not assert. Two here are unmistakable to any reader — the config format `yazelix.nix → yazelix.toml` and the issue tracker `bd → br`:

| belief | change | at commit |
|---|---|---|
| `base_directory` | `~/.config/yazelix/ as the base directory` → `~/.config/yazelix/` | `fb0d350f` (docs: improve Zellij configura) |
| `configuration_handling` | `handled via yaze…nix (user) and yazelix_d` → `…toml (user) and yazelix_` | `21c010d0` (docs: update references to yaz) |
| `synchronization_requirements` | `Always sync Home…nix, update home_manager` → `…toml, update home_manage` | `21c010d0` (docs: update references to yaz) |
| `critical_rules` | `- Work is NOT complete until `git push` succ` → `- Do not push non-trivial changes before use` | `1b8ea730` (Migrate issue tracking to bead) |
| `issue_tracker_tool` | `bd (beads)` → `br (beads_rust)` | `1b8ea730` (Migrate issue tracking to bead) |
| `mandatory_workflow_steps` | `1. File issues f…This is MANDATORY:
5. Cl` → `…Required only after the ` | `1b8ea730` (Migrate issue tracking to bead) |
| `session_completion_protocol` | `When ending a wo…you MUST complete ALL st` → `…complete the steps below` | `1b8ea730` (Migrate issue tracking to bead) |
| `task_tracking_instructions` | `Use `bd` for ALL task tracking — do NOT use ` → `Use `br` for ALL task tracking — do NOT use ` | `1b8ea730` (Migrate issue tracking to bead) |

*Honest note: of these 8 changes, ~1 are the same belief restated (real-prose extraction variance — the perception noise the gate below measures). The operator shows all of them and anchors each; it neither hides the noise nor ranks the signal — that's the perception layer's job, and we measure it rather than assert it.*

## The receipt — recompute it yourself, offline, in two languages

Each reversal ships a signed ER1 receipt. Recomputed by the Python reference verifier **and** the zero-dependency JavaScript one — then one byte flipped, rejected by both.

| reversal | verdict | `er1_verify.py` | `er1_verify.mjs` | 1-byte tamper |
|---|---|---|---|---|
| `base_directory` → ~/.config/yazelix/ | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |
| `configuration_handling` → handled via yazelix.toml | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |
| `synchronization_requirements` → Always sync Home Manager | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |
| `critical_rules` → - Do not push non-trivia | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |
| `issue_tracker_tool` → br (beads_rust) | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |
| `mandatory_workflow_steps` → 1. File issues for remai | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |
| `session_completion_protocol` → When ending a work sessi | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |
| `task_tracking_instructions` → Use `br` for ALL task tr | HALT `SUPERSEDED_VALUE` | ✓ VERIFIED | ✓ VERIFIED | ✓ FAILED (rejected) |

The 8 receipts are in [`receipts/`](receipts/). Verify any of them with the reference verifiers from [er1-spec](https://github.com/Cruxia-Labs/er1-spec):

```bash
python er1_verify.py <receipt>.er1.json      # Python
node er1_verify.mjs <receipt>.er1.json       # zero-dep JS
```

## What we don't solve yet — the perception gate

The operator over a **recorded** change is deterministic and guaranteed. Reading beliefs out of **free prose** in the first place is perception — we *measure* it, we don't assert it.

- **Mechanism ceiling (synthetic prose):** when each reversal is stated explicitly, the operator recovers ~100% of flips and a flat reading reliably mis-orders or misses them.

- **Real prose (measured):** on this exact repo's `CLAUDE.md` history, the anchored extractor caught all 4 of 4 canonical reversals cleanly at ≥7B local (`llama3.1:8b` 98.8% term stability, holding the gpt-4o ceiling). The honest edge is the model floor (3.8B fragments the same reversal) and recall noise, **not** a missed-reversal rate. The anchored extraction runs **locally** — we never see your files; on this repo it caught all 4 canonical reversals cleanly.

> A prose-extracted belief never gates a HALT. The deterministic operator is the part we defend; the perception is honest-and-improving. A proof is only worth anything if it admits exactly what it cannot see.

---

**Run it on your own history.** Run the shipped linter on *your* repo's rule files: `uvx sagrada-linter scan-history .` — it emits the same kind of ER1 receipt you just recomputed.

---

*A worked example from [Cruxia-Labs](https://github.com/Cruxia-Labs). The receipts here are recomputable with the open [er1-spec](https://github.com/Cruxia-Labs/er1-spec) verifiers; the catch ships in [sagrada-linter](https://github.com/Cruxia-Labs/sagrada-linter).*
