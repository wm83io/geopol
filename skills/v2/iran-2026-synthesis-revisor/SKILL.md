---
name: iran-2026-synthesis-revisor
description: >
  Revises and versions up the Iran 2026 base synthesis AND produces a parallel blog-ready external
  version stripped of internal bookkeeping. Invoke when the user says "update the synthesis", "revise
  the framework", "version up", "new synthesis", or after annexes show material framework drift. Also
  invoke after 5+ daily annexes accrue, after 3+ framework revision triggers fire across probe cycles,
  or after a structural break (new constraint layer, new principal actor, central thesis drift) that
  daily annexes cannot absorb. Produces TWO files: the internal synthesis (version notes, PROBE-N /
  BS-N / Appendix refs, validation jargon — required for framework to keep functioning) and the
  external blog version (single coherent standalone document, table-heavy, no scaffolding, modeled on
  blog.wntrdev.ca/posts/iran-framework-update). Opus task. Use whenever synthesis revision, framework
  version-up, or blog-publishable framework refresh is requested.
---

# Iran 2026 — Synthesis Revisor

Produces a new versioned synthesis from accumulated SITREP / annex drift. **Always produces two outputs:**
the internal synthesis (with bookkeeping required for the framework to function) and the external blog
version (stripped for publication). Both come from the same analytical pass; the external is a
deterministic transform of the internal, not a separate analysis.

**Cadence:** not for single-event updates. Synthesis revises when the *architecture* moves, not when the
*news* moves. News belongs in daily annexes.

**This is an Opus task.** Complexity and stakes require it.

---

## Pre-flight

Load all of the following before writing a single word. Read from filesystem MCP at `D:\claude\geopol`.
Use Filesystem tools directly — do not rely on project_knowledge_search for these files.

