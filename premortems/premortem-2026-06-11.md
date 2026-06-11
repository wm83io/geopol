# Iran 2026 Framework Pre-Mortem — 2026-06-11 (Day 105)

Second diagnostic under the formal cadence. 15 days since the Day 90 pre-mortem (past the 14-day floor); manually invoked; triggered also by the v4.3 minor increment, the T9 disc-ratio 4:10 drift event, and two inputs routed here by the Day 105 /audit. 30-day window: Day 90 (sweep-2026-05-27) → Day 105 (sweep-2026-06-11); 8 SITREPs (day-90 → day-105), 8 sweeps. Synthesis anchor: v4.3.

Six-month-forward frame: it is December 2026. The 30-day and 6/12-month projections from the Day 90-105 window were materially wrong. What is the most likely cause?

---

## Mitigation manifest

| # | Failure mode | Routing | File to patch | Status |
|---|---|---|---|---|
| 1 | T9 disc-ratio breach reviewed but falsification bar is unreachable by events that actually occur | reference-patch | `reference/strategic-trends.md` (T9 reachable CONTESTED trigger) | **approved 2026-06-11; executed** |
| 2 | Fork A/C convergence absorbed as range width instead of forcing a fork re-cut | slash-command-patch | `.claude/commands/sitrep.md` (overlap-forces-recut probability rule) | **approved 2026-06-11; executed** |
| 3 | 6/12m structural prior frozen through a sustained within-state regime shift (gate mis-specified) | slash-command-patch | `.claude/commands/revise.md` (sustained-within-state-advance secondary gate) + next /revise refresh | **approved 2026-06-11; executed** |
| 4 | Provisional-principal demotion (A4/A2) becomes a new holding state with no per-cycle forcing | slash-command-patch | `.claude/commands/sweep.md` Step 7b (forcing question through the 6-cycle provisional window) | **approved 2026-06-11; executed** |
| 5 | Reconstitution "3+ clusters" is multi-metric, single-ecosystem; analytical/commercial laundering | reference-patch | `reference/quality-sources.md` (analytical-ecosystem + metric-heterogeneity independence) | **approved 2026-06-11; executed** |

Failure 6 (escalation-side watchlist coverage gap) is already routed by the Day 105 /audit to a `/sitrep` watchlist-construction directive; this pre-mortem ratifies it, no new patch.

---

## Retrospective

**Prior pre-mortem (Day 90) scored.** All 5 mitigations were applied; 3 bound, 2 had no adverse test case; no no-traction escalations.

1. *A2/A4 wrong-principal lock-in* — mitigation **bound**: v4.3 demoted A2 and A4 to provisional exactly per the staged manifest (§3.5, §7). Failure `partial`: the lock-in was caught and corrected, but the apex identity remains unknown, so the underlying exposure persists (escalates to Failure 4 below).
2. *Replacement-attribution thinness* — **bound**: v4.3 §2a/§3.5 explicitly refused the IRGC-council replacement the halo confidence it had not earned and demoted it. Failure `did-not-occur` (prevented). This is the cleanest bind of the five.
3. *Reading-swing trend rigidity* — applied; **no test case** arose (T1 logged no second swing Days 90-105). Counter is in place, untested.
4. *Fork D' decomposition unstaged* — applied; **no test case**: Fork D' collapsed to 12-20% rather than sustaining >30%, so the decomposition never fired; v4.3 §8.1a nonetheless retains the pre-staged D'-i..v variants. The rushed-decomposition failure was averted by the collapse, not by the rule binding.
5. *6/12m frozen without reasoning* — **bound**: v4.3 §8.1b carries explicit per-transition / held-prior reasoning. The reasoning-gap closed; it exposed the deeper gate problem (Failure 3 below).

**Ledger lookback (rows resolved since Day 90).** Matrix-followed: **14/14 scoreable, zero `n`** — no discipline breaches; the process layer is clean. Surprises: S5 (Iran-Israel direct axis, Day 101-102) is the only post-Day-90 surprise, and it maps to the coverage gap (Failure 6). Instrumentation: P90-04a resolved-late (gap closed before second escalation); P87-03 at first expiry, watch for a second. Signal quality: the standing signals are binary-resolvable (US KIA; new operation name; Brent >$100 close); no vague-signal Goodhart surface detected. Coverage 15/20, with all 5 misses escalation-side — the one persistent weakness.

