---
description: Audit and refresh the Iran 2026 Appendix B blind-spot inventory and probe directives
---

# Iran 2026 — Blind-Spot Auditor

Refreshes Appendix B's blind-spot inventory and standing probe directives. Comparative job:
what does the current framework think it cannot see, versus what recent probe data shows it can or cannot.

**Cadence:** monthly floor, faster on trigger events. Do not run weekly. Probes update; blind spots evolve.

---

## Pre-flight

Load into working context. All paths are relative to the repo root.

1. **Strategic trends baseline:** read `reference/strategic-trends.md` in full FIRST. The audit
   is responsible for trend-state maintenance: promoting PENDING trends to VALIDATED on threshold,
   logging drift events, and closing reference-to-operational instrumentation gaps. The trend
   table is the audit's anchor; without it, the audit is reactive to the most recent SITREP.
2. **Anchor synthesis:** read highest-versioned file in `synthesis/`
3. **Appendix B:** read `appendix/appendix-b-blind-spots.md`
   This is the document this skill modifies. Read it in full before proposing any change.
4. **Last 2-3 probe sweeps:** read most recent files in `probes/sweeps/`
   in chronological order. Without 2+ cycles to compare, defer the audit. Each sweep's
   `reference_trends` field is a primary input for trend-state updates.
5. **Last 2-3 SITREPs:** read most recent files in `sitreps/`
   in chronological order.
6. **Prediction ledger:** read `calibration/prediction-ledger.md` Scorecard, Surprise register,
   and every row resolved `did-not-fire`, `expired-unresolved`, or surprise-logged since the last
   audit. Primary input for Source C and Step 5c.

After producing the audit delta, write the patched Appendix B back to
`appendix/appendix-b-blind-spots.md` using the Edit or Write tool.
Confirm write succeeded. If trend states changed, also patch `reference/strategic-trends.md`
in the same audit cycle. Git history tracks versions — no need to rename the file.

---

## Audit Loop — existing blind spots

For each BS-1..BS-N, walk five questions in order. Stop at the first decisive answer.

### Step 1 — Did probes resolve it?

If recent probe findings closed the gap (e.g. confirmed appearance closes part of an opacity BS), the
blind spot is partially or fully resolved. Update visibility upward, note resolution mechanism, consider
retirement.

Resolution does not require certainty. Visibility moving from 15% to 50% on confirmed signal is a real
upgrade even if 50% is still poor. Retire only when visibility is high enough that the BS no longer
materially constrains the framework.

### Step 2 — Did probes confirm it harder?

If probe attempts repeatedly returned `null` on a target signal across multiple cycles, the blind spot is
structurally durable. A persistently dark area is more dangerous than an acknowledged gap because it
signals the source ladder itself is inadequate, not just that the data has not surfaced yet.

If a BS has been null for **3+ probe cycles**, escalate priority and propose alternative sources. If no
alternative exists, mark as `structurally opaque` and note the framework risk this imposes.

### Step 3 — Did the framework move underneath it?

A blind spot's framework risk is not static. If the synthesis revised an assumption that depended on the
dark area, the BS's priority changes.

Worked example: when A4 (Iranian fracture) was revised twice in 48 hours, BS-1 (Iranian internal
politics) became *more* critical, not less, because the framework now claims more precision about a still-dark
area.

For each BS, check: did the framework variable it constrains get revised? If yes, did revision increase
or decrease dependence on the dark area?

### Step 4 — Should the visibility/risk/priority scores move?

Apply the matrix:

| Dimension | Range | Definition |
|---|---|---|
| Visibility | 0-100% | How much of the relevant signal we are reading. Updated on probe yield. |
| Framework risk | Low / Med / High | If BS broke open tomorrow with bad news, how much does the framework move? Independent of visibility. |
| Priority | Low / Med / High / Critical | Function of visibility AND risk. Low visibility + high risk = critical. High visibility + low risk = low. |

Score movements are conservative. A single probe finding does not move visibility 30 points. Cumulative
pattern across cycles does.

### Step 5 — Should standing directives change?

Probe directives in Appendix B are the operational link between blind spots and the runner skill. If BS
scores moved, directives should usually move with them:

| Score change | Directive change |
|---|---|
| Visibility dropped | Add sources, increase frequency, lower trigger thresholds |
| Visibility rose | Can dial back — only if structural factors stable |
| Risk rose | Tighten "what changes the framework" criteria |
| Priority changed | Reorder the directive list |

### Step 5b — Trend-state maintenance (MANDATORY)

The audit owns trend-state maintenance. Walk every active trend in `reference/strategic-trends.md`:

1. **Aggregate sweep cross-checks:** read the `reference_trends` field of each sweep since last
   audit. Count `advance`, `hold`, `contradict_single`, `contradict_multi`, `close_pending_gap`
   per trend.
