# Prediction Ledger - Iran 2026 Framework

*Created Day 105 (June 11, 2026). Backfilled Days 84-102. Maintained by `/sitrep` (resolution sub-block, Section 2) and consumed by `/audit` (Source C miscall input, portfolio stats) and `/premortem` (retrospective).*

---

## Discipline

**What gets logged.** Three row types:

1. **signal**: every entry in a SITREP's "Signals That Force Immediate Revision" list. Logged with the pre-committed matrix move stated in the list. A signal re-listed in later SITREPs is ONE row; `carried-to` advances. Reformulated signals close the old row (`superseded`) and open a new one.
2. **fork**: a 30d matrix snapshot, logged from the first SITREP of each calendar month and at synthesis version increments. Scored at 30d expiry (non-overlapping samples). Explicit sub-horizon forecasts (e.g. "Israeli pre-emption 32-45% / 14-21d") are logged as fork rows with their own windows.
3. **surprise**: an event that forced a material matrix or trend move but appeared on no prior watchlist. Logged at resolution time only. Surprises are the watchlist's false negatives.

**Resolution vocabulary.** `open` | `fired` (condition occurred; matrix-followed noted) | `fired-partial` (occurred in weaker form than stated) | `did-not-fire` (window or carry closed without event; a non-event, not a miss) | `expired-unresolved` (could not determine; instrumentation failure, feeds audit gap log) | `superseded` (reformulated or made moot).

**Matrix-followed** (fired rows only): `y` (pre-committed move applied or explicitly justified-held next SITREP) | `partial` | `n` (move neither applied nor justified; discipline breach, cite in premortem) | `n.a.` (no move was pre-committed).

**Scoring rules.**
- Signals: report counts. Coverage ratio = fired signals / (fired signals + surprises). Matrix-followed rate = (y + partial) / fired. No percentage claims below N=20 resolved signals; counts only.
- Forks: at snapshot expiry, mark realized outcome per row (in-range / above / below) and compute multi-class midpoint Brier across the fork set. Log, do not interpret, below 6 scored snapshots.
- Expired-unresolved rows are an instrumentation metric, not forecast misses. 2+ consecutive expirations on the same signal: escalate to `/audit` (source-ladder failure).

**What this ledger does not claim.** Fork ranges are constraint-space compressions, not frequency claims; small-N Brier numbers are logged for trend detection across months, not as calibration verdicts. The signal layer (binary, short-window, high-N) is the primary accuracy instrument; the fork layer is secondary.

---

## Scorecard (backfill Days 84-102, as of Day 105)

| Metric | Count |
|---|---|
| Signal rows logged | 41 |
| Resolved fired (full + partial) | 12 (8 full, 4 partial) |
| Resolved did-not-fire | 14 |
| Expired-unresolved | 2 |
| Superseded | 1 |
| Open (carried into Day 103+) | 12 |
| Surprises (unlisted major movers) | 5 |
| **Watchlist coverage** | **12 / 17 major movers pre-listed (~71%; N below interpretation floor)** |
| **Matrix-followed** | **y: 7, partial: 3, n.a.: 2, n: 0 (10/10 scoreable followed)** |
| Fork snapshots logged | 2 (both pending expiry) |
| Fork snapshots scored | 0 |

Reading (provisional, small N): process discipline is strong (no fired signal saw its pre-committed move silently ignored); the weak edge is **coverage** (1 in 3 major movers arrived unlisted, all on kinetic/spoiler vectors, none on diplomatic vectors) and **instrumentation persistence** (BS-9.3 Putin count and the Vahidi-direct HEU discriminator carried 12+ cycles unresolved).

---

## Surprise register (Days 84-102)

| # | Day | Event | Matrix effect | Why unlisted |
|---|---|---|---|---|
| S1 | 85 | Iran-Oman permanent Hormuz toll (second LOI collision) | Fork B-bilateral 10-16 → 8-14; Fork D' 25-33 → 22-30 | Watchlist tracked HEU collision only; no second-collision class |
| S2 | 88 | Lebanon clause enters MOU as binding obstacle | Became dominant Fork D' blocker through Day 102 | Israeli spoiler tracked as kinetic, not diplomatic-clause vector |
| S3 | 88 | Abraham Accords "mandatory" demand (Trump) | Fork B-multilateral 13-20 → 11-18 | No Trump-initiated-demand class on any list |
| S4 | 90 | CENTCOM self-defense strikes inside Iran | Fork C 15-22 → 18-25 | US-side kinetic initiation absent from Day 88 list (Israel-side and IRGC-side were listed) |
| S5 | 101-102 | Iran ballistic missiles at Israel (new direct axis) | PROBE-16 fired; third accident surface; Fork C upper band | Day 100 list had IRGC-vs-US and Gulf-strike branches; no Iran-vs-Israel branch |

