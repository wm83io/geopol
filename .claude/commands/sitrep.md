---
description: Compose the daily Iran 2026 SITREP annex against the base synthesis and most recent probe sweep
---

# Iran 2026 — Daily SITREP Composer

Composes the daily annex update to the base synthesis. Output is a delta document, not a rewrite.

---

## Pre-flight

Load in order before drafting. All paths are relative to the repo root.

1. **Anchor:** read highest-versioned file in `synthesis/`
   (e.g. `synthesis-v3-0.md`). This is the delta target. Do not rewrite.
2. **Last annex:** read highest day-number file in `sitreps/`
   (e.g. `day-70-pm.md`). Establishes rolling baseline.
3. **Probe sweep:** read most recent file in `probes/sweeps/`
   (e.g. `sweep-2026-05-09.json`). Primary input for sections 2-4.
   If no sweep exists for current cycle, flag at top of SITREP and proceed with reduced confidence. Do not silently skip.
4. **Appendix B:** read `appendix/appendix-b-blind-spots.md`
   for section 6 probe status.
5. **Output schema:** read `probes/probe-schema.md`
   for probe-to-framework variable mapping.

After drafting, write output directly to `sitreps/day-{N}.md` using the Write tool.
Confirm write succeeded before reporting completion.

---

## Search before writing

Targeted searches for developments since the last SITREP. Cap at 8-12 total. Chase signal that moves framework variables, not comprehensiveness.

Priority sources:

- CENTCOM operational announcements
- Iranian government statements (Araghchi, Ghalibaf, Vahidi, Pezeshkian)
- Oil tape (Brent, WTI, backwardation curve)
- War Powers / congressional developments
- ISW, ICG/Vaez, HCR Letters from an American (daily)
- logicofwar.com, mind-war.com, foreignaffairs.com, foreignpolicy.com for structural framing

---

## Document structure

Output filename: `day-{N}.md`

Header block:

```
# Iran 2026 Operational SITREP — Daily Update
**Day {N} | {Weekday}, {Month} {DD}, {YYYY}**
*Annex/Update to Iran 2026 Operational SITREP and Strategic Synthesis (base report v3.0)*
```

---

### Executive Summary

Written last, placed first. Three to five sentences plus a composite line. Answers four questions and surfaces one derived headline:

1. Single most important development since last SITREP?
2. Did the central thesis hold, drift, or break?
3. Dominant trajectory and probability?
4. Key trigger to watch in next 48-72 hours?
5. **Kinetic Escalation Composite (DERIVED)** — one sentence, format below.

Composite line format:

> *Kinetic Escalation Composite: ~X% (30d), ~Y% (12m) — derived from Fork A + Fork C + conflict-leading tails; Fork D' (deferral) excluded. Dominant non-escalation path: [Fork B / Fork D' / other] at Z%.*

The composite is recomputed each SITREP from the then-current synthesis matrix (Fork A primitive + Fork C primitive + conflict-leading tail register entries; Variants A/B absorbed as Fork A trigger paths, not added). It is a communication aid, not an analytical primitive — the analytical text in sections 3, 4, and 7 references primitives, not the composite.

No background. No restating the base framework. A reader dark for 24 hours should know exactly where things stand after this block.

---

### Section 1 — Operational Update

Developments since the last SITREP. Subsections by domain:

- **Diplomatic track** — proposals, rejections, mediator activity
- **Maritime / CENTCOM** — vessel counts, ROE changes, carrier posture
- **Iranian internal** — Vahidi/Mojtaba/Ghalibaf signals, rial, inflation
- **Lebanon / proxy fronts** — IDF, Hezbollah, Houthi posture
- **Cyber** — CISA advisories, stage progression, attribution
- **Markets** — Brent, WTI, S&P, VIX, gold, 10Y, gas price. Table format.
- **US domestic** — polling, War Powers, congressional, supplemental
- **International** — Russia, China, Gulf, European coalition

Factual, source-attributed. No editorializing. Flag confidence (H/M/L) for contested claims. Distinguish tape action from statement.

---

### Section 2 — Framework Validation

Which assumptions held this cycle. Format:

- **A{N} ({assumption name}):** one sentence on what validated it. Cite specific event.

Only list assumptions with confirming evidence this cycle. Do not re-list stable assumptions with no new signal.

---

### Section 3 — Framework Revisions Required

Where data forced changes. For each revision:

- Prior assumption/probability
- What data broke it
- Revised position

If the probe trigger digest contains immediate-urgency items, they go here, flagged **TRIGGER FIRED** with probe source.

If nothing requires revision, state so explicitly. Do not invent revisions.

---

### Section 4 — Framework Additions

New dynamics not in the base synthesis or prior annexes. Threshold: structural (repeating mechanism, new actor, new constraint layer), not one-off events. One-off events belong in Section 1.

If nothing new meets the threshold, omit this section.

---

### Section 5 — Revised Probability Matrix

Table format. Include only rows where probability moved this cycle or where a new outcome was added. Always include a delta column.

```
| Outcome | 30 days | 12 months | vs. last SITREP | Driver |
|---------|---------|-----------|-----------------|--------|
| ...     | X-Y%    | X-Y%      | up/down/stable  | one line |
```

Do not reprint the full matrix unchanged. Deltas only. Ranges, not point estimates.

If a primitive (Fork A, Fork C, or any conflict-leading tail component) moved this cycle, recompute the Kinetic Escalation Composite and report the new value in the Executive Summary composite line. The composite is derived, not a primitive; do not report a composite delta alone without the underlying primitive delta that drove it.

---

### Section 6 — Probe Status Table

Pull directly from probe sweep output, formatted per `probes/probe-schema.md` sweep summary table. If probes were not run, insert: `*Probe sweep not executed this cycle — see pre-flight note.*`

---

### Section 7 — Conclusion and Forking Analysis

Three parts:

1. **Central thesis check** — one sentence on whether the base report's central thesis (faction misalignment producing emergent escalation within constraint architecture) is holding, drifting, or breaking.

2. **Forking paths** — update the dominant trajectory and tail branches. Each fork: label, probability, one-paragraph driver, key indicator. No more than four forks. Dominant trajectory first.

3. **Key operative judgment** — one paragraph. Single most important thing the framework says about the next 48-72 hours. What signal would force immediate revision?

Footer: `*Compiled {date} | Day {N} | Subject to revision as data updates*`

---

## Tone and style discipline

- Factual, terse, no hedging filler.
- Discount Trump statements to near-zero unless corroborated. Note explicitly when relevant.
- Distinguish tape action from statement in market references.
- When sources conflict, name both sides and adjudicate. Do not average.
- No section longer than it needs to be. Compress or omit empty sections.
- Avoid em-dashes; use commas, semicolons, or restructure.

---

## Anti-patterns

- Do not rewrite the base synthesis. Annex equals delta.
- Do not pad Sections 2-4 by repeating Section 1 data.
- Do not produce probability point estimates. Ranges only.
- Do not let Section 7 become a news summary. It is forward-looking judgment.
- Do not omit Section 3 because revisions are uncomfortable. If data broke an assumption, say so.
- Do not synthesize new probe findings inside the composer. The composer consumes probe output; it does not re-run probes.
- Do not report the Kinetic Escalation Composite without the underlying primitives. The composite is derived; primitives drive analysis.
- Do not aggregate Fork D' into the composite. Fork D' is the deferred-kinetic / gray-zone path; aggregating it collapses the framework's most operative distinction.
