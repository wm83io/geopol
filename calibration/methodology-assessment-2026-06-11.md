# Methodology Assessment: Prediction Efficiency and Accuracy

*Day 105 (June 11, 2026). Scope: how the framework predicts principal behavior and SITREP outcomes; where cycle effort goes. Data: 19 sweeps (May 11 - June 8), 27 SITREPs (Days 62-102), command specs, reference apparatus, Day-90 premortem. Companion artifact: `calibration/prediction-ledger.md` (discipline spec + Days 84-102 backfill).*

---

## Verdict

The framework's process discipline is strong and its outcome discipline is absent. Every SITREP emits falsifiable predictions; nothing resolves them. Per the premortem's own standard, the fix is enforcement instrumentation, not new rules: the per-SITREP "Signals That Force Immediate Revision" lists are ready-made resolution criteria that were going unused. On the efficiency side, collection runs at flat cadence against fire-rate evidence that justifies tiering, and pre-flight re-reads ~2,500 lines per command against files that change by tens of lines per cycle.

Six findings, each now patched or routed. Backfill of Days 84-102 produced the first measured baseline.

---

## Findings

### F1. The prediction loop never closes (accuracy; primary)

Predictions are emitted in two layers and resolved in neither:

- **Signals layer.** Each SITREP terminates in 5-10 named observables with pre-committed matrix moves ("Araghchi T1 corroboration: Fork D' 21-29% → 24-33%"). No subsequent SITREP states whether they fired. Day-84's "Israeli unilateral strike 28-38% (14-21d)" window passed unscored; the carried Vahidi-direct HEU discriminator reached 12+ cycles open with no aging metric.
- **Fork layer.** 30d matrices update on new signal, never on outcome ("signal-triggered, not outcome-triggered"). No snapshot is ever scored at horizon expiry.

Consequences measured in backfill: of 20 major matrix movers in Days 84-102, **5 arrived from off-watchlist (surprise register S1-S5)**, all escalation-side, three of them new-vector classes (Hormuz toll, Lebanon clause, Iran-Israel direct axis). The watchlists over-index resolution-side discriminators (LOI-acceptance variants on every list) and under-index adversary option-generation. Nothing in the prior apparatus could see this pattern because nothing aggregated misses.

The good news the backfill also surfaced: **matrix-followed is 13/13** on scoreable fired signals. Two pre-committed moves were overridden with stated justification (T9 held VALIDATED through the House WPR passage; Fork A held through the Day-100 Gulf strikes), and both overrides were vindicated. The framework follows its own pre-commitments; it just never knew that.

**Fix (shipped).** `calibration/prediction-ledger.md` + mandatory Prediction Resolution sub-block in `/sitrep` Section 2 + month-end fork snapshots scored at expiry + surprise register. Misses route into Section 3 revision logic (outcome-triggered updating); expired-unresolved rows route to `/audit` as instrumentation failures.

### F2. Premortems are prospective-only (accuracy)

The Day-90 premortem diagnosed five failure modes and never looked back: no check whether the previous diagnosis occurred, no mitigation-traction measurement. Its own meta-finding ("good at noticing failure modes, weaker at routing the notice") applies to itself.

**Fix (shipped).** Mandatory Retrospective section in `/premortem`: score the prior premortem's failure modes (occurred / partial / did-not / unobservable), check mitigation traction, pull ledger misses and surprises since last run.

### F3. Zero-fire probes run at full cadence (efficiency)

Verified per-probe fire rates across all 19 sweeps (262 finding cards, 126 fired, 48%):

| Band | Probes (fired/runs) |
|---|---|
| High (≥60%) | PROBE-16 (15/17, 88%), PROBE-13 (15/19, 79%), PROBE-9 (14/19, 74%), PROBE-12' (13/19, 68%), PROBE-14 (11/18), PROBE-15 (11/18) |
| Mid (30-60%) | PROBE-8 (10/18), PROBE-20 (7/13), PROBE-10 (10/19), PROBE-7 (7/19), PROBE-2 (6/19) |
| Low (<30%, nonzero) | PROBE-1 (2/9), PROBE-3 (1/4 + 1 gap), PROBE-6 (3/18) |
| **Zero** | **PROBE-11 (0/5), PROBE-17 (0/11), PROBE-18 (0/5), PROBE-21 (0/11)** |

