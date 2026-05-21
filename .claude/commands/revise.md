---
description: Version up the Iran 2026 synthesis and produce both internal and external blog versions
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

Load all of the following before writing a single word. All paths are relative to the repo root.

1. **Strategic trends baseline:** read `reference/strategic-trends.md` FIRST. A revision is a
   re-validation event: every active trend must be re-assessed against the cumulative
   SITREP/sweep evidence since last revision. Trend states feed both Version Notes (which
   trends moved across this revision interval) and the Methodological Note (which trends
   anchor the framework's voice discipline). For a major-version increment, every trend
   state must be re-validated explicitly; for a minor-version increment, only trends touching
   the manifest-listed mechanisms.
2. **Appendix C methodology:** read `appendix/appendix-c-methodology.md` in full. The synthesis's
   Methodological Note paragraph is a deterministic transform of Appendix C; voice discipline
   throughout the revision is governed by it. If a candidate revision drifts toward
   substrate-as-agent voice, the candidate is wrong; rewrite with agent as subject and
   constraint as modifier.
3. **Current synthesis:** read highest-versioned file in `synthesis/`
   This is the version being superseded.
4. **All SITREPs since last synthesis revision:** read all files in `sitreps/`
   in chronological order. The annex chain is the authoritative record of framework drift.
5. **Appendix B:** read `appendix/appendix-b-blind-spots.md`
6. **All probe sweeps since last revision:** read all files in `probes/sweeps/`
   in chronological order. The `reference_trends` field of each sweep is the trend-cross-check
   record; aggregate across the revision interval to identify trends that moved or held.
7. **Output schema:** read `probes/probe-schema.md`
8. **Staging directory:** check `synthesis/staging/` for any pending change
   manifests before drafting. If files exist, read them all in full. These are pre-staged
   structural revisions that must be incorporated into the new synthesis version — they are
   not optional inputs. A manifest in staging takes precedence over annex-derived inference
   for any mechanism or probability it explicitly covers.

   Multiple manifests are common (e.g., a data-driven change manifest plus a scope-expansion
   companion). Where sibling manifests overlap on a section, the scope-expansion manifest's
   structural framing takes precedence; the data-driven manifest's specific findings populate
   that framing as instances. Section letters across sibling manifests reference the same
   destination sections in the new synthesis; merge accordingly.

   After a successful synthesis write, move consumed manifests to `synthesis/staging/archive/`
   — do not delete them.
   If staging is empty, proceed normally.

### Trend re-validation discipline at revision

For every active trend in `strategic-trends.md`:

- Cite the cumulative evidence across the revision interval (SITREPs + sweeps).
- Confirm or transition the state per the rules in the trend tracker.
- If state transitions, the synthesis's Version Notes must mention the transition explicitly.
- If a reference-to-operational instrumentation gap exists (trend has no BS or PROBE), flag for
  the next /audit and note in Version Notes.
- If voice-discipline drift occurred in any SITREP since last revision, log in the trend
  tracker's drift log and address in Version Notes.

A revision is the only place trend states transition at synthesis-level scope. Audit-level
transitions are tactical; revision-level are confirmatory.

After producing both outputs:
- Write internal synthesis to `synthesis/synthesis-v{X-Y}.md`
- Write blog version to `synthesis/synthesis-v{X-Y}-external.md`
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
| Manifest item in staging | pre-validated | incorporate as settled; do not re-derive |

The annex chain is ground truth. The synthesis is its compression. Do not restate annex content —
extract the architecture underneath it.

### Mental inventory before drafting

- Which assumptions were validated, revised, or broken across the chain
- Which probability matrix entries drifted materially (>10 points or direction reversal)
- Which framework additions are now structural (repeat mechanism) vs still provisional
- Whether the central thesis held, strengthened, or requires reformulation
- Which staging manifest items are queued and how they interact with annex-derived findings

If the central thesis held, the revision is an update. If it requires reformulation, that must be
flagged explicitly and argued, not just substituted.

---

## Versioning Rules

| Increment | Trigger | Example |
|---|---|---|
| Minor (v2.5 → v2.6) | Updates that preserve central thesis and constraint architecture | Probability drift, new validated assumptions, mechanism additions |
| Major (v2.x → v3.0) | Reformulation of central thesis, new constraint layer, restructured probability architecture | Constraint layer 4 promoted to permanent; thesis breaks |

Derived elements (composites such as the Kinetic Escalation Composite) and tail-register additions do not by themselves drive a major increment. They are structural in form but additive in effect — they sit alongside existing primitives without replacing them. Major increments require thesis reformulation or constraint-layer change, not new derived headlines.

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
2a. **Methodological Note** — mandatory paragraph placed immediately after Executive Summary in the internal synthesis only. 70-110 words. Names the framework's intellectual provenance: bargaining model (Fearon 1995; Powell 1999); two-level games (Putnam 1988); system-effects emergence (Jervis 1997); path dependence (Pierson 2000); neoclassical realism (Rose 1998). Engels-register materialist substrate, not vulgar-materialist. Cross-references `reference/costly-signaling-framework.md` and `appendix/appendix-c-methodology.md`. Closes by stating: the framework predicts dominant strategies under joint constraints; it does not predict selection. Treat as boilerplate after first revision (rewrite only if a new tradition is added or a citation is retired). Stripped from external version (see Transform table).
3. **Conflict Timeline and Operational Status** — key events to current day; current posture
4. **Market Snapshot** — table format, updated levels
5. **Constraint Architecture** — five layers (L1 military physics, L2 asymmetric-conflict logic, L3 time arithmetic, L4 faction misalignment, L5 principal-agent gap). Update each layer if data moved it.
6. **Ideological Currents and Motives** — only update where actor posture has materially shifted
7. **Structural Dynamics and Mechanisms** — update existing mechanisms; add new ones only if structural threshold met
8. **Probability Assessment** — full matrix, updated, direction arrows vs prior version. Include the Kinetic Escalation Composite as a derived line immediately after the primitive matrix, explicitly labeled "DERIVED" with construction formula (Fork A + Fork C + conflict-leading tail components; Fork D' and Variants A/B excluded). Tail-Risk Residual Register sits as a separate sub-section listing exogenous / actor-replacement events outside the fork architecture. The composite never replaces primitives; it sits alongside them as a communication headline.
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
- Any item explicitly listed in a staging manifest

### Update only if materially changed
- Constraint layers 1-2 (military physics, asymmetric-conflict logic) — structural; update only if a new capability or doctrine has been confirmed
- Ideological currents — actor posture only if a named actor's position has demonstrably shifted, not just been tested
- Structural dynamics mechanisms — add only if a mechanism has appeared in 3+ annexes and is not explainable by existing ones

### Preserve unless broken
- Central thesis
- Faction misalignment model
- July 1914 historical analog
- "Nobody chooses the reordering" formulation, game-theoretic version (per DELTASYNTHESIS §1)
- Constraint architecture's five-layer structure (L1 military physics, L2 asymmetric-conflict logic, L3 time arithmetic, L4 faction misalignment, L5 principal-agent gap)

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

**Exception:** a dynamic explicitly listed in a staging manifest with a structural designation bypasses
the three-annex threshold. The manifest represents pre-validated conclusions from the probe/SITREP
chain; re-applying the threshold to already-validated findings is redundant.

---

## Probability Matrix Discipline

- Use ranges, not point estimates
- Direction arrows: `↑ ↓ →` (up, down, stable) vs prior version
- Add a `vs v{N}` column showing direction since last *synthesis*, not since last annex
- 12-18 rows maximum. Merge outcomes driven by the same mechanism.
- Mutually exclusive outcomes flagged where they genuinely are; most outcomes are not, and should not be presented as if they are

---

## Central Thesis Handling

The current central thesis (v4.0):

> The Iran 2026 conflict is a trigger event accelerating a tripolar reordering of the international system. The framework operates as a materialist bargaining model: five layers of material substrate (military physics, asymmetric-conflict logic, time arithmetic, faction misalignment, and the principal-agent gap) condition each principal's decision set; faction misalignment and PA-gap dynamics determine form and timing within those sets; Bayesian updates on correlated signal clusters tighten or loosen priors on which option becomes the dominant strategy for each principal at each cycle. Nobody designs the reordering. It is the joint equilibrium of constrained choices when no actor controls the constraint surface. The framework ranks options under the surface; the actors select.

| Incoming data | Action |
|---|---|
| Supports thesis | Restate, update supporting evidence, tighten the argument |
| Partially contradicts | Identify specific element that broke, propose minimal reformulation, flag explicitly |
| Fundamentally breaks | Major version increment. New thesis stated in Version Notes, argued in Executive Summary, supported by probability matrix. Do not bury a thesis change in body text. |

---

## Tone and Style Discipline

- Terse, factual, no hedging filler
- Discount Trump statements to near-zero unless corroborated
- Distinguish tape action from statement in market references
- When sources conflict, adjudicate, do not average
- No section longer than it needs to be
- Write for a reader returning after 2-3 weeks dark, not for a reader who read yesterday's annex
- The synthesis is the anchor document; it must be self-contained
- Every probability range must be defensible from the text; do not assert numbers that have no mechanism backing them

### Methodological discipline (from DELTASYNTHESIS, 2026-05)

**Forbidden constructions (substrate-as-agent voice):**

- "The architecture selected / composed / innovated / closed / opened / chose..."
- "The constraint set composed / produced / engineered..."
- "No principal chose this; X did it instead..."
- "The framework constructs / builds / resolves..."
- "The architecture is composing toward..."
- "What the architecture selected as resolution mechanism..."
- "The reordering is the architecture choosing for them"
- Any verb of intention or agency whose subject is the substrate, the architecture, the constraint set, the framework, or the system.

**Required constructions (constrained-agent / game-theoretic voice):**

- "Under constraint X, the relative cost-benefit of pathway Y improves against Z; selection by {named actor} remains contingent..."
- "Constraints compress the principal choice set; principals select within it..."
- "Pathway Y is the dominant strategy under joint constraints (A, B, C)..."
- "Option Y moves from sub-dominant to dominant when constraint Z binds..."
- "Signal cluster X tightens the prior that selection of Y is being weighted..."
- "The trajectory emerges as the equilibrium of constrained choices when no actor controls the constraint surface..."

**Distinguishing valid from invalid uses of "architecture":**

- Valid (noun, structure): "the alliance architecture," "the constraint architecture is reinforced," "the principal-access architecture."
- Invalid (subject of intention verb): "the architecture selected," "the architecture composes."

When the framework appears as subject: only epistemic verbs (`reads`, `predicts`, `ranks`, `weights`, `names`, `maps`). Never choice verbs.

**Additional rules:**

- Substrate-as-agent constructions are the highest-priority style failure. They falsify the methodological frame. Treat them as factual errors, not style preferences.
- When a sentence about a new mechanism, pathway, or option does not name the human or institutional actor whose selection is contingent, the sentence is incomplete. Add the actor.
- Predictions are of the form "Y becomes the dominant strategy / tightens the prior on Z," never "Y will happen / Y is the outcome the architecture is selecting."

---

## Dual Output Architecture

Both files are produced. The internal is the analytical artifact; the external is its public-facing
projection. They share the same content but differ in scaffolding.

```
Internal (project anchor)              External (blog publication)
────────────────────────              ──────────────────────────
synthesis-v{N}.md                      synthesis-v{N}-external.md

Version Notes section            →     stripped
Methodological Note paragraph    →     stripped
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
- Which staging manifest items were incorporated and archived

### External (blog) version — derived

Run the transform table above against the internal. Result is a single coherent standalone document.

**Required structure:**

1. **Title** — substantive, evocative, no version number. Pick from acceptable patterns; do not generate variants of forbidden patterns.

   Acceptable patterns:

   | Pattern | Why it works |
   |---|---|
   | "Iran 2026: The Equilibrium Nobody Designed" | Game-theoretic emergence frame; preserves the surprise move |
   | "Iran 2026: Constraints Compress the Choice Set" | Names what the framework actually does; agent voice retained |
   | "Iran 2026: When the Dominant Strategy Is Surgical" | Names the move at the current cycle; actor implicit (US executive) |
   | "Iran 2026: The Constraint Surface and the Compressed Game" | Structure + game-theoretic frame; no agency to substrate |

   Forbidden patterns (do not use, do not generate variants of):

   - Anything with `architecture chooses / selects / decides / picks / composes`
   - Anything with `the system wants / the framework engineers / the substrate produces`
   - Anything with `constraints choose / constraints engineer outcomes`

2. **Italicized framing note** — date, day count, one-sentence framing of what this is
3. **TL;DR** (blockquote) — central thesis + dominant trajectory + key shift since prior post, ~3-5 sentences
4. **Body** — natural section headers, narrative arc: Frame → Operational → Markets → Constraint Architecture → External Players → Structural Mechanisms → Outcome Table → Forking Analysis → Synthesis → Indicators
5. **Outcome architecture table** — full matrix with `vs prior` direction column
6. **Forking analysis** — dominant trajectory + tail branches, with conditional probability structure where applicable
7. **Italicized closing line** — single sentence stating the equilibrium under current constraints, with the actor whose selection remains contingent named or implicit. Substrate-as-agent failures here propagate widely because the post is shared and quoted; treat with the same discipline as the central thesis.

**Style guardrails:**

- No em-dashes anywhere. Use hyphens, semicolons, colons. (Non-negotiable.)
- No internal jargon: no "PROBE-N," "BS-N," "Appendix A," "Appendix B," "v2.5," "Validated/Revisions/Additions"
- Self-contained: a reader who never saw the prior version should follow the argument fully
- Tables wherever comparison or scannability helps (constraint layers, outcomes, indicators)
- Bold inline emphasis for the analytical hinges, not headers
- No "subject to revision" footers, no "companion document" framing
- No academic citation names without inline definition: named theoretical mechanisms (Fearon-Slantchev, Talmadge, Powell, Weisiger, Reiter-Weisiger, etc.) must be defined parenthetically on first use or replaced with plain-language equivalents. Use the concept; not the citation.
- No game-theory jargon without definition: "win-set," "joint feasible set," "information rent," "commitment device," "type-revelation" require plain-language equivalents or an inline parenthetical definition on first use.
- No inherited-mechanism parenthetical lists: when noting that prior-cycle mechanisms continue to operate, name the category ("several structural mechanisms from the prior cycle continue to shape this configuration") not individual mechanism names. External readers lack the context to parse a named-mechanism inventory.

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

- Internal: version increment + rationale, assumption status changes, biggest probability moves, central thesis disposition, staging manifest items incorporated
- External: title chosen, framing note, TL;DR, transform deltas applied (which scaffolding was stripped)

---

## Anti-patterns

- Do not treat the synthesis as a news summary. Events belong in annexes; mechanisms belong in the synthesis.
- Do not revise for recency. An event is synthesis-worthy only if it changes the architecture, not just the operational picture.
- Do not let probability ranges creep wider each version as a hedge. Wider ranges mean less analytical work, not more epistemic humility.
- Do not quietly drop assumptions that proved wrong. Mark them revised with rationale; the error is as informative as the correction.
- Do not produce a synthesis longer than the prior version without justification. Accretion without retirement is intellectual hoarding.
- Do not carry academic citation names from the internal into the external without inline definitions. The external tracks the argument, not the literature. If the internal says "Fearon-Slantchev type-revelation without convergence: information rents were exhausted," the external says "the costly kinetics exhausted informational value without converging positions." Named mechanisms (Talmadge, Powell, Weisiger, Reiter-Weisiger) must be defined in the same sentence or replaced with what they mean.
- Do not enumerate inherited mechanism names in the external. "Several structural mechanisms from the prior cycle continue to operate" is correct external framing; listing twelve named mechanisms by name is not. The list belongs in the internal version.
- Do not let the external version drift in substance from the internal. The external is a transform, not a re-write. If you find yourself making a different argument in the blog version, stop — the difference belongs in the next internal revision.
- Do not overwrite the external blog file — always use versioned filename `synthesis-v{N}-external.md`.
- Do not skip producing the external version because "the user can do it later." Both outputs are the deliverable.
- Do not skip the staging directory check. A manifest in staging represents pre-validated structural changes argued through the probe and SITREP chain. Ignoring it forces re-derivation of conclusions that are already settled.
- Do not leave staging manifests in place after a successful synthesis write. Move them to `synthesis/staging/archive/` to mark them as consumed.

### Methodological discipline (from DELTASYNTHESIS, 2026-05)

1. **Do not preserve the old thesis sentence "as a courtesy to readers familiar with it."** The old formulation is the source of the drift. Quoting it in the new version, even framed as "the prior formulation said X, now corrected to Y," reintroduces the construction into the synthesis text and into future model context. Make the correction in Version Notes; do not quote the old sentence.
2. **Do not let the external version drift back to teleological voice for "narrative flow."** The external is a transform of the internal. If the internal is methodologically tight, the external is too. Stylistic concessions that reintroduce substrate-as-agent voice for readability are exactly the drift this directive corrects.
3. **Do not predict selection.** The framework ranks options under the constraint surface and identifies dominant strategies under specified joint constraints. It does not say "X will be selected." It says "Y becomes the dominant strategy under joint constraints (A, B, C); selection by {actor} remains contingent and tightens / loosens conditional on signal cluster Z."
4. **Do not use "convergence" or "cluster" as causal verbs.** Signal clusters tighten priors. They do not cause outcomes. The grammar of probabilistic updating, not the grammar of teleology, governs.
5. **Do not invoke the July 1914 analog as substrate-determinism.** The analog is valid as a structural-constraint comparison (mobilization timetables, bargaining-geometry compression, principal-agent ratification failures). It is invalid as "1914 chose itself / the system chose war." If the analog is invoked, the historical actors stay as subjects of intention verbs (the German General Staff, Sazonov, Berchtold), not the war itself.
6. **Do not let "emergence" do the work "architecture chose" used to do.** Emergence is a valid concept in game theory and complex-systems analysis when an aggregate outcome is the equilibrium of individual constrained choices. It is invalid when it smuggles intention back in ("the system emerges toward war" is teleology dressed as physics). Test: can you specify the individual decision rules and the constraint surface that produces the equilibrium? If yes, emergence is doing real work. If no, it is rhetorical filler covering the same teleological pattern.