---

## Failure-mode finding cards

### Failure 1: T9 is unfalsifiable by reachable events

**Likelihood:** medium

**What happened.** By December the framework's projection that the executive war-powers path is durable (T9 VALIDATED) failed: a Federal court accepted WPA standing, or a veto-override coalition formed, and the framework had spent months treating every contradicting cycle as subordinate to a falsification bar (both chambers + veto-override) that no realistic sequence reaches. The disc-ratio hit 4:10, was routed here, and was resolved "not demoted" on the strength of the Day 102 on-merits Senate failure.

**Root cause.** The disc-ratio rule routes a breach to /premortem; /premortem is the body that decides; if it ratifies "not demoted," it has self-certified the trend. The current reading (executive path held at the on-merits vote) is correct, but T9's falsification bar is set so high (bicameral passage + veto-override) that the evidence classes that actually occur — single-chamber passage, court filings, near-passages — can never demote it. Multi-cycle confirmation plus an unreachable falsification bar is the metastasis: discipline becomes immunity.

**Evidence in current outputs.** `strategic-trends.md` T9 now reads "4:10 (>1:3); /premortem"; v4.3 §2b T9 "Advance." The House passed 215-208 (Day 97), the deepest WPA challenge of the conflict, and it moved the trend state not at all. The disc-ratio breach is real and the trend absorbed it without a state change.

**Mitigation.** Do NOT re-demote (the on-merits failure is genuine supporting evidence). Add a *reachable* intermediate CONTESTED trigger to T9: a Federal court **granting** standing or certiorari (not merely a filing), OR a second on-merits single-chamber passage, moves T9 VALIDATED → CONTESTED even short of full falsification. This makes the trend falsifiable by events in the plausible set and converts the disc-ratio breach into a live, testable threshold rather than a self-certified hold.

**Routing.** `reference-patch`.

---

### Failure 2: Fork A/C convergence absorbed as width instead of a re-cut

**Likelihood:** medium-high (incipient, this cycle)

**What happened.** By December the communicated risk picture had been dominated for months by an undifferentiated "escalation" band because, once PROBE-7's discriminator collapsed and Fork A and Fork C converged, the framework widened Fork C toward Fork A rather than re-drawing the boundary. The 30d matrix carried two overlapping primitives whose sum (the KEC, 57-81% and climbing) became the de-facto headline the footnote rule was built to prevent.

**Root cause.** The range-width rule says "wider = undecomposed (split) or hedge (tighten)." v4.3 widened Fork C to 12pp citing "genuinely elevated evidence dispersion" from the Fork A/C convergence. But a declared overlap between two primitives is the textbook case for re-cutting the fork boundary (a named convergence cell), not widening one fork toward the other. The width is absorbing an undecomposed overlap.

**Evidence in current outputs.** v4.3 §8.1a range-width note: "Fork C and Fork A are partially overlapping and the cascade-vs-resumption boundary is less resolvable this cycle." day-105 KEC 57-81% (24pp), "up from 50-68%." The PROBE-7 recalibration I just wrote (two-axis nominal/operational with a "pressure-while-talking" convergence register) is the operational fix; the probability layer has no matching primitive.

**Mitigation.** Patch `sitrep.md` probability discipline: when two primitives are declared partially-overlapping or their boundary "less resolvable," the cycle must either re-cut the forks at the new operational reality OR report a named joint cell (e.g., "Fork A/C convergence, X-Y%"), not widen one primitive toward the other. Mirror the PROBE-7 two-axis register in the matrix.

**Routing.** `slash-command-patch`.

---

### Failure 3: 6/12-month prior frozen through a sustained regime shift

**Likelihood:** high (incipient; explicitly flagged in v4.3)

**What happened.** By December the 6/12m projections were materially wrong: the Day 90-105 escalation persisted and became structural (30d Fork D' 12-20%, Fork C 35-47%), but the 6/12m matrix held the v4.1 (Day 84) numbers for months (6m Fork C 16-22%; 12m Fork D' 12-18%) because no trend-state transition ever "enacted" the update gate. T2/T8/T12 advanced every single cycle — within state — and a sustained within-state advance does not trip the gate.