2. **State transition rules:**
   - PENDING → VALIDATED: 2+ cycles of `advance` evidence OR 1 cycle with 2+ independent source
     clusters.
   - VALIDATED → CONTESTED: 2+ cycles of `contradict_multi` evidence OR a structural reference
     revision that adds a new prediction the trend did not previously make.
   - CONTESTED → VALIDATED: 2+ cycles of `advance` evidence resolving the prior contradiction.
   - CONTESTED → DISCONFIRMED: 3+ cycles of sustained contradiction without resolution.
   - Any → state-unchanged: when evidence is mixed or insufficient.
3. **Drift event logging:** every `contradict_single` event across the cycles is a candidate drift
   event. If a BS mechanism revision was made in operational layer (Appendix B or SITREP Section 3)
   that contradicts a VALIDATED trend, log the drift event in `strategic-trends.md` with:
   trend involved, operational divergence description, reference prediction over-ridden,
   resolution (if resolved) or pending-confirmation status, methodology lesson, cost in cycles.
4. **Pending-candidate promotion:** the pending-candidate table at the bottom of
   `strategic-trends.md` is the audit's responsibility. Promote candidates that meet 2-cycle
   threshold; retire candidates that have not surfaced operational evidence in 4+ cycles.
5. **Reference-to-operational instrumentation gap check:** for each active trend, confirm the
   coverage matrix entry. If a trend lacks BS or PROBE instrumentation, this is a Step 6
   candidate (new BS or new PROBE directive). The Day 82 BS-18 promotion was the canonical case;
   the trend tracker prevents future cases from emerging as reactive promotions after operational
   evidence forces them.
6. **Methodology check (T7 maintenance):** scan the SITREPs since last audit for substrate-as-agent
   voice slips. T7 (materialist bargaining model holds against teleological substrate voice) is
   the only trend that fails as drift rather than as falsification; voice-discipline violations
   in SITREP prose are T7 drift events. Log violations and any corrections issued in the trend
   tracker's drift log.

Trend-state maintenance is not optional. The audit's deliverable to `strategic-trends.md` is a
required artifact alongside the patched Appendix B.

### Step 5c — Probe portfolio review (MANDATORY)

The audit owns probe cadence. Walk the portfolio against measured yield:

1. **Fire-rate table.** Compute per-probe status counts over the trailing 12+ sweeps (parse
   `probes/sweeps/*.json` finding cards; statuses fired/partial/null/gap). Normalize probe-ID
   variants before counting. Include the table in the audit summary.
2. **Tier assignment.** Record a tier (D / E / M, per the sweep.md tier model) against every
   directive in Appendix B. Downshift candidates: 10+ consecutive cycles without a fire AND
   attached BS not CRITICAL. Upshift: any fire-rate recovery or risk elevation. Tier E directives
   must state their activation condition explicitly.
3. **Threshold sanity.** A probe with sustained partials and zero fires (10+ cycles) has a
   miscalibrated fire bar or an inadequate source ladder; redefine the fired/partial boundary in
   the directive or expand the ladder. PROBE-21 is the standing case.
4. **Ceiling.** Hard ceiling: 25 active directives. Exceeding it forces retirement or merger of
   the lowest-yield probes before any addition. Growth without retirement is the documented
   failure pattern (13 directives Day 74 → 21+ Day 102, zero retirements since Day 76).
5. **Ledger escalations.** Action every `expired-unresolved` ledger row at its second consecutive
   expiry: source-ladder reconstruction, reformulation, or explicit structural-opacity marking.

**One-time directive (first audit after 2026-06-11).** Restructure Appendix B for diff-reads:
move the Confidence Architecture Summary and the new probe tier table to the top of the file as a
state header; move the accreted per-day audit-note chronicle below the BS inventory. Delete
nothing; git preserves. Add a probe-ID normalization note (canonical spellings). This enables the
sweep/sitrep diff-read pre-flight.

### Step 6 — Promote BS and PROBE candidates from archived staging manifests

If a synthesis-revision manifest in `synthesis/staging/archive/` introduced BS or PROBE candidates not yet promoted to operational status in Appendix B, evaluate at this audit:

- **For each BS candidate:** does current probe data support promotion to an operational BS-N entry? If yes, assign the next BS number, write the full inventory entry (visibility, framework risk, sources, revision conditions per the candidate spec), and remove the "candidate" status. If probe data is insufficient, hold the candidate for the next audit with a one-line rationale.
- **For each PROBE candidate:** does the BS it serves now sit in the operational inventory? If yes, assign the next PROBE number, write the full directive (frequency, target signal, sources, revision conditions per the candidate spec), and add to the Standing Weekly Intelligence Directives section. If the parent BS was deferred, defer the probe in parallel.
- **Document promotions** in the audit summary so subsequent skills (sweep, sitrep) know the inventory expanded. List promoted-from-candidate items separately from new BSs detected this cycle via Sources A/B/C below.

Candidate evaluation does not bypass the existing audit loop; a candidate must still meet the standard criteria for inventory inclusion. The candidate status only signals that a sibling skill (revise) has pre-validated the dark area worth tracking.

---

## New Blind-Spot Detection

