---
name: iran-2026-sitrep-composer
description: >
  Composes the daily Iran 2026 SITREP annex against the base synthesis and the most recent probe sweep.
  Invoke when the user says "write the SITREP", "daily SITREP", "Day N update", "compose the annex",
  "draft today's annex", "Iran 2026 update", or asks for a SITREP after a trigger event. Also invoke
  automatically after a probe sweep completes, after a high-impact news event in the Iran/US/Israel
  theatre, or when the user requests a delta against the prior daily file. Produces a single dated
  annex file in the canonical seven-section structure (Exec Summary, Operational Update, Validation,
  Revisions, Additions, Probability Matrix, Probe Status, Forking Conclusion). Use this skill whenever
  Iran 2026 framework SITREP composition, daily annex drafting, or framework delta reporting is
  requested — even if the user does not use the word "SITREP" explicitly.
---

# Iran 2026 — Daily SITREP Composer

Composes the daily annex update to the base synthesis. Output is a delta document, not a rewrite.

---

## Pre-flight

Load in order before drafting. Read from filesystem MCP at `D:\claude\geopol`.
Use Filesystem tools directly — do not rely on project_knowledge_search for these files.

1. **Anchor:** read highest-versioned file in `D:\claude\geopol\synthesis\`
   (e.g. `synthesis-v3-0.md`). This is the delta target. Do not rewrite.
2. **Last annex:** read highest day-number file in `D:\claude\geopol\sitreps\`
   (e.g. `day-70-pm.md`). Establishes rolling baseline.
3. **Probe sweep:** read most recent file in `D:\claude\geopol\probes\sweeps\`
   (e.g. `sweep-2026-05-09.json`). Primary input for sections 2-4.
   If no sweep exists for current cycle, flag at top of SITREP and proceed with reduced confidence. Do not silently skip.
4. **Appendix B:** read `D:\claude\geopol\appendix\appendix-b-blind-spots.md`
   for section 6 probe status.
5. **Output schema:** read `D:\claude\geopol\probes\probe-schema.md`
   for probe-to-framework variable mapping.

After drafting, write output directly to `D:\claude\geopol\sitreps\day-{N}.md`
via filesystem MCP. Confirm write succeeded before reporting completion.

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

Output filename: `iran-2026-sitrep-day{N}-update.md`

Header block:

```
# Iran 2026 Operational SITREP — Daily Update
**Day {N} | {Weekday}, {Month} {DD}, {YYYY}**
*Annex/Update to Iran 2026 Operational SITREP and Strategic Synthesis (base report v2.0)*
```

---

### Executive Summary

Written last, placed first. Three to five sentences. Answers four questions:

1. Single most important development since last SITREP?
2. Did the central thesis hold, drift, or break?
3. Dominant trajectory and probability?
4. Key trigger to watch in next 48-72 hours?

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

---

### Section 6 — Probe Status Table

Pull directly from probe sweep output, formatted per `iran-2026-probe-output-schema.md` sweep summary table. If probes were not run, insert: `*Probe sweep not executed this cycle — see pre-flight note.*`

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