1. **Current synthesis:** read highest-versioned file in `D:\claude\geopol\synthesis\`
   This is the version being superseded.
2. **All SITREPs since last synthesis revision:** read all files in `D:\claude\geopol\sitreps\`
   in chronological order. The annex chain is the authoritative record of framework drift.
3. **Appendix B:** read `D:\claude\geopol\appendix\appendix-b-blind-spots.md`
4. **All probe sweeps since last revision:** read all files in `D:\claude\geopol\probes\sweeps\`
   in chronological order.
5. **Output schema:** read `D:\claude\geopol\probes\probe-schema.md`

After producing both outputs:
- Write internal synthesis to `D:\claude\geopol\synthesis\synthesis-v{X-Y}.md`
- Write blog version to `D:\claude\geopol\synthesis\synthesis-v{X-Y}-external.md`
Confirm both writes succeeded. Never overwrite an existing synthesis file.

### Annex chain scan — do this before drafting

Read each annex's Section 2 (Framework Validation), Section 3 (Framework Revisions Required), and
Section 4 (Framework Additions) in sequence. Build a running tally:

| Signal | Threshold | Treatment |
|---|---|---|
| Assumption validated in 3+ annexes | stable | preserve |
| Assumption revised in any annex | drift | note revision + driver |
| Assumption broken | structural break | flag in Version Notes |
| Probability moved >10pts or reversed direction | material | list with drivers |
| Framework addition in 3+ annexes | structural threshold | promote from provisional |
| Trigger digest from probe sweep | revision input | primary input |

The annex chain is ground truth. The synthesis is its compression. Do not restate annex content —
extract the architecture underneath it.

### Mental inventory before drafting

- Which assumptions were validated, revised, or broken across the chain
- Which probability matrix entries drifted materially (>10 points or direction reversal)
- Which framework additions are now structural (repeat mechanism) vs still provisional
- Whether the central thesis held, strengthened, or requires reformulation

If the central thesis held, the revision is an update. If it requires reformulation, that must be
flagged explicitly and argued, not just substituted.

---

## Versioning Rules

| Increment | Trigger | Example |
|---|---|---|
| Minor (v2.5 → v2.6) | Updates that preserve central thesis and constraint architecture | Probability drift, new validated assumptions, mechanism additions |
| Major (v2.x → v3.0) | Reformulation of central thesis, new constraint layer, restructured probability architecture | Constraint layer 4 promoted to permanent; thesis breaks |

- **Internal filename:** `synthesis-v{N}.md`
- **External filename:** `synthesis-v{N}-external.md`
- Add a **Version Notes** section at the top of the *internal* document (below header block) listing what changed substantively from prior version. 5-8 bullets. Diff summary for readers returning after an absence.

---

## Internal Document Structure

Preserve existing section architecture unless a section is genuinely obsolete or a new one is
structurally required. Do not reorganize for aesthetics.

Mandatory sections in order:

1. **Version Notes** — what changed from prior version
2. **Executive Summary** — central thesis, dominant trajectory, key constraints, probability headline. 4-6 paragraphs. Rewritten each version.
3. **Conflict Timeline and Operational Status** — key events to current day; current posture
4. **Market Snapshot** — table format, updated levels
5. **Constraint Architecture** — three layers (military physics, asymmetric-conflict logic, time arithmetic) plus faction misalignment as Layer 4. Update each layer if data moved it.
6. **Ideological Currents and Motives** — only update where actor posture has materially shifted
7. **Structural Dynamics and Mechanisms** — update existing mechanisms; add new ones only if structural threshold met
8. **Probability Assessment** — full matrix, updated, direction arrows vs prior version
9. **Key Assumptions** — numbered list, each with current validation status
10. **Most Probable Outcome Architecture** — dominant trajectory + tail branches
11. **Conclusions** — rewritten each version; must engage central thesis directly
12. **Key Indicators to Monitor** — updated watchlist

---

## What to Update vs What to Preserve

### Always update
- Probability matrix entries that moved in annexes
- Assumption validation status
- Operational posture (Section 3)
- Market levels (Section 4)
- Time arithmetic in constraint architecture (Layer 3)
- Most probable outcome architecture

### Update only if materially changed
- Constraint layers 1-2 (military physics, asymmetric-conflict logic) — structural; update only if a new capability or doctrine has been confirmed
- Ideological currents — actor posture only if a named actor's position has demonstrably shifted, not just been tested
- Structural dynamics mechanisms — add only if a mechanism has appeared in 3+ annexes and is not explainable by existing ones

### Preserve unless broken
- Central thesis
- Faction misalignment model
- July 1914 historical analog
- "Reordering nobody is choosing" formulation
- Constraint architecture's three-layer structure

If any of the above require modification, argue it explicitly in Version Notes and Executive Summary.
Do not quietly rewrite them.

---

## Structural Threshold for New Dynamics

A dynamic qualifies for permanent inclusion if it meets **two of three**:

1. Appeared in 3+ consecutive daily annexes without being resolved
2. Has a named mechanism (not just a pattern of events)
3. Changes the probability of at least one matrix entry by >8 points

Provisional dynamics (one or two annex mentions) go in a **Provisional Dynamics** subsection within
Section 7, clearly flagged. They graduate to permanent on next revision if threshold is met.

---

## Probability Matrix Discipline

- Use ranges, not point estimates
- Direction arrows: `↑ ↓ →` (up, down, stable) vs prior version
- Add a `vs v{N}` column showing direction since last *synthesis*, not since last annex
- 12-18 rows maximum. Merge outcomes driven by the same mechanism.
- Mutually exclusive outcomes flagged where they genuinely are; most outcomes are not, and should not be presented as if they are

---

## Central Thesis Handling

The current central thesis (v2.x):

> The Iran 2026 conflict is a trigger event accelerating a tripolar reordering of the international
> system. Three constraint layers operate prior to faction decision-making — military physics,
> asymmetric-conflict logic, and time arithmetic. Faction misalignment determines style and timing
> within these constraints; it does not determine the trajectory. The reordering nobody is choosing is
> the architecture choosing for them.

| Incoming data | Action |
|---|---|
| Supports thesis | Restate, update supporting evidence, tighten the argument |
| Partially contradicts | Identify specific element that broke, propose minimal reformulation, flag explicitly |
| Fundamentally breaks | Major version increment. New thesis stated in Version Notes, argued in Executive Summary, supported by probability matrix. Do not bury a thesis change in body text. |

---

## Tone and Style Discipline

Identical to the daily SITREP skill:

- Terse, factual, no hedging filler
- Discount Trump statements to near-zero unless corroborated
- Distinguish tape action from statement in market references
- When sources conflict, adjudicate, do not average
- No section longer than it needs to be

Additional for synthesis:

- Write for a reader returning after 2-3 weeks dark, not for a reader who read yesterday's annex
- The synthesis is the anchor document; it must be self-contained
- Every probability range must be defensible from the text; do not assert numbers that have no mechanism backing them

---

## Dual Output Architecture

Both files are produced. The internal is the analytical artifact; the external is its public-facing
projection. They share the same content but differ in scaffolding.

```
Internal (project anchor)              External (blog publication)
────────────────────────              ──────────────────────────
iran-2026-sitrep-synthesis-v{N}.md     iran-2026-framework-blog.md
                                       