**Root cause.** The two-matrix discipline (insulate long horizons from cycle noise) is correct, but its update gate is "trend-state transition" only. A multi-cycle regime shift can occur entirely through VALIDATED trends advancing within state, so the structural prior never updates despite a real structural change. Insulation metastasizes into staleness.

**Evidence in current outputs.** v4.3 §8.1b: "the 6/12m matrix is materially lagging the operational picture... by design under the two-matrix cadence" — and the Day 105 /audit did not update it (audit does not own the structural prior; /revise does). The gap (30d Fork C 35-47% vs 6m 16-22%) is now ~2x.

**Mitigation.** Patch `revise.md`: add a secondary 6/12m update gate — **N consecutive cycles (set N=4) of same-direction within-state advance** on the trends anchoring a fork forces a structural-prior re-evaluation at the next /revise, even absent a formal state transition. Flag the immediate next /revise to refresh the stale prior (T2/T8/T12 have advanced 8/8 cycles; the gate would already be tripped).

**Routing.** `slash-command-patch`.

---

### Failure 4: Provisional demotion becomes the new holding state (apex was Aerospace, autonomous)

**Likelihood:** high (incipient)

**What happened.** By December the escalation-control reading had failed: the GCC-axis and Hormuz decisions were taken by IRGC Aerospace Force command under delegated rules of engagement, not by a deliberating apex. The framework had demoted A4 to "principal-uncertain provisional within a candidate set" and then parked it there — the Day 90 pre-mortem's "flag became a holding state" failure recurred one layer down as "provisional became a holding state," with a 6-cycle-to-opaque clock but no per-cycle forcing of the discriminating evidence.

**Root cause.** The principal-validation discipline now has three states (validated / provisional / inherited-or-opaque). The Day 90 sweep Step 7b patch forces a discriminating-evidence question *at the 5th-cycle flag*; it does not carry that forcing through the *post-demotion provisional window*. Demotion resolved the flag-as-holding problem by creating a provisional-as-holding problem.

**Evidence in current outputs.** v4.3 §1.2: "no discriminating evidence on whether the apex approved GCC-axis expansion or Aerospace acted under delegated ROE (material for escalation-control reading)." The escalation-control reading is load-bearing — whether a US-KIA-triggering strike is apex-intended or agent-autonomous changes the Fork A entry probability — and rests on an unresolved principal with a clock but no forcing.

**Mitigation.** Patch `sweep.md` Step 7b: extend the discriminating-evidence forcing question through the entire 6-cycle provisional window, not just at the 5th-cycle flag. Name the GCC-axis discriminator explicitly: apex public claim/ownership of the GCC strikes (apex-directed) vs apex silence with Aerospace-only attribution (delegated-ROE). Each provisional cycle must state what would resolve the candidate set this cycle.

**Routing.** `slash-command-patch`.

---

### Failure 5: Reconstitution "3+ clusters" was multi-metric, single-ecosystem

**Likelihood:** medium

**What happened.** By December the T12 strong-reinforcement and the BS-13 +5pp upgrade proved overstated: the Day 105 "3+ independent clusters" (ISW 70% missile retention; IISS 90% underground storage; 30/33 Hormuz sites; Kpler solid-fuel imports) shared an ecosystem (ISW and IISS both drawing on the same US-IC briefing) and mixed metrics that measure different things (a commercial AIS flow does not corroborate a missile-inventory percentage). The framework had treated heterogeneous metrics as independent confirmations of one claim.

