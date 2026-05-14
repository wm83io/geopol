---
description: Transform the latest daily SITREP into a published blog annex with Hugo frontmatter, an image prompt, and visual continuity with prior posts
---

# Iran 2026 — Daily Annex Blog Composer

Transforms a daily SITREP into a publishable Hugo blog post under `posts/iran/day-N.md`. Produces **three artifacts** in one task:

1. The blog markdown with Hugo frontmatter, written to `output/blog/day-N.md`
2. A Nano Banana image prompt for the cover, written to `output/blog/day-N-image-prompt.md`
3. A copy of the blog markdown placed at `/run/media/winterdev/Data/myblog/content/posts/iran/day-N.md`

The blog is a **deterministic transform of the SITREP**, not a separate analysis. Analytical content is identical; only scaffolding and vocabulary change. If you find yourself making a different argument than the SITREP, stop. The difference belongs in the next SITREP, not in the blog rewrite.

**Cadence:** runs once per SITREP. Do not run if no new SITREP exists since the last published blog.

---

## Pre-flight

Load all of the following before drafting a single line.

1. **Source SITREP:** highest day-number file in `sitreps/` (e.g. `sitreps/day-76.md`). This is the input.
2. **Prior published blog:** highest day-number file in `/run/media/winterdev/Data/myblog/content/posts/iran/` (e.g. `day-74.md`). This is the style and continuity reference. Read the frontmatter and the closing footer in particular.
3. **Prior cover image:** read the image file alongside the prior blog (e.g. `day-74.png`) using the Read tool. Build a one-paragraph visual style inventory: palette, composition, illustration style, recurring symbolic elements. This becomes the anchor for the new image prompt.
4. **Anchor synthesis:** highest-versioned file in `synthesis/` for thesis check.

If `output/blog/` does not exist, create it. If the destination `/run/media/winterdev/Data/myblog/content/posts/iran/` does not exist, stop and ask the user.

After writing, confirm all three files exist and report the paths.

---

## Title Convention

Title format: `Iran Day N - [Clause One]; [Clause Two]`

Two short clauses separated by a semicolon. The two clauses should be in tension or paradox, naming the cycle's central reframe. Examples from the canon:

- Day 74: `Iran Day 74 - The MOU Is Dead; The Negotiation Continues`
- Day 76: `Iran Day 76 - The Hardline Decayed; The Asymmetry Locked`

Draw the title from the SITREP's own title field if it follows the same convention; otherwise compose from the Executive Summary's central reframe. The title is the post's analytical hook; spend the cognitive effort to get it right.

---

## Hugo Frontmatter

```toml
+++
date = '{YYYY-MM-DDTHH:MM:SS-04:00}'
draft = true
title = 'Iran Day N - [Clause One]; [Clause Two]'
description = 'Annex/Update to Iran 2026 Operational SITREP and Strategic Synthesis (base report vX.Y)'
tags = ["iran", "geopolitics", "war", "sitrep", "diplomacy"]
[cover]
    image = "posts/iran/day-N.png"
    relative = false
+++
```

- Date: today's date in ISO format with America/Toronto offset (-04:00 EDT, -05:00 EST). Use a plausible compose-time hour, not midnight.
- Title: see above.
- Description: `Annex/Update to Iran 2026 Operational SITREP and Strategic Synthesis (base report vX.Y)` — fill in the current synthesis version number.
- Tags: base set is `["iran", "geopolitics", "war", "sitrep", "diplomacy"]`. The last 1-2 tags may be swapped for cycle-specific focus (e.g., `"nuclear"`, `"markets"`, `"escalation"`) if a different domain dominates the cycle.
- Cover path: `posts/iran/day-N.png` matching the filename of the blog file.
- `draft = true` so the post goes through a publish review before going live.

---

## Body Structure

The blog opens with the executive summary as plain prose — no section header. Main sections use `#` (h1); subsections use `##` (h2). No numbered sections anywhere. A `---` horizontal rule separates every major section.

