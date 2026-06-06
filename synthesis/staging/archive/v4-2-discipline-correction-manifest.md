# v4.2 Discipline-Correction Manifest

**Staged:** 2026-05-22
**Origin:** /premortem-derived adversarial-review diagnostic against framework's 6-month projection failure modes
**Activation:** at next `/revise` invocation; not contingent on v4.1 activation but compatible with it
**Type:** discipline correction (methodology-layer adjustment to existing v4.0 thesis; not a thesis revision)

---

## Diagnostic basis

Pre-mortem assumed a 6-month-forward retrospective: "It is November 2026. The framework's projections from May 2026 were materially wrong. What is the most likely cause?" The diagnostic identified five recurring failure modes whose root causes traced to defensive discipline rules that had become failure surfaces:

1. **VALIDATED-trend lock-in producing commitment bias.** The multi-cycle-confirmation rule, originally one-directional (promotion required 2+ cycles; demotion implicitly required more), allowed VALIDATED trends to absorb contradicting evidence as "single-cycle noise" indefinitely.
2. **Source-cluster collapse masquerading as multi-source confidence.** Multi-outlet T2 pickup of the same originating reporter or anonymous-source cluster was being treated as independent confirmation. The Day 84 Mojtaba HEU directive (5 outlets, 1 cluster) was the canonical near-miss.
3. **Wrong principal identification.** Named principals (Mojtaba, Trump A1, Netanyahu, etc.) were inherited from media framing without independent validation. The "actors as subjects of choice verbs" voice discipline made this more dangerous, not less: the model committed to the named agent.
4. **Probability-band erosion and composite degeneracy.** Fork D' grew toward residual-catch-all status; KEC became the analytical object rather than a derived headline; ranges crept wider as hedging.
5. **Crisis cadence producing false confidence on 6-month projections.** Daily SITREP rhythm sharpened short-horizon resolution and degraded long-horizon resolution; 12-month numbers were largely extrapolations of 30-day positions with arbitrary widening factors.

The cross-cutting pattern: every defensive discipline rule (multi-cycle confirmation; source tiering; voice discipline; range-only probability; substrate-as-agent prohibition) eventually metastasizes into the failure it was designed to prevent.

---

## Synthesis-level changes (consumed at next /revise)

### S1. Probability matrix architecture (Section 5)

The v4.0 probability matrix collapses into a single table with 30-day and 12-month columns updated together every SITREP. v4.2 splits this into two matrices on separate cadences:

- **Matrix 5a (30-day):** cycle-Bayesian; updates every SITREP.
- **Matrix 5b (6/12-month):** structural-prior-driven; updates only on trend-state transitions, constraint-layer shifts, or synthesis major-version increments.

**Rationale:** cycle-level Bayesian updates over correlated signal clusters produce sharp short-term estimates and miscalibrated long-term ones. The single-matrix architecture created an illusion of long-horizon precision driven by short-horizon noise.

**Synthesis Section 5 must be re-architected** to present both matrices, label each cadence explicitly, and carry a "last structural update" date on Matrix 5b.

### S2. Range-width cap and "None of the above" row

All probability matrices in the synthesis carry:

- **Hard cap on range widths:** 15 percentage points maximum. Wider ranges either undecompose (split the row) or hedge (tighten).
- **Mandatory "None of the above" row:** non-zero floor (5-10% on 30-day; 10-15% on 6/12-month). The named forks do not span the outcome space; this enforces acknowledgment of the gap.

**Synthesis Section 5 matrix layout must be updated** to include the None-of-above row across all probability scenarios.

### S3. Kinetic Escalation Composite demotion

KEC moves from Executive Summary headline to Section-5 footnote. The composite was becoming the analytical object — referenced in operative judgment, used as a comparable across cycles, sometimes substituting for primitive analysis. v4.2 enforces:

- KEC appears only in Section 5 as a footnote with construction formula and an explicit `[DERIVED]` label.
- Executive Summaries lead with two primitives (escalation-leading + non-escalation-leading) and the None-of-above floor.
- Analytical text in Sections 3, 4, and 7 references primitives, not the composite.

### S4. Fork D' decomposition rule

If Fork D' exceeds 30% on the 30-day matrix sustained over 4+ cycles, decompose at the next SITREP. "Deferral" is not an analytical primitive at that probability mass; the question becomes "deferred how, by whom, for how long, with what mechanism." Each named variant takes its own row.

**Synthesis Section 5 must establish the decomposition rule** and provide the template structure for decomposed Fork D' variants.

### S5. Trend-state symmetry and decay clause

The synthesis's reference-layer description (in CLAUDE.md and `reference/strategic-trends.md`, already patched in the v4.2 working set) is updated to:

- Symmetric demotion: 2+ cycles of contradicting evidence transitions VALIDATED → CONTESTED.
- 30-day decay clause: VALIDATED trends with no re-verifying signal auto-demote at the next /audit or /sweep Calibration Check.
- Evidence asymmetry log per trend.

