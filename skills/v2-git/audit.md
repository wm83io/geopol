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

1. **Anchor synthesis:** read highest-versioned file in `synthesis/`
2. **Appendix B:** read `appendix/appendix-b-blind-spots.md`
   This is the document this skill modifies. Read it in full before proposing any change.
3. **Last 2-3 probe sweeps:** read most recent files in `probes/sweeps/`
   in chronological order. Without 2+ cycles to compare, defer the audit.
4. **Last 2-3 SITREPs:** read most recent files in `sitreps/`
   in chronological order.

After producing the audit delta, write the patched Appendix B back to
`appendix/appendix-b-blind-spots.md` using the Edit or Write tool.
Confirm write succeeded. Git history tracks versions — no need to rename the file.

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

If the framework predicted X and Y happened, the gap between them often points at a blind spot. Walk
recent SITREP probability matrices: any variable that moved sharply in an unexpected direction is a
candidate for blind-spot diagnosis. The miscall itself is information about what we were not seeing.

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

Produce four:

1. **Audit summary** — three to five sentences stating what changed structurally since last audit. Frame
   at the level of the framework's epistemics, not individual data points.
2. **Per-BS deltas** — for each BS that moved, before/after state with one-line justification. Skip BSs
   with no movement.
3. **New BSs added** — full BS entries with initial visibility/risk/priority scores and standing probe
   directives.
4. **Retired BSs** — list with retirement rationale.

These artifacts are the patch. The user applies them to Appendix B, or asks this skill to produce a
refreshed full document.

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

The framework's central thesis: emergent behavior from misalignment produces outcomes nobody chose. Apply
to the audit itself. Three known structural biases:

- **Western source bias:** the source ladder is heavier on US/UK/Israeli reporting than
  Iranian/Russian/Chinese. Iranian internal BSs will systematically be darker than Western ones.
  Acknowledge, do not pretend symmetry.
- **Recency bias:** the most recent probe cycle dominates audit perception. Weight cumulative patterns
  over single-cycle signals.
- **Confirmation bias:** if the framework predicted X and we are looking for X, we will find X. Audit
  specifically for what would *contradict* current assumptions, not just confirm them.

Note any of these that bit this cycle in the audit summary.