```
{Executive summary. No header. 3-5 paragraphs. Opens with the cycle's single most important
development. Closes with the kinetic composite sentence: "Across paths to renewed military
action, cumulative probability sits at roughly X to Y percent over the next month and Y to Z
percent over the next year. The non-escalation path carrying most weight is [descriptive name]
at X to Y percent."}

---

# Operational Update

## Diplomatic Track
## Maritime and Military Posture
## [Actor] Internal Picture    {name the actor explicitly: "Iran's Internal Picture",
                                "Israel's Internal Picture"; add a second block if warranted}
## Markets                     {include the table from the SITREP, scrubbed for em-dashes}
## US Domestic
## International

---

# What Held This Week          {= SITREP "Framework Validation"}

---

# What Changed                 {= SITREP "Framework Revisions Required"}

---

# What's New                   {= SITREP "Framework Additions"; omit section if nothing new
                                meets the structural threshold}

---

# The Probability Picture      {= SITREP "Revised Probability Matrix": compact 4-column
                                summary table first, then prose. Both required.}

---

# Conclusion and What Comes Next

## Central Thesis Check
## The 72-Hour Picture          {= SITREP forking paths, prose}
## The Operative Judgment

---

*Compiled {Month} {DD}, {YYYY} | Day N | Subject to revision as data updates*
*Next SITREP: Day {N+1}-{N+2}. Watch: {scoped watchlist}.*
*Companion: Day {N-2} annex (operational baseline); synthesis-v{X}-{Y}.md (anchor).*
```

The probe status table is **omitted** from the blog. It is internal bookkeeping.

### Probability Picture section

The `# The Probability Picture` section opens with a compact summary table, then expands in prose. The table is scannable for returning readers; the prose carries the analytical weight. Both are required.

Table spec (4 columns, 5-8 rows):

| Trajectory | 30-day range | Direction vs prior post | Primary driver |
|---|---|---|---|
| {plain-English outcome name, not Fork letter} | {X-Y%} | {↑ ↓ → with one-word qualifier if needed} | {one short clause} |

Rules:
- Plain-English outcome names. Never `Fork A`, `Fork B`, etc. Use the descriptive translations: "Negotiated arrangement at modified terms," "Indefinite deferral," "Full kinetic resumption," "Miscalculation cascade," "Israeli unilateral pre-emption," "Materialized constitutional crisis."
- Probability ranges only, never point estimates.
- Direction arrows reference the prior published blog post, not the prior SITREP. If the prior published post was Day 74, the arrow shows the move from Day 74 to this cycle.
- Driver column: one short clause naming the cycle's operative mechanism for that outcome. Not a sentence.
- Include only trajectories that moved this cycle or are co-equal leaders. Stable secondaries can be summarized in prose without a table row.
- Add a final row for any new conditional outcome introduced this cycle.

After the table, the prose section walks through each row in 1-3 sentences, naming the conditions under which the range would tighten or shift further. Prose does the analytical work the table cannot carry.

---

## Transform Table (SITREP → blog)

| SITREP element | Blog treatment |
|---|---|
| SITREP header block (day/date line, annex/supersedes metadata) | Drop entirely. No header above the executive summary. |
| `## Title: {clause}` block | Drop. Title is in the frontmatter only. |
| `Framework Validation` section | Rename `What Held This Week` |
| `Framework Revisions Required` section | Rename `What Changed` |
| `Framework Additions` section | Rename `What's New` |
| `Revised Probability Matrix` table | Compress to a 4-column summary table at the top of `The Probability Picture`, then follow with prose. See "Probability Picture section" below for the table spec. |
| `Probe Status Table` (Section 6) | Drop entirely |
| `Forking Paths` (Section 7.2) | Render as `The 72-Hour Picture` prose |
| `PROBE-N`, `BS-N`, `A1`/`A4`/`A13` codes | Translate to plain English ("Iran-side principal-agent visibility," "Trump improvisational decision-making," etc.) or drop |
| `Fork A` / `Fork B` / `Fork C` / `Fork D'` labels | Translate to descriptive names ("full kinetic resumption," "negotiated arrangement at modified terms," "miscalculation cascade," "indefinite deferral") |
| `Kinetic Escalation Composite (DERIVED)` line in Executive Summary | Transform to external prose framing. Suggested phrasing: "Across the paths that lead to renewed military action — full kinetic resumption, miscalculation cascades, and a register of structural shocks outside the main trajectories — the cumulative probability sits at roughly X% over the next month and Y% over the next year. The non-escalation path that currently carries the most weight is [descriptive non-escalation name] at Z%." Preserve numeric values exactly; replace "Fork A / Fork C / tails / Fork D'" jargon with prose. Drop the "DERIVED" label — the construction is implied by the phrasing. |
| `TRIGGER FIRED (PROBE-N, IMMEDIATE)` headers | Drop the label, keep the analytical content |
| `v3.0` / `v3.1` version references | Translate to "the base framework" or "the current synthesis" |
| `sweep-YYYY-MM-DD.json` references | Drop |
| `Appendix B`, `BS-1a/b/c` references | Drop or restate as "the framework's blind spots" |
| em-dashes (everywhere) | Comma, semicolon, period, or restructure. **Non-negotiable: zero em-dashes in the output.** |
| Internal probability point estimates | Keep as ranges; never assert a single number |
| Day-N cross-references | Keep as `Day 74 reading` for continuity with prior posts |
| Source citations (CNN, ISW, Reuters, etc.) | Keep verbatim |
| Named-actor quotations | Keep verbatim |
| Specific numerics ($107 Brent, 49-50 vote, 98 days inventory) | Keep verbatim |

