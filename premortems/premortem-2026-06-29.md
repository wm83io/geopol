# Iran 2026 Framework Pre-Mortem — 2026-06-29 (Day 123)

Third diagnostic under the formal cadence. 18 days since the Day 105 pre-mortem (past the 14-day floor); manually invoked; triggered also by the v4.5 minor increment (T9 VALIDATED → CONTESTED enacted, A2/A4 demoted) and the BS-7/BS-11 four-cycle Hormuz-sub-read oscillation routed here by the Day 123 sweep and SITREP. 30-day window: Day 102 (sweep-2026-06-08) → Day 123 (sweep-2026-06-29); SITREPs day-102 → day-123; sweeps June 8 → June 29. Synthesis anchor: v4.5.

Six-month-forward frame: it is December 2026. The 30-day and 6/12-month projections from the Day 102-123 window were materially wrong. What is the most likely cause?

---

## Mitigation manifest

| # | Failure mode | Routing | File to patch | Status |
|---|---|---|---|---|
| 1 | Probability primitive (Fork C) oscillates with the headline; no multi-cycle-confirmation analog at the fork layer | slash-command-patch | `.claude/commands/sitrep.md` (primitive-oscillation standing-floor rule) | **approved 2026-06-29; executed** |
| 2 | Structurally-opaque apex used as a positive causal variable (opaque-as-blackbox) | slash-command-patch | `.claude/commands/sweep.md` Step 7b (opaque ≠ explanatory node) | **approved 2026-06-29; executed** |
| 3 | 6/12m secondary gate is advance-only; misses stale-HIGH when anchoring trends stop advancing | slash-command-patch | `.claude/commands/revise.md` (symmetric within-state gate) | **approved 2026-06-29; executed** |
| 4 | VALIDATED-trend falsification conditions not reachability-audited (T2 0:n across ~40 cycles) | reference-patch | `reference/strategic-trends.md` (falsification-reachability audit) | **approved 2026-06-29; executed** |

Failure 3 (zero-US-KIA gate on single-ecosystem self-report) is `none-recommended`: the adjudication was correct and the discount discipline exists; noted for /audit, no patch.

---

## Retrospective

**Prior pre-mortem (Day 105) scored.** All 5 mitigations executed; 3 bound, 2 had no adverse test case. No no-traction escalations.

1. *T9 reachable-CONTESTED trigger* — **bound, the cleanest bind in the framework's history.** The Senate WPR 50-48 (June 23) fired reachable trigger (b); T9 demoted VALIDATED → CONTESTED at the Day-119 audit / v4.5. Failure 1 (T9 unfalsifiable) `did-not-occur`, prevented exactly as designed: the trend proved demotable on reachable evidence while the operational prediction held.
2. *Fork A/C overlap-forces-recut* — applied Day 123 (the A/C boundary was checked, found cleanly gated by the US-KIA / sustained-operation sub-conditions, and Fork C was re-cut 8pp → 10pp on live-exchange evidence rather than widened toward A). `did-not-occur`; no convergence-cell test case arose this window.
3. *6/12m secondary within-state gate (N=4)* — **bound**: forced the v4.4 re-base, then checked-and-held at v4.5 ("the secondary gate did NOT re-fire... priors carried"). The mitigation works; this pre-mortem's Failure 3 finds its advance-only asymmetry exposes a stale-HIGH gap (the recurrence pattern).
4. *Provisional forcing-question through the window* — **bound**: A4 → structurally-opaque and A2 → inherited at v4.5, on schedule at window close, not re-flagged. This pre-mortem's Failure 2 finds the demotion endpoint became the new holding state (the same recurrence, one layer deeper).
5. *Reconstitution ecosystem/metric independence* — applied; **no strong test case** (no T12 multi-cluster claim arose Days 109-123; mild application Day 123, declining to treat strike use-confirmation as a reconstitution-rate cluster).