Version Notes section            →     stripped
"v2.5 supersedes v2.0"           →     stripped
PROBE-N references               →     stripped
BS-N / Appendix B references     →     stripped
"Validated / Revisions /         →     stripped
 Additions" jargon
"Framework Self-Correction       →     folded into narrative (no label)
 Note" as labeled section
Companion-document footers       →     stripped
"Subject to revision" notice     →     stripped
Numbered sections (1-12)         →     natural section headers
                                       (no "Section 7", etc.)
em-dashes                        →     hyphens / semicolons / colons
                                       (per blog style preference)
                                       
                                 +     TL;DR block at top
                                 +     italicized framing note at top
                                       (date, day count, what this is)
                                 +     italicized closing line at bottom
                                 +     heavy table use for scannability
                                 +     coherent narrative arc, no internal
                                       version seams
```

### Internal version — first

Produce the complete revised synthesis as a standalone file. Do not produce a diff or patch. The new
version replaces the old as the project anchor.

After writing, state explicitly:
- Version increment and rationale (minor vs major)
- Which assumptions changed status
- Which probability entries moved most materially
- Whether central thesis was preserved, updated, or reformulated

### External (blog) version — derived

Run the transform table above against the internal. Result is a single coherent standalone document
modeled on `https://blog.wntrdev.ca/posts/iran-framework-update/`.

**Required structure:**

1. **Title** — substantive, evocative, no version number (e.g. "Iran 2026: The Architecture Chooses the Exit")
2. **Italicized framing note** — date, day count, one-sentence framing of what this is
3. **TL;DR** (blockquote) — central thesis + dominant trajectory + key shift since prior post, ~3-5 sentences
4. **Body** — natural section headers, narrative arc: Frame → Operational → Markets → Constraint Architecture → External Players → Structural Mechanisms → Outcome Table → Forking Analysis → Synthesis → Indicators
5. **Outcome architecture table** — full matrix with `vs prior` direction column
6. **Forking analysis** — dominant trajectory + tail branches, with conditional probability structure where applicable
7. **Italicized closing line** — single sentence stating the architectural conclusion

**Style guardrails:**

- No em-dashes anywhere. Use hyphens, semicolons, colons. (User preference; non-negotiable.)
- No internal jargon: no "PROBE-N," "BS-N," "Appendix A," "Appendix B," "v2.5," "Validated/Revisions/Additions"
- Self-contained: a reader who never saw the prior version should follow the argument fully
- Tables wherever comparison or scannability helps (constraint layers, outcomes, indicators)
- Bold inline emphasis for the analytical hinges, not headers
- No "subject to revision" footers, no "companion document" framing

**What NOT to strip from external:**

- Substantive analytical content (every mechanism, every probability, every named actor)
- The July 1914 analog if invoked
- The central thesis in its current formulation
- Quotations and named-source citations
- Specific numerical claims ($118 Brent, $25B war cost, etc.)

Stripping is *scaffolding only*. The argument is identical; only the bookkeeping is removed.

---

## Output

Two files produced in the same task:

1. `synthesis-v{N}.md` — internal anchor
2. `synthesis-v{N}-external.md` — external blog version

After producing both, state:

- Internal: version increment + rationale, assumption status changes, biggest probability moves, central thesis disposition
- External: title chosen, framing note, TL;DR, transform deltas applied (which scaffolding was stripped)

---

## Anti-patterns

- Do not treat the synthesis as a news summary. Events belong in annexes; mechanisms belong in the synthesis.
- Do not revise for recency. An event is synthesis-worthy only if it changes the architecture, not just the operational picture.
- Do not let probability ranges creep wider each version as a hedge. Wider ranges mean less analytical work, not more epistemic humility.
- Do not quietly drop assumptions that proved wrong. Mark them revised with rationale; the error is as informative as the correction.
- Do not produce a synthesis longer than the prior version without justification. Accretion without retirement is intellectual hoarding.
- Do not let the external version drift in substance from the internal. The external is a transform, not a re-write. If you find yourself making a different argument in the blog version, stop — the difference belongs in the next internal revision.
- Do not overwrite the external blog file — always use versioned filename `synthesis-v{N}-external.md`. Blog versioning is implicit by post date.
- Do not skip producing the external version because "the user can do it later." Both outputs are the deliverable.