---

## Word Count Target

Approximately **75-85 percent** of the source SITREP word count. Measure with `wc -w` after writing. If the blog is over 90 percent, the transform did not strip enough scaffolding. If under 70 percent, analytical substance was lost. Common cuts: probe table, sweep metadata footer, internal cross-references, multi-source citation lists collapsed to primary source, redundant table cells.

---

## Continuity With Prior Posts

The blog series is read sequentially by a non-internal audience. Continuity discipline:

- Reference the prior post by day number explicitly ("the Day 74 reading concluded," "since Day 72"). Do not say "last cycle" or "previously."
- If a Day N-2 finding is being revised this cycle, name it: "the Day 74 framework added X; Day 76 refines that to Y."
- The metadata footer's `Companion: Day {N-2} annex` line must match the actual prior post number.
- The Hugo `[cover]` image filename must match the blog filename (`day-N.md` → `day-N.png`).

---

## Image Prompt Sidecar

Write `output/blog/day-N-image-prompt.md` containing a Nano Banana prompt for the cover image. Structure:

1. **Target line** — filename and one-sentence visual goal
2. **Conceptual anchor** — one paragraph summarizing the prior post's image (built from your style-inventory pre-flight read) and the visual shift required for this cycle. Name what you are deliberately changing this cycle and why.
3. **Primary prompt** — a single paragraph, paste-ready for Nano Banana. Include: aspect ratio (16:9 cinematic), an illustration style descriptor from the durable thread (see below), a palette specification chosen for this cycle, the composition's central conceit, symbolic elements keyed to the cycle's central reframe, an evocative middle and background, the standard exclusions ("no people, no text, no logos, no flags"), and a mood line
4. **Style reference tags** — short comma-separated tag list
5. **Negative prompt** — what to exclude (text, watermarks, photoreal, neon, cartoon, recognizable real persons)
6. **Symbolic key** — small table mapping each element of the prompt to the analytical idea it represents, for revision passes
7. **Revision heuristics** — three short bullets on what to ask for if the first generation overcrowds, skews palette, or misfires

### Visual identity: durable thread vs deliberate variation

The series is recognizable but not redundant. Two of the prior covers in a row sharing setting, palette, and symbolic class is a failure mode; the post should reward returning readers with a fresh visual angle that still feels like the same series.

**Durable thread (always present):**

- Allegorical composition. Not literal news scene, not photoreal reportage, not cartoon. The cover represents an analytical idea, not an event.
- Painterly or illustrative finish (digital matte painting, editorial illustration, ink-and-wash, woodcut, engraving, gouache, oil sketch — any of these qualify; pick one per cycle).
- Editorial-cover quality: cinematic 16:9, considered composition, depth of field where applicable.
- No text, no logos, no flags, no faces of named real figures.
- A mood register in the somber-to-foreboding range. No celebratory, no comedic.

**Variable (the surprise):**

- **Setting.** Default to the Hormuz strait, but rotate freely: mountain pass, desert horizon, oil-tanker silhouette at night, an empty negotiating room, a snow-bound forest, a ruined classical colonnade, a courtroom interior, an abandoned port, a globe under glass, a chessboard mid-game, a starlit waterfront. Setting should encode the cycle's central metaphor, not default to the strait.
- **Palette.** The slate-blue + ochre + burnt-orange dusk is one option, not the obligation. Rotate among: cold nocturne (deep blue, silver, charcoal); storm grey with a single warm accent; sepia and ivory; russet and bone; volcanic red and ash; high-contrast monochrome; mineral green and rust. Pick a palette that fits the cycle's emotional register, not the prior post's.
- **Symbolic vocabulary.** Chains, scrolls, seals, anchors, and pendulums are one shelf in a much larger cabinet. Also available: balance scales, hourglasses, clock faces, broken mirrors, doors ajar, keys, locks, threads woven or cut, knives, bread, salt, stones stacked, masks, candles, ink wells, sealed envelopes, mirrors, prisms, weather vanes, lighthouses, frayed ropes, knotted ropes, single shoes, empty chairs, tipped chess pieces, broken columns, drawn curtains, smoke, fog, snowdrifts, footprints leading into water. Choose objects the prior two posts have not used.
- **Perspective and scale.** Eye-level shore view is one option among many. Also: bird's-eye, worm's-eye, interior, claustrophobic close-up, vast desolate landscape, theatrical-stage framing.
- **Style finish.** Vary among matte painting, ink wash, gouache, etching, oil sketch, chiaroscuro engraving. Each gives a distinct surface.