Pattern: all five surprises are escalation-side and three are new-vector classes (toll, clause, axis). The watchlists over-index on resolution-side discriminators (LOI acceptance variants appear on every list) and under-index on adversary option-generation. Routed to `/audit` Source C.

---

## Open predictions

| ID | Logged | Carried-to | Type | Claim | Pre-committed move | Resolve-by |
|---|---|---|---|---|---|---|
| P84-07 | 84 | 102 | signal | Vahidi direct named statement on HEU disposition | A4 HEU-axis resolved; synthesis revision candidate | standing; 12+ cycles open; v4-3 manifest staged Day 90 |
| P87-01 | 87 | 102 | signal | White House readout using "full dismantlement" / "all HEU removed" | Confirms Netanyahu Penetration relay at principal level | standing; A2 demotion staged in v4-3 manifest |
| P85-02 | 85 | 102 | signal | Israeli unilateral strike on Iranian nuclear/military site | Fork D' and Fork B collapse; mass into Fork A | standing tail-watch |
| P86-03 | 86 | 102 | signal | IDF air-refueling tempo / F-35-F-15 forward-positioning escalation | Israeli pre-emption rhetorical → operational; Variant B reprices toward 38-50% | standing; "rhetoric not operational" through D102 |
| P90-04 | 90 | 102 | signal | BS-9.3 fires (Putin <2 appearances/month, 3rd consecutive month) | Emergency synthesis review; M3 elevated | April count STILL unresolved; 2nd expiry = audit escalation |
| P93-01 | 93 | 102 | signal | Trump signs 60-day MOU / LOI | Fork D' activates; 60-day clock; A2 demoted | open; "near-signed" claimed Day 100, unsigned through D102 |
| P93-04 | 93 | 102 | signal | US KIA in any kinetic exchange | Fork C resolves into Fork A entry; deal track collapses; matrix resets | standing |
| P97-02 | 97 | 102 | signal | Tehran Grand Bazaar full closure confirmed T1/T2 | BS-1b activates; BS-15 Iran-side threshold breached | open; Day 97 provisional signal only |
| P100-09 | 100 | 102 | signal | Hezbollah accepts South Litani withdrawal framework | Lebanon triple-block partially resolves; Fork D' lower bound recovers toward 26-34% | open |
| P102-01 | 102 | - | signal | Araghchi T1 corroboration of Trump "near-signed" claim | Fork D' 21-29 → 24-33; LOI "impasse" → "near-signing"; synthesis revision candidate | next 1-2 SITREPs (stated 72h discriminator) |
| P102-02 | 102 | - | signal | Second Iran-Israel direct exchange without successful Trump halt | Fork C → 34-44; deal-direction breaking; synthesis revision required | next Lebanese provocation cycle |
| P102-03 | 102 | - | signal | Netanyahu coalition fracture (far-right resignation) | Caretaker accelerates; Lebanon clause → Zamir authority; Fork D' recovery conditional | open |
| P102-08 | 102 | - | signal | Iran hard exit from talks (SNSC or Araghchi T1 refusing Pakistan channel) | Fork D' collapses below 15%; synthesis revision required | open |
| P102-09 | 102 | - | signal | Saudi public support for US military action | BS-18 fractures; Fork A re-elevates; Fork B-multilateral collapses | standing |

(Standing rows P85-02, P86-03, P93-04, P97-02, P100-09, P102-09 subsume their verbatim re-listings on Day 102; resolve once, at event or at framework retirement of the signal.)

## Fork snapshots (pending expiry)

