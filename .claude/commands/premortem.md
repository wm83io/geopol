---
description: Run an adversarial pre-mortem against the Iran 2026 framework and recommend mitigations
---

# Iran 2026 — Framework Pre-Mortem

Monthly adversarial-review cycle. Forces the analyst to assume the framework has failed and diagnose the most likely cause. Output is a structured diagnosis with proposed mitigations routed to the appropriate layer (reference, slash command, CLAUDE.md, or staged manifest).

This command exists because every defensive rule in the framework eventually metastasizes into the failure it was designed to prevent. Multi-cycle confirmation prevents recency bias and creates commitment bias. Source tiering prevents credulity and creates cluster-laundering. Voice discipline prevents projection and can commit the model to wrong principals. The pre-mortem cadence is the framework's adversarial check against its own discipline.

---

## When to invoke

- **Monthly floor** (calendar): on the 1st of each month, against the prior month's cumulative outputs.
- **On trigger**: after any synthesis major-version increment; after any logged trend-vs-operational drift event; after any cycle where the analyst's gut says "the framework feels too comfortable."
- **Manual**: any time the user invokes `/premortem`.

If the last `/premortem` ran within 14 days, skip unless invoked manually with explicit override.

---

## Pre-flight

Load in order. All paths relative to the repo root.

1. **Strategic trends baseline:** read `reference/strategic-trends.md` in full. Note every VALIDATED trend's last review date; flag any beyond the 30-day decay clause.
2. **Latest synthesis:** read `synthesis/synthesis-v*.md | sort -V | tail -1`.
3. **Last 30 days of SITREPs:** read the most recent ~30 day-N files in `sitreps/`. Look for repeated framing, probability-band drift, KEC-as-driver substitution, Fork D'-as-residual expansion.
4. **Last 30 days of sweeps:** read JSON files in `probes/sweeps/` from the prior 30 days. Look for source-cluster patterns (same outlet repeatedly originating "multi-source" claims), confidence inflation (M → H without new sourcing), trigger-firing concentration on a small number of probes.
5. **Appendix B:** read `appendix/appendix-b-blind-spots.md`. Note any blind spot that has not fired in 30+ days.
6. **Prior pre-mortems:** `ls premortems/ 2>/dev/null | sort | tail -3`. Read the last three. Look for recurring failure-mode hypotheses; if the same hypothesis appears in 2+ prior pre-mortems without mitigation traction, escalate.
7. **Prediction ledger:** read `calibration/prediction-ledger.md` Scorecard, Surprise register, and rows resolved since the last pre-mortem.

Output directory: `premortems/`. Create if absent. Filename: `premortem-YYYY-MM-DD.md`.

---

## Retrospective (mandatory; precedes the diagnostic)

The pre-mortem imagines failure forward; this section scores it backward. Two parts, ≤400 of the
2,500-word budget, placed immediately after the mitigation-manifest table in the output file:

1. **Prior pre-mortem scored.** For each failure mode in the previous pre-mortem: `occurred` /
   `partial` / `did-not-occur` / `unobservable`, one line of evidence each. For each approved
   mitigation: did it get applied, and did it bind (cite a cycle where the rule changed behavior,
   or state that no test case arose). A mitigation approved but never applied is itself a finding;
   2+ consecutive no-traction scores on the same mitigation escalate per pre-flight item 6.
2. **Ledger lookback.** From rows resolved since the last pre-mortem: surprises mapped to the five
   failure-mode categories; any matrix-followed `n` (discipline breach); any second-expiry
   instrumentation failures; signal-quality check (count of signals too vague to resolve; vague
   signals inflate apparent coverage and are the Goodhart surface of the resolution discipline).

Retrospective findings feed the diagnostic's "Evidence in current outputs" lines. A failure mode
that the retrospective shows already occurring is `high` likelihood by default.

---

## Diagnostic structure

The pre-mortem assumes a 6-month-forward retrospective: "It is six months from today. The framework's 30-day and 6-month projections from the last 30 days were materially wrong. What is the most likely cause?"

Generate 4-6 candidate failure modes. For each, produce a finding card:

```
### Failure {N}: {short name}

**Likelihood:** {high / medium / low}

**What happened.** 2-4 sentences. Imagine the specific way the projection failed: which fork came in unexpectedly, which trend reversed, which actor selected an option the framework ranked sub-dominant.

**Root cause.** 1-2 sentences. Name the discipline rule, methodological commitment, or operational habit that produced the failure.

**Evidence in current outputs.** Cite specific instances from the last 30 days of SITREPs and sweeps where the failure mode is already incipient. If no incipient evidence, mark as "speculative pre-mortem" rather than "evidence-based pre-mortem."

**Mitigation.**
- {specific change to reference/, slash command, CLAUDE.md, or synthesis}
- {alternative or supplementary mitigation}

**Routing.** One of: `reference-patch` / `slash-command-patch` / `CLAUDE.md-patch` / `synthesis-manifest` / `none-recommended`.
```

---

## Required failure-mode coverage