### Anti-repetition rule

Before finalizing the prompt, audit the prior two covers (read the images if available). If this cycle's draft shares **two or more** of {setting class, palette family, dominant symbolic class, perspective} with either of the prior two, force a deliberate break on at least one axis. Name the break in the **Conceptual anchor** paragraph: "Prior cycles used X; this cycle deliberately shifts to Y because [analytical reason]."

The break should not be arbitrary. Tie the visual shift to the cycle's analytical reframe. A reversal cycle might call for a pendulum or weather vane; a lock-in cycle for a vault or a frozen surface; a deferral cycle for an empty stage or fog; a strangulation cycle for narrowing corridors or rationed objects; a constitutional cycle for chambers, scales, or empty seats; a markets cycle for tickertape, gauges, or candle charts rendered as sculpture.

### Worked example of variation logic

Day 74: strait, slate-blue and ochre, broken chain and sealed scroll, eye-level shore. Day 76: strait, slate-blue and ochre, partially restitched scroll and asymmetric chain, eye-level shore. Two consecutive covers sharing setting, palette, perspective, and symbolic class. **This is the redundancy failure mode the rule exists to prevent.** A correctly varied Day 78 would shift away from the strait entirely, or from the slate palette, or from the chain-and-scroll vocabulary, or from eye-level perspective. Pick the axis that the analytical reframe most naturally drives.

---

## Output

Three files in one task:

1. `/run/media/winterdev/Data/claude/geopol/output/blog/day-N.md` — the blog post
2. `/run/media/winterdev/Data/claude/geopol/output/blog/day-N-image-prompt.md` — the Nano Banana sidecar
3. `/run/media/winterdev/Data/myblog/content/posts/iran/day-N.md` — published copy (use the Bash `cp` tool)

After producing all three:

- Confirm each path exists
- Report blog word count and ratio to SITREP word count
- Run `grep -c "—" <blog file>` to confirm zero em-dashes
- Run a regex check for stray internal vocabulary: `grep -nE "PROBE-[0-9]|BS-[0-9]|Fork [A-D]|v[0-9]\.[0-9]|sweep-[0-9]" <blog file>` and confirm empty
- State the title chosen
- Remind the user the PNG must be generated separately and dropped at `posts/iran/day-N.png` to complete the post

---

## Style Discipline

- No em-dashes anywhere. Hyphens, commas, semicolons, periods. Non-negotiable.
- No internal jargon (PROBE-N, BS-N, Fork letters, version numbers, sweep filenames).
- Self-contained: a reader who has only seen earlier posts in this series should follow the argument fully.
- Discount Trump statements to near-zero unless corroborated; named-source citations stay.
- Distinguish tape action from statement.
- Bold inline emphasis only for analytical hinges, not for routine names or dates.
- Probability ranges, never point estimates.
- Tables retained for markets, for the probability summary (compact 4-column form, see Section 5 spec), and for the watchlist. Probe status table is removed.

---

## Anti-patterns

- Do not produce a different analysis than the SITREP. The blog is a transform, not a re-derivation. If you disagree with the SITREP, fix the SITREP first.
- Do not skip the prior-post read. Continuity language is the series' main value to returning readers.
- Do not invent a probability range. Every number must come from the SITREP.
- Do not strip named-source citations. Stripping is for internal vocabulary only.
- Do not overwrite an existing `day-N.md` in either output path. If one exists, stop and ask the user.
- Do not generate the PNG yourself. Produce the prompt; the user runs Nano Banana separately.
- Do not silently leave em-dashes in. Always run the post-write `grep -c "—"` and fix any hits before reporting completion.
- Do not let the word count creep above 90 percent of the SITREP. The transform should compress.
- Do not default the cover to the same strait-and-slate composition as the prior post. The durable thread is allegory and painterly finish; everything else rotates. If you find yourself writing "rocky strait" and "slate-blue" for a third consecutive cycle without a strong analytical reason, stop and pick a different setting or palette.