**Synthesis methodology section (or Appendix C cross-reference)** should note the trend-state symmetry rule as a v4.2 methodology correction.

### S6. Source-independence (provenance) discipline

The synthesis's source-quality treatment is updated to distinguish outlet quality from source independence. Multi-outlet pickup of the same originating reporter or anonymous cluster is not multi-source; the -50% anonymous-source discount applies to the originating cluster regardless of outlet count.

**Synthesis Source Quality section** should briefly cross-reference `reference/quality-sources.md` Source-Independence Discipline.

### S7. Principal-validation alternative-hypothesis discipline

The synthesis's principal-identification commitments (Mojtaba as apex; Trump A1; Netanyahu Penetration mechanism; etc.) carry an explicit acknowledgment that principal identification is provisional and re-validated cycle-by-cycle via discriminating evidence. Where discriminating evidence has been absent for 4+ cycles, the principal commitment is flagged as `inherited, not validated`.

**Synthesis principal sections** should add the alternative-principal hypothesis as a structural caveat, not as a footnote.

---

## Reference-layer changes (already applied in working set; v4.2 absorbs)

- `reference/strategic-trends.md`: Trend State Transition Symmetry section; decay clause; evidence asymmetry log requirement. Already patched 2026-05-22.
- `reference/quality-sources.md`: Source-Independence Discipline section. Already patched 2026-05-22.

These do not require synthesis-level absorption beyond cross-reference; they are reference-layer authoritative.

---

## Operational-layer changes (already applied in working set; v4.2 notes)

- `.claude/commands/sweep.md`: Step 3b (provenance trace); Step 7b (principal-validation cross-check). Already patched 2026-05-22.
- `.claude/commands/sitrep.md`: Section 5 dual-matrix structure; 15pp cap; None-of-above row; KEC demotion. Already patched 2026-05-22.
- `.claude/commands/premortem.md`: new monthly adversarial-review command. Already created 2026-05-22.
- `CLAUDE.md`: probability discipline section updated; new anti-patterns; /premortem in command table and daily cadence; v4.2 added to framework version history. Already patched 2026-05-22.

These operational changes are live; v4.2 ratifies them in the synthesis version-history and methodology narrative.

---

## What this manifest is NOT

- **Not a thesis revision.** The v4.0 central thesis (Iran 2026 as trigger event accelerating tripolar reordering; materialist bargaining model with Bayesian updates) holds. v4.2 corrects the discipline architecture under which the thesis is operationalized.
- **Not a reaction to a specific projection failure.** The diagnostic is a pre-mortem (forward adversarial review), not a post-mortem on an observed failure. The mitigations target failure surfaces before they produce catastrophic mis-projection.
- **Not a re-architecture of constraint layers.** L1-L5 (military physics, asymmetric-conflict logic, time arithmetic, faction misalignment, PA-gap) are unchanged.
- **Not a new probe inventory.** Appendix B blind-spots are unchanged; only the probe procedure is updated (provenance trace, principal-validation step).

---

## Activation procedure at next /revise

1. **Read this manifest first.** Carry forward S1-S7 into synthesis section structure.
2. **Verify reference-layer patches.** Confirm `reference/strategic-trends.md` and `reference/quality-sources.md` carry the 2026-05-22 v4.2 working-set additions; cross-reference from synthesis methodology section.
3. **Verify operational-layer patches.** Confirm `.claude/commands/sweep.md`, `.claude/commands/sitrep.md`, `.claude/commands/premortem.md`, and `CLAUDE.md` carry the v4.2 working-set additions.
4. **Re-architect Section 5** per S1-S4 (dual matrix; 15pp cap; None-of-above row; KEC demotion; Fork D' decomposition rule).
5. **Update methodology section** per S5-S7 (cross-reference trend-state symmetry; cross-reference source-independence; principal-validation caveat in principal-attribution sections).
6. **Version-history entry:** confirm v4.2 entry in synthesis Version Notes with provenance to this manifest and to the /premortem diagnostic that originated it.
7. **Archive this manifest** to `synthesis/staging/archive/` via `git mv` after successful synthesis write.

---

## Sibling manifests at activation

- `v3-1-change-manifest.md` (Day 74; not yet activated)
- `v3-1-scope-expansion-manifest.md` (Day 76; not yet activated)
- `v3-2-russia-pole-revision-manifest.md` (2026-05-14 §9.3 patch; not yet activated)
- `v4-2-discipline-correction-manifest.md` (this; 2026-05-22)

v4.2 activates independently of v3.1 / v3.2 manifests but is compatible with concurrent activation. If activated concurrently with v3.1 / v3.2, the discipline-correction rules in v4.2 apply to the synthesis output structure regardless of the content changes from v3.1 / v3.2.

---

*End of v4.2 manifest. Consumed at next /revise; archive on successful synthesis write.*