Each pre-mortem must address at least one candidate in each of the following five categories, even if only to dismiss them as not-current-risks:

1. **Trend rigidity** — VALIDATED trend that should have demoted but didn't, due to commitment bias dressed as multi-cycle discipline.
2. **Source-cluster collapse** — multi-outlet T2 confirmation that was actually single-source laundering; "anonymous senior X sources" treated as independent.
3. **Wrong principal** — named principal whose decisions don't match the constraint-model prediction; alternative principal hypothesis under-tested.
4. **Probability-band erosion or composite degeneracy** — ranges crept wider; Fork D' absorbed too much; KEC obscured primitives.
5. **Time-horizon mismatch** — daily-cadence updating producing false confidence on 6/12-month projections; long-horizon numbers drifting without separate update rules.

A pre-mortem missing one of the five categories is incomplete and must be re-run.

---

## Cross-cutting check: defensive-rule metastasis

For each defensive rule in the framework (multi-cycle confirmation; source tiering; voice discipline; range-only probability; substrate-as-agent prohibition), ask:

> Is this rule, in the last 30 days of outputs, producing the failure it was designed to prevent?

If yes for any rule, that is the primary mitigation target — propose a counter-rule or a calibration check that makes the defensive rule re-examined rather than auto-applied.

Examples:
- Multi-cycle confirmation → commitment bias. Counter-rule: symmetric demotion + 30-day decay clause.
- Source tiering → cluster-laundering. Counter-rule: originating-reporter provenance check.
- Voice discipline → wrong principal lock-in. Counter-rule: alternative-principal-hypothesis probe.

---

## Output artifacts

Each `/premortem` produces three artifacts:

1. **Diagnostic file** at `premortems/premortem-YYYY-MM-DD.md`. Contains all failure-mode finding cards plus the defensive-rule metastasis check.
2. **Mitigation manifest** at the top of the diagnostic file as a table:

   ```
   | # | Failure mode | Routing | File to patch | Status |
   ```

   Status starts `proposed`. The analyst reviews and either approves (status → `approved`) or rejects (status → `rejected; reason: ...`). Approved items are then executed.

3. **One-line entry** appended to `premortems/INDEX.md` with date, count of failure modes diagnosed, count of approved mitigations.

---

## Execution discipline

- **Do not propose mitigations the framework already has.** Read CLAUDE.md and the relevant slash command before proposing a discipline rule; if the rule already exists, the failure mode is "rule exists but is not being applied," and the mitigation is enforcement (calibration check), not new rule.
- **Do not over-engineer.** Each pre-mortem should produce 2-5 actionable mitigations max. More than 5 means the diagnosis is unfocused; less than 2 means the pre-mortem didn't try hard enough.
- **Do not skip the metastasis check.** It is the highest-leverage portion of the cycle. Defensive rules that have become failure surfaces are the framework's largest blind spot.
- **Do not mark the framework healthy without evidence.** If every failure-mode card is "low likelihood, no incipient evidence," re-run the pre-mortem with the assumption that you are the failure mode and the framework is overfitting to your priors.

---

## Routing rules

| Routing | Where the patch lands | Activation |
|---|---|---|
| `reference-patch` | `reference/*.md` | Direct edit; commit as `reference: {file} - {pre-mortem mitigation}` |
| `slash-command-patch` | `.claude/commands/*.md` | Direct edit; commit as `command: {name} - {pre-mortem mitigation}` |
| `CLAUDE.md-patch` | `CLAUDE.md` | Direct edit; commit as `claude.md: {section} - {pre-mortem mitigation}` |
| `synthesis-manifest` | `synthesis/staging/v{X-Y}-premortem-manifest.md` | Consumed at next `/revise`; commit as `manifest: v{X-Y} pre-mortem - {N} items` |
| `none-recommended` | n/a | Failure mode noted but no mitigation worth the change cost |

Approved mitigations execute in the same `/premortem` session if scope permits; otherwise stage and note in the diagnostic file.

---

## Anti-patterns

- Do not turn the pre-mortem into a defensive justification of the framework's current outputs. The exercise assumes failure; if you cannot imagine failure, the framework is overfit to your priors.
- Do not propose mitigations that re-enforce the discipline rule under suspicion. If multi-cycle confirmation is producing commitment bias, the mitigation is symmetry or decay, not "stricter multi-cycle confirmation."
- Do not skip the "evidence in current outputs" line on any finding card. A pre-mortem without grounding in the last 30 days is a thought experiment, not a diagnostic.
- Do not invoke `/premortem` to retroactively justify a contemplated change to the framework. Run it cold; let the diagnosis route the changes.
- Do not let the diagnostic file exceed 2,500 words. Compression discipline applies; if the analysis cannot fit, the failure modes are too numerous and the diagnostic is unfocused.

---

*The pre-mortem cadence is the framework's adversarial check against its own discipline. Every defensive rule eventually becomes a failure surface; this command makes that visible on a fixed schedule rather than at the moment of catastrophic mis-projection.*