**Ledger lookback (rows resolved since Day 105).** Matrix-followed: **21/21 scoreable, zero `n`** across the run; process layer clean. Surprises: **S6 only** (Day 119 Senate WPR, domestic-institutional vector); Day 123 logged **no** surprise (the kinetic exchange was pre-listed via P115-02 + the CENTCOM-strike branch, a coverage recovery). Instrumentation: no second-expiry; persistent weakness is Vahidi-direct HEU (12th absence) and the never-arrived apex-direct statement, both now retired into the A4 structurally-opaque demotion. Signal quality: standing signals are binary-resolvable (US KIA, warship firing, Brent close, Doha no-show, court standing); no vague-signal Goodhart surface, though P123-03 (MBS-MBZ split, "standing") is the softest current row.

---

## Failure-mode finding cards

### Failure 1: Fork C oscillates with the headline (no fork-layer recency check)

**Likelihood:** high (evidence-based; four consecutive cycles)

**What happened.** By December the communicated near-term risk picture had been whipsawed for months because Fork C tracked each cycle's loudest event rather than holding a structural floor. The framework cut Fork C on quiet weeks and spiked it on loud ones, and a reader following the 30d matrix saw a miscalibrated, mean-reverting band that under-warned before the incident that finally converted to Fork A and over-warned in the lull before it.

**Root cause.** Multi-cycle confirmation, symmetric demotion, the disc-ratio, and the reading-swing counter all discipline the *trend* layer against recency bias. There is no analog at the *probability-primitive* layer. A fork level can reverse direction every cycle on single-cycle evidence with no rule flagging it, because the SITREP re-cuts the 30d matrix every cycle by mandate.

**Evidence in current outputs.** The BS-7/BS-11 Hormuz sub-read reversed four consecutive cycles: D110 settled → D115 contested-leverage re-arm (Fork C 16-26) → D119 declaratory/de-arm (Fork C 14-22) → D123 live-exchange (Fork C 18-28). The Day-119 sweep flagged its own de-arm ("is the sub-read tracking each headline?"); Day 123 confirmed it. Both the Day-123 sweep and SITREP recommend a standing Fork-C floor; the recommendation has no rule to land in.