**Root cause.** The source-independence discipline fires on *anonymous-source* cluster-laundering. It has no rule for *analytical-ecosystem* laundering (think tanks co-drawing on one classified briefing or each other's priors) or *metric-heterogeneity* laundering (four different measurements presented as four confirmations of a single proposition). The through-use demonstration is the real evidence; the multi-metric stack inflates apparent confirmation.

**Evidence in current outputs.** v4.3 §2b T12 row: "3+ independent clusters Day 105 (ISW 70% missile retention; IISS 90% underground storage; 30/33 Hormuz sites; Kpler solid-fuel imports)." These confirm four different things; none independently corroborates another's claim.

**Mitigation.** Patch `quality-sources.md` Source-Independence Discipline: add that (a) analytical outfits that routinely co-draw on the same IC ecosystem (ISW/IISS/FDD) count as one cluster absent distinct sourcing, and (b) heterogeneous metrics are not multiple confirmations of a single claim; "N independent clusters" requires N sources confirming the *same* proposition through *distinct* sourcing. Operational demonstration (through-use) is the strongest evidence and should be cited as such, not padded with metric-stacking.

**Routing.** `reference-patch`.

---

### Failure 6: Watchlists under-instrument adversary option-generation

**Likelihood:** high (evidence-based; 5/5 surprises escalation-side)

**What happened.** By December the framework had been repeatedly surprised on the escalation side: the 5-surprise pattern (Hormuz toll, Lebanon clause, Iran-Israel direct axis, US-side initiation, GCC-base axis) extended into further new vectors (e.g., a Stage-3 cyber event, a Bab-el-Mandeb second chokepoint, a third-country tanker war) that no revision-signal watchlist carried.

**Root cause.** The "Signals That Force Immediate Revision" list is built by asking "what resolves the current forks" (resolution-side discriminators: LOI-acceptance variants appear on every list) rather than "what new option could an adversary generate." Resolution-side framing is a structural blind spot in watchlist construction.

**Evidence in current outputs.** Ledger Surprise register: 5 surprises, all escalation-side, 3 new-vector classes; coverage 15/20. Routed by the Day 105 /audit to a `/sitrep` watchlist-construction directive.

**Mitigation.** Already routed by the /audit: every revision-signal list must carry at least one adversary-new-vector branch (a novel escalation modality not yet observed), not only resolution-side discriminators. This pre-mortem ratifies; no new patch.

**Routing.** `none-recommended` (audit-routed; ratified).

---

## Defensive-rule metastasis check

| Rule | Failure-it-prevents | Current metastasis state |
|---|---|---|
| Multi-cycle confirmation + symmetric demotion | Recency bias / commitment bias | **Metastasizing at the falsification bar** (Failure 1): T9's demotion bar is unreachable by the events that occur, so the disc-ratio breach self-certifies. The reading-swing counter (Day 90 fix) is in place and untested. |
| Source independence / cluster-laundering | Multi-outlet single-cluster pickup as multi-source | **Metastasizing at the analytical/metric layer** (Failure 5): the anonymous-source rule is sound; analytical-ecosystem co-drawing and metric-heterogeneity stacking are unguarded laundering surfaces. |
| Principal-validation (provisional demotion) | Wrong-principal lock-in | **Working at the flag layer; new holding state at the provisional layer** (Failure 4): the Day 90 fix converted "flag-as-holding" into demotion; demotion created "provisional-as-holding" with a clock but no per-cycle forcing. |
| Range-only (15pp cap, None-of-above) | Composite degeneracy, false precision | **Metastasizing into width-as-hedge** (Failure 2): a declared primitive overlap is absorbed as Fork C width rather than forcing a re-cut; the KEC footnote (24pp) drifts toward de-facto headline. |
| Two-matrix cadence (30d vs 6/12m) | Cycle noise miscalibrating long horizons | **Metastasizing into staleness** (Failure 3): the transition-only update gate misses sustained within-state advances that compound into a structural shift; the prior freezes through a regime change. |

The pattern this cycle is one layer deeper than Day 90's. Day 90: rules flag correctly, action stalls. Day 105: the Day 90 action-routing fixes bound, and the **defensive rules' own thresholds are now the failure surface** — the falsification bar (T1/F1), the independence definition (F5), the demotion endpoint (F4), the width-vs-split choice (F2), and the update gate (F3) are each calibrated so the rule cannot catch the failure it was built for. The highest-leverage finding: every defensive rule needs a *reachability check* on its own trigger — can the event that should fire this rule actually occur in the plausible set? Four of five currently cannot.

---

## Closing note

Six failure modes, five mitigations, all routable inside the framework's own discipline. No new lens. The binding theme is **threshold reachability**: the framework's defensive rules are well-specified except at the exact point where their trigger is set beyond the reach of plausible events, converting discipline into immunity. Failure 3 (6/12m staleness) is the most urgent because it is already explicitly true and the next /revise is the gate; Failure 1 (T9 unfalsifiable) is the deepest because it is the disc-ratio rule reviewing itself and ratifying a hold. The process layer remains clean (14/14 matrix-followed, zero breaches); the weakness is entirely in calibration of the rules' own thresholds.

~2,380 words excluding tables.

*Compiled 2026-06-11 | Day 105 | next /premortem: monthly floor 2026-07-01 unless triggered earlier.*