| ID | Logged | Snapshot | Expiry | Status |
|---|---|---|---|---|
| F95-30d | 95 (Jun 1) | Fork D' 22-30; Fork C 25-33; Fork A 18-28 (Israeli pre-emption 28-40 / 14-21d; Vahidi decap 5-12); Fork B-bi 8-13; Fork B-multi 8-12; none-of-above 5 | Jul 1 | pending |
| F102-30d | 102 (Jun 8) | Fork C 30-39; Fork D' 21-29; Fork A 18-28 (Israeli pre-emption 32-45 / 14-21d; Vahidi decap 5-12); Fork B-bi 7-12; Fork B-multi 8-12; none-of-above 5 | Jul 8 | pending |

Sub-horizon watch: Israeli pre-emption 14-21d windows from Days 84-102 all closed or close without a strike through Day 102; first full scoring at F95-30d expiry. Month-end snapshot cadence: next log = first SITREP of July.

---

## Resolved log (Days 84-102 backfill; newest resolution first)

| ID | Logged | Type | Claim (terse) | Resolved | Outcome | Evidence | Matrix-followed |
|---|---|---|---|---|---|---|---|
| P100-02 | 100 | signal | Senate WPR passes on-merits (Fetterman + 3+ GOP) | 102 | did-not-fire | Failed 47-53 June 8 | y: inverse branch applied; T9 VALIDATED confirmed, disc-ratio 4:10 held |
| P97-07 | 97 | signal | Senate schedules WPR on-merits vote | 102 | fired | Vote held June 8 (failed) | y: PROBE-10 fired H; T9 bicameral test complete |
| P95-02 | 95 | signal | Iran FM named acceptance of MOU resumption post-de-escalation | 102 | fired-partial | Exchanges resumed; "messages continue"; no named acceptance | partial: Fork D' lower bound firmed 20-28 → 21-29 |
| P84-08 | 84 | signal | Senate on-merits WPR result; Fetterman position | 102 | fired | Senate on-merits failed 47-53 (18 cycles after logging) | y |
| P97-03 | 97 | signal | Second Iranian strike with Gulf-state civilian casualties | 100 | fired | Ballistic missiles at two GCC states simultaneously (largest single-cycle launch) | partial: BS-18 fracture-test logged, "any measures" decay noted; pre-committed Fork A re-elevation NOT applied (Fork A HELD 18-28; brake held); justification recorded Day 100 |
| P95-01 | 95 | signal | IDF halts past-Litani ops + Beirut stand-down | 100 | did-not-fire | Lebanon ceasefire COLLAPSED instead (Hezbollah rejection + IDF non-compliance); see S2 lineage | n.a. |
| P88-04 | 88 | signal | Netanyahu accepts sustainable Lebanon ceasefire language in MOU | 100 | did-not-fire | Lebanon clause double-blocked Day 100; opposite branch realized | n.a. |
| P86-04 | 86 | signal | Knesset dissolution readings advance to scheduling | 100 | fired | Knesset advancing; pre-caretaker window compressing | n.a.: no specific move pre-committed |
| P93-03 | 93 | signal | Lebanon-Israel June 2-3 talks produce named ceasefire text Iran accepts | 97-100 | fired-partial | Framework text produced June 3; Iran "all fronts" acceptance never came; collapsed Day 100 | y: Fork D' HELD 22-30 with offset driver named Day 97 |
| P93-02 | 93 | signal | House WPR passes June 2 (Golden flip + 3+ GOP) | 97 | fired | House WPR PASSED June 2 | partial: pre-committed "T9 → CONTESTED" NOT applied; held for Senate on-merits test (justified Day 97; vindicated Day 102). Logged as correct override of a pre-commitment |
| P85-04 | 85 | signal | House WPR scheduled and passed after Memorial Day | 97 | fired | Same event as P93-02 | partial (see P93-02) |
| P90-01 | 90 | signal | IRGC executes "reciprocal response" against US naval/air asset | 93 | fired | Fateh-110 ballistic missile on US base in Kuwait; 5 Americans injured; warning shots at 4 vessels | y: Fork C 18-25 → 22-30; KIA sub-condition not met so Fork A entry correctly NOT applied |
| P88-01 | 88 | signal | MBS public rejection of Abraham Accords demand | 93 | fired-partial | MBS "Palestinian-state-first" position confirmed (conditional, not flat rejection) | y: Fork B-multilateral 11-18 → 10-15 |
| P84-05 | 84 | signal | Saudi-Iran principal-level meeting during Hajj window (May 24-29) | 90 | did-not-fire | Pilgrim conduit disconfirmed (visas suspended); no principal meeting; window closed | y: pending-candidate revised to official-level-contact criterion (Day 88 audit) |
| P84-10 | 84 | signal | Mojtaba Tier-1 Mahdist invocation during Hajj window | 90 | did-not-fire | Hajj closed; Day 90 written message doctrinal, not Mahdist; T5 holds PENDING | n.a. |
| P84-09 | 84 | signal | Eisenhower deployment order; offensive ROE; Sledgehammer executed | 90 | did-not-fire | Suspension extended; no deployment through Day 90 carry; dropped from lists | n.a. |
| P88-02 | 88 | signal | Rubio/State echoes "mandatory" Accords framing within 48h | 90 | did-not-fire | No echo in window; two-reading ambiguity resolved toward leverage | n.a. |
| P88-03 | 88 | signal | Iranian T1 wholesale MOU rejection | 102 | did-not-fire | June 1 suspension was conditional and unnamed; talks resumed | n.a. |
| P87-02 | 87 | signal | T1 intra-troika split (UAE public break) | 90 | did-not-fire | Saudi-UAE divergence stayed T2/T3 analytical | n.a. |
| P87-03 | 87 | signal | IEA June Hormuz-resumption assumption fails absent LOI | 102 | expired-unresolved | Two-track transit continued; shortfall-path data not retrievable at T1/T2 | instrumentation gap → audit |
| P90-02 | 90 | signal | Second US strike round inside Iran under new operation name | 102 | did-not-fire | "No new operation name" held through Day 102 | n.a. |
| P90-04a | 90 | signal | BS-9.3 April Putin appearance count retrieval | 102 | expired-unresolved | April count unresolved across 5 SITREPs; carried; second expiry triggers audit escalation | instrumentation gap → audit |
| P86-01 | 86 | signal | Trump revises "largely negotiated" after Netanyahu contact (May 25 test) | 87 | fired | Walk-back to "in no rush" within ~24h; Penetration mechanism operative | y: Fork D' 27-35 → 25-33, driver cites walk-back |
| P86-02 | 86 | signal | 6th round Oman produces MOU text signed or formally rejected | 88 | did-not-fire | Round outcome unconfirmed; "mixed messages"; neither branch | n.a. |
| P85-01 | 85 | signal | Munir travels to Tehran (breakthrough-condition inverse of non-travel) | 86 | fired | NON-TRAVEL → TRAVEL May 23 | y: Fork D' 22-30 → 27-35, driver cites Munir arrival |
| P85-03 | 85 | signal | Named-country product-scarcity riots (ZA/IN/TH/TW) | 88 | did-not-fire | No riots; dropped after Day 86 | n.a. |
| P84-01 | 84 | signal | Araghchi/Baghaei T1 named acceptance or rejection of LOI concept | 86 | fired-partial | Baghaei "finalization stage of this memorandum" (mid-tier named; not accept/reject) | y: Fork D' ↑ driver cites Baghaei finalization |
| P84-03 | 84 | signal | Trump holds deal-direction past May 22-25 window (second extension) OR abandons | 85 | fired | Second extension "couple of days past May 22" | y: extension logged as B-multilateral driver; BS-18 brake durability noted |
| P84-04 | 84 | signal | Knesset first subsequent dissolution reading | 85 | fired | Readings advanced on schedule | n.a. |
| P84-06 | 84 | signal | Second Barakah-class Gulf infrastructure attack + UAE attribution | 102 | did-not-fire | As stated, never; adjacent events arrived via different vectors (see S5, P97-03 lineage) | n.a. |
| P84-02 | 84 | signal | Munir public characterization of Tehran meetings as accepted-in-principle | 85 | superseded | Reformulated as travel/non-travel signal (P85-01) after Day 85 cancellation | n.a. |

*Backfill notes.* (1) Rows carried verbatim across multiple SITREPs are logged once from first appearance; 41 unique rows compress ~110 list entries. (2) Day 89, 91-92, 94, 98-99, 101 had no SITREP; windows bridge per supersede chain. (3) The two `n.a.`-heavy blocks are healthy: most did-not-fire rows pre-committed moves only on the fire branch.