The four zero-fire probes consumed 32 of 262 probe-runs (12%) with no framework movement: roughly 96-160 web searches. PROBE-21 is the sharpest case: 11 partials, 0 fires, meaning its fire bar is either unreachable through the current source ladder or misdefined. PROBE-11 and PROBE-17 overlap (both Russia-internal; BS-9 structural sub-probes supersede routine probing; Russia path ≤5%). Correction of record: an earlier internal read had PROBE-1 and PROBE-3 at zero fires; the parsed counts show 2/9 and 1/4 (the Day-90 written-statement fire and the Day-97 provisional bazaar signal). Their cadence is an audit call, not a retirement case.

**Fix (shipped).** Tier model in `/sweep` (daily / event-triggered / monthly; auto-upshift on any fire or touching signal; downshifts audit-only; CRITICAL-BS probes never below event-tier; every probe runs at least monthly). Interim tiers: PROBE-11 → M, PROBE-17 → M, PROBE-18 → E, PROBE-21 → cadence unchanged + threshold-recalibration flag. `/audit` gains Step 5c (portfolio review on trailing fire rates, 25-directive ceiling).

### F4. Probe identity hygiene (accuracy + efficiency, minor)

The same probe appears in sweep JSONs as `PROBE-12'`, `PROBE-12-prime`, and `PROBE-12p`; PROBE-5 appears once. Any automated fire-rate computation silently fragments. Canonical-ID rule added to `/sweep`; normalization map goes to next `/audit`.

### F5. Stale cadence spec vs actual practice (efficiency)

`sweep.md` described a "weekly probe cycle" with a static frequency table (PROBE-1 through 8 "weekly") while actual practice is ~daily sweeps of 13-21 probes. The dead table neither constrained nor informed. Replaced by the tier model (F3).

### F6. Pre-flight re-reads full files that change marginally (efficiency)

Mandated reads per sweep: trends (269 lines) + synthesis (548) + appendix-b (1,120) + last SITREP (~256) + schemas (~300) ≈ 2,500 lines; `/sitrep` repeats most of it same-day plus 8-12 searches overlapping the sweep's 40-85. Appendix-b's state summary sits at the bottom of the file under 55+ lines of accreted audit-note chronicle at the top.

**Fix (shipped).** Diff-based pre-flight in `/sweep` and `/sitrep` (state tables + entries changed since last cycle, via git diff; full-read weekly floor retained per CLAUDE.md). SITREP search dedup: consume sweep finding cards, search only post-sweep developments and non-probe domains. Appendix-b restructure directive staged for next `/audit` (state header to top; chronicle below inventory; nothing deleted).

---

## Cycle cost, before and after

| Cost line | Before | After (steady-state) |
|---|---|---|
| Sweep probe-runs per cycle | 17-19 | ~13-14 (zero-fire tiers idle; monthly floor) |
| Web searches per cycle (sweep + SITREP) | 51-97 | ~40-70 (tiering + dedup) |
| Pre-flight line-reads per cycle (both commands) | ~5,300 | ~1,700-2,500 (diff-reads; floors retained) |
| New cost: ledger upkeep | 0 | ~5-10 rows logged + due rows resolved per SITREP |

Net: the accuracy instrumentation is paid for several times over by the collection and read savings.

## What was deliberately not changed

- No formal Bayesian machinery. Ranges remain constraint-space compressions; the ledger scores them honestly (in/out at expiry, midpoint Brier logged not interpreted below N=6) without pretending they are frequency claims.
- No new discount rules, trend states, or voice discipline; all existing layers (Step 7b principal validation, source-cluster provenance, disc-ratio, reading-swing) stand. The ledger feeds them data instead of duplicating them.
- No probe-schema contract changes. Sweep metadata extensions follow the `reference_trends` precedent.

## Follow-ups (routed, not executed here)

1. **Next `/audit`:** appendix-b header restructure; tier table written into Appendix B directives; PROBE-21 fire-bar redefinition; PROBE-11/17 consolidation under BS-9; probe-ID normalization map; second-expiry escalations from ledger (BS-9.3 April count, IEA Hormuz-resumption data).
2. **`/revise` to v4.3:** the staged `synthesis/staging/v4-3-principal-validation-manifest.md` (A2/A4 demotion) has been a fired trigger since May 27; consuming it also clears the two longest-open ledger discriminators into provisional status.
3. **First scored fork snapshot** lands July 1 (F95-30d expiry); first ledger-fed premortem due July 1 per monthly floor.