**Mitigation.**
- Patch `sitrep.md` probability discipline: when a primitive's level reverses direction on ≥3 of the last 5 cycles without a *structural* driver (constraint-layer shift or trend transition), the cycle must hold a stated standing floor for that primitive and name the floor explicitly, rather than re-zeroing or re-spiking on the latest operational headline. The floor is the persistent-live-surface base rate; single-cycle events move the band within the floor, not through it.
- Supplementary: log primitive-oscillation events to the sweep `calibration` block (the trend-layer reading-swing counter's fork-layer twin).

**Routing.** `slash-command-patch`.

---

### Failure 2: Structurally-opaque apex used as a causal variable (opaque-as-blackbox)

**Likelihood:** medium-high (incipient, this cycle)

**What happened.** By December the escalation-control reading had failed because the framework kept explaining Iranian behavior with a "diffuse council" it had explicitly declared illegible. Escalation was read as "the council brandishes," de-escalation as "the council controls the off-ramp," apex silence as "council opacity" — a node that explains everything and is contradicted by nothing. When the council read mattered most (was a US-KIA-triggering strike apex-intended or agent-autonomous?), the framework had a confident story resting on an attribution it had retired to structurally-opaque.

**Root cause.** The principal-validation discipline now demotes an unvalidated apex to "structurally-opaque / diffuse council that consents without a legible owner." That is the correct epistemic move, but the demotion endpoint is being used as a *positive* explanatory variable rather than as silence. The Day-90 "flag-as-holding" and Day-105 "provisional-as-holding" failures recur here as "opaque-as-blackbox": the resurrection condition (an authenticated apex-direct statement) may never arrive (Mojtaba unseen since Feb 28, 4+ months), so the opaque node is parked and quietly load-bearing.

**Evidence in current outputs.** Day-123 sweep PROBE-2/PROBE-1 and SITREP: "the rapid cease-and-resume-Doha agreement points to council-level control of the off-ramp"; "a diffuse council that consents to the deal while the military brandishes." Both escalation (base strikes) and de-escalation (off-ramp) this cycle were attributed to the same illegible council; the escalation-control reading is named load-bearing on Fork A entry while resting on it.

**Mitigation.**
- Patch `sweep.md` Step 7b: when a principal is `structurally-opaque`, the framework may not make the opaque node the subject of control/intent verbs ("the council controls/calibrates/consents"). Escalation-control reads must rest on *observable agent behavior* (IRGC attribution, claimed-vs-actual effect, timing) stated as such, with the apex node held as unknown. Adjacent to the substrate-as-agent prohibition (CLAUDE.md), extended to demoted-opaque principals.

**Routing.** `slash-command-patch` (cross-reference CLAUDE.md voice discipline).

---

### Failure 3: 6/12m secondary gate is advance-only (stale-HIGH blind spot)

**Likelihood:** medium (incipient)

**What happened.** By December the 6/12m Fork A composite (32-42% / 38-48%, set at v4.4 on "sustained T8/T12 advance") proved stale-high: T8 eased and T12 stopped advancing for months after v4.4, but the structural prior never re-evaluated because the secondary gate only fires on consecutive *advance*. The long-horizon Fork A number stayed elevated on a driver that had stopped driving.

**Root cause.** The Day-105 Mitigation 3 secondary gate (N=4 consecutive same-direction within-state advance → structural re-eval) is one-directional. It catches stale-LOW (drivers advancing within state while the prior is frozen low, the Day-105 case) but not stale-HIGH (drivers easing/holding while the prior stays elevated). Insulation-into-staleness metastasizes in the direction the gate does not watch.

**Evidence in current outputs.** 6/12m Fork A 32-42% / 38-48% last updated v4.4 (Day 109), driver "sustained T8/T12 advance." Across Days 110-123 T8 is logged "hold/easing" (pre-emption channeled to Lebanon, now a signed framework) and T12 "hold" (no fresh reconstitution cluster, 4+ cycles). The advance-only gate cannot fire on this pattern; the prior carries unexamined.

**Mitigation.**
- Patch `revise.md`: make the secondary gate symmetric. N consecutive cycles of same-direction within-state *movement* on a fork's anchoring trends, advance OR ease, forces a structural-prior re-evaluation at the next /revise. The next /revise should re-examine the 6/12m Fork A prior against T8-easing / T12-holding.

**Routing.** `slash-command-patch`.

---

### Failure 4: VALIDATED-trend falsification conditions not reachability-audited (T2)

**Likelihood:** medium

**What happened.** By December T2 (multi-channel deterrent, VALIDATED, 0:n disc-ratio across ~40 cycles) proved a commitment dressed as robustness: every Iranian escalation that did not collapse a proxy channel was scored "T2 advance / calibrated below maximum," so the trend advanced monotonically regardless of escalation magnitude, and the confidence it lent the multi-channel-deterrent-holds thesis was never tested because its falsification conditions (Houthi mass-launch, Hezbollah resumption, PMU collapse) are all channel-collapse events that the actual escalation path never produces.

**Root cause.** The Day-105 closing named threshold-reachability as the binding theme and applied it to T9. The lesson was not generalized: no rule audits whether a VALIDATED trend's *falsification* conditions are reachable by the plausible event set. A 0:n disc-ratio across ~40 cycles is either genuine robustness or an unfalsifiable read, and the framework has no procedure to distinguish them.

**Evidence in current outputs.** Day-123 read the sharpest Iranian escalation of the conflict (coordinated ballistic+drone strikes on US bases in two Gulf states) as "T2 advance, calibrated below maximum." `strategic-trends.md` T2 disc-ratio 0:n; falsification conditions are all channel-collapse. Five VALIDATED trends (T1/T2/T4/T8/T12) carry a formal "last review" of 2026-05-25 (35 days stale), operationally re-verified each sweep but never formally re-dated.

**Mitigation.**
- Patch `strategic-trends.md`: add a falsification-reachability audit to the trend-state discipline (generalizing the T9 reachable-trigger lesson). At each /audit, any VALIDATED trend with disc-ratio 0:n across 12+ cycles must have its falsification conditions checked for reachability by the plausible event set; unreachable conditions get a reachable intermediate CONTESTED trigger, as T9 did. Bump the formal review dates when the substance is cross-checked.

**Routing.** `reference-patch` (requires analyst approval per CLAUDE.md reference-edit restriction).

---

### Failure 5 (source-cluster, none-recommended): zero-US-KIA gate on single-ecosystem self-report

**Likelihood:** low-medium

**What happened / root cause.** The cycle's most load-bearing fact, zero US KIA from the IRGC base strikes (the Fork A vs Fork C discriminator), rests on US-government self-report (CENTCOM + a US official to Reuters) during an active information war, with the IRGC asserting the opposite ("eight bases destroyed"). The framework adjudicated toward zero-damage, defensibly (Iranian battle-damage claims routinely inflate), but a *gate* fact resting on one interested ecosystem is a thinner base than a probability *input*.

**Evidence in current outputs.** Day-123 sweep PROBE-2/PROBE-7: "CENTCOM/US official (Reuters): zero damage, zero casualties"; IRGC claim discounted as posture. The adjudication is correct; the structural point is that the Fork-gate, not just a band input, turned on it.

**Mitigation.** None-recommended. The discount discipline and conflict-adjudication rules already exist and were applied. Noted for /audit: load-bearing Fork-gate facts resting on single-ecosystem self-report during info-war should carry an explicit "confirm independently next cycle" tag, not a new rule.

**Routing.** `none-recommended`.

---

## Defensive-rule metastasis check

| Rule | Failure-it-prevents | Current metastasis state |
|---|---|---|
| Multi-cycle confirmation / reading-swing counter | Recency bias (trend layer) | **No analog at the fork layer** (F1): Fork C oscillates four cycles with the headline; the recency discipline stops at the trend boundary. |
| Source independence / cluster-laundering | Multi-outlet single-cluster as multi-source | **Working** (F5 none-recommended): adjudication correct this cycle; residual exposure is gate-facts on interested self-report, noted not patched. |
| Principal-validation (provisional → opaque demotion) | Wrong-principal lock-in | **Demotion endpoint became a blackbox** (F2): opaque is being used as a causal variable rather than as silence; Day-90/105 holding-state recurrence, one layer deeper. |
| Range-only (15pp cap, None-of-above) | Composite degeneracy, false precision | **Working at the width layer; failing at the level layer** (F1): Fork C width stayed disciplined (10pp, driver stated) but its *level* tracks headlines unchecked. |
| Two-matrix cadence + secondary gate | Cycle noise miscalibrating long horizons | **Advance-only asymmetry** (F3): the gate catches stale-low, not stale-high; the prior can freeze elevated when drivers stop advancing. |

The recurrence pattern from Day 90 (flag-as-holding) → Day 105 (provisional-as-holding, threshold-unreachability) extends this cycle: every Day-105 mitigation bound, and the **same failure re-emerged one layer deeper** (opaque-as-holding F2; the gate's asymmetric reachability F3; the recency rule's missing fork-layer analog F1; the falsification-reachability not generalized F4). The binding theme is now **reachability + symmetry + layer-recursion**: a defensive rule's trigger must be reachable by plausible events (F4), must watch both directions (F3), and must be replicated at every layer the failure can occur (F1 fork layer, F2 demotion endpoint). The process layer remains clean (21/21 matrix-followed, zero breaches); the weakness is entirely in the rules' own thresholds and scope.

---

## Closing note

Four routable mitigations plus one noted exposure. No new lens. The most urgent is Failure 1 (Fork C headline-tracking), because it is already four cycles deep and degrades the framework's primary communicated output, the 30d primitive bands. The deepest is Failure 2 (opaque-as-blackbox), because the apex may stay structurally-opaque indefinitely and the framework is quietly drawing causal inferences from a node it declared illegible. Failures 3 and 4 are the Day-105 threshold-reachability theme generalizing: the secondary gate needs symmetry, and the falsification-reachability check that fixed T9 needs to cover every VALIDATED trend. The framework is good at building the right rule and calibrating its trigger one layer too narrow; the pre-mortem's standing job is to find next layer.

~2,290 words excluding tables.

*Compiled 2026-06-29 | Day 123 | next /premortem: monthly floor 2026-07-01 (2 days out; this run satisfies it unless a trigger intervenes).*