After walking existing BS, scan for new ones from three angles.

### Source A — Probe gap log

Probes returning `gap` status repeatedly are new BS candidates. Distinguish:

- **Gap:** we asked, found nothing. ← signal here
- **Null:** we asked, confirmed nothing happened.

Three consecutive `gap` cycles on one probe = new BS candidate.

### Source B — Framework additions

Has Appendix A added new dynamics since last audit? Each new dynamic carries assumptions, and assumptions
imply visibility requirements. Walk Appendix A's recent additions: for each, ask what we would need to
see to validate, and whether we are seeing it. Anything we would need but cannot see is a new BS.

### Source C — Recent miscalls

If the framework predicted X and Y happened, the gap between them often points at a blind spot. The
systematic input is `calibration/prediction-ledger.md`: the Surprise register (major movers no
watchlist carried), heavy did-not-fire clusters, and expired-unresolved rows are each candidates
for blind-spot diagnosis. Supplement by walking recent SITREP matrices for sharp unexpected moves.
The miscall itself is information about what we were not seeing; the Days 84-102 backfill pattern
(all five surprises escalation-side, three of them new-vector classes) is the canonical example.

---

## Retirement

A blind spot retires when:

- Visibility climbs above 60% AND framework risk drops to Low/Med, OR
- The framework variable it constrained has been removed from the synthesis, OR
- It has been folded into another BS that captures the same dark area more precisely.

When retiring, archive the BS-N entry to a `retired` section at the bottom of Appendix B. Do not delete.
Future framework revisions may resurrect it.

---

## Confidence Architecture Summary

Maintain the summary table at the bottom of Appendix B as an at-a-glance state of the audit.

- **Three critical BSs** = structural baseline.
- **More than five critical** = framework is overextended and should be narrowed.

The summary table is the audit's executive summary. Update it last, after the per-BS walk.

---

## Output Artifacts

Produce five:

1. **Audit summary** — three to five sentences stating what changed structurally since last audit. Frame
   at the level of the framework's epistemics, not individual data points. Cite trend-state changes
   explicitly.
2. **Per-BS deltas** — for each BS that moved, before/after state with one-line justification. Skip BSs
   with no movement.
3. **New BSs added** — full BS entries with initial visibility/risk/priority scores and standing probe
   directives.
4. **Retired BSs** — list with retirement rationale.
5. **Trend-state patch** — every state transition, every drift event logged, every pending-candidate
   promotion or retirement, every instrumentation-gap-closure recommendation. Applied to
   `reference/strategic-trends.md` as part of the same audit commit (use `command: audit -
   {one-line}` commit message format per CLAUDE.md, with co-mention of the trend-tracker patch).

These artifacts are the patch. The user applies them to Appendix B AND `reference/strategic-trends.md`,
or asks this skill to produce refreshed full documents.

---

## Anti-patterns

- Do not invent blind spots to look thorough. Five well-tracked BSs beat fifteen vague ones.
- Do not let recency bias drive priority. A BS critical six weeks ago and still critical does not need
  revisiting unless probes moved its scores.
- Do not collapse multiple distinct BSs into one to clean up the list. Each BS should map to a discrete
  dark area; merging hides structure.
- Do not produce blind-spot entries that reference specific news items. BSs are structural; news items
  belong in probe findings.
- Do not let the audit become a framework rewrite. If the audit surfaces that the framework itself needs
  revision, escalate as a separate task. The auditor's deliverable is Appendix B, not the synthesis.

---

## Calibration Check

The framework's central thesis (per v4.0 / Appendix C): the framework ranks options under a
constraint surface; agents select; the substrate is materialist not teleological. Apply to the
audit itself. Four known structural biases:

- **Western source bias:** the source ladder is heavier on US/UK/Israeli reporting than
  Iranian/Russian/Chinese. Iranian internal BSs will systematically be darker than Western ones.
  Acknowledge, do not pretend symmetry.
- **Recency bias (CANONICAL FAILURE MODE):** the most recent probe cycle dominates audit
  perception. Weight cumulative patterns over single-cycle signals. The Day 77 → Day 83 BS-12
  "apex-veto" over-read is the documented instance; T3 Fearon-Slantchev prediction was
  over-ridden on single-cycle ISW analytical evidence, mis-stating the PA-gap mechanism for six
  cycles until Day 83's Vahidi silence-break confirmed the trend baseline. The trend tracker
  (`reference/strategic-trends.md`) exists to block this; the audit must consult it before
  declaring any BS mechanism revision.
- **Confirmation bias:** if the framework predicted X and we are looking for X, we will find X. Audit
  specifically for what would *contradict* current assumptions, not just confirm them.
- **Reactivity bias:** the audit risks responding to the latest SITREP rather than to the
  multi-cycle reference baseline. The trend table is the corrective; audit it FIRST in pre-flight
  to anchor before reading SITREPs.

Note any of these that bit this cycle in the audit summary. Specifically, name any recency-bias
or reactivity-bias instance the trend-cross-check surfaced.
