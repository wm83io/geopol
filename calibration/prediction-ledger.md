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

## Scorecard (updated through Day 123)

| Metric | Count |
|---|---|
| Signal rows logged | 67 |
| Resolved fired (full + partial) | 23 (14 full, 9 partial) |
| Resolved did-not-fire | 20 |
| Expired-unresolved | 1 (P90-04a resolved-late Day 105) |
| Superseded | 2 (+Day 123: P115-03 superseded by v4.5 A4 demotion) |
| Open (carried into Day 124+) | 20 |
| Surprises (unlisted major movers) | 6 (Day 123: no new surprise; kinetic cluster pre-listed) |
| **Watchlist coverage** | **21 / 27 major movers pre-listed (Day 123: the US-Iran kinetic exchange was pre-listed via P115-02 vessel branch + the CENTCOM-strike branch, and the Iran-base-strike modality recurred from Day-90 P90-01; no new surprise, a coverage recovery after the Day-119 S6 miss; N below interpretation floor)** |
| **Matrix-followed** | **y: 13, partial: 8, n.a.: 5, n: 0 (21/21 scoreable followed)** |
| Fork snapshots logged | 2 (both pending expiry; F95-30d due Jul 1, F102-30d due Jul 8) |
| Fork snapshots scored | 0 |

Reading (provisional, small N): process discipline holds (no fired signal saw its pre-committed move silently ignored; Day-123 P115-02 fired-partial applied the Fork C re-arm and justified withholding the Fork A reset; P119-02 fired-partial held D'-v as the leading variant). Coverage recovered at Day 123: the cycle's major mover (the US-Iran bilateral kinetic exchange driving the Fork C re-arm) was substantially pre-listed via the P115-02 vessel-interdiction branch and the CENTCOM-strike branch, with the Iran-base-strike modality a recurrence of Day-90 P90-01, so no new surprise was logged, reversing the Day-119 S6 domestic-institutional miss. The cascade-to-Fork-A barrier held under live fire (zero US KIA; no operation name), vindicating the standing Fork-A-reset-withhold discipline. Instrumentation persistence remains the open weakness (Vahidi-direct HEU absent again D123, 12th; the apex-direct discriminator question retired into the v4.5 A4 structurally-opaque demotion, P115-03 superseded, successor P123-04 the A4-resurrection watch). Process watch for /audit: the BS-7/BS-11 Hormuz operational sub-read has oscillated four consecutive cycles (settled → re-arm → declaratory → live-exchange), a recency-bias pattern routed to /premortem.

---

## Surprise register (Days 84-119)

| # | Day | Event | Matrix effect | Why unlisted |
|---|---|---|---|---|
| S1 | 85 | Iran-Oman permanent Hormuz toll (second LOI collision) | Fork B-bilateral 10-16 → 8-14; Fork D' 25-33 → 22-30 | Watchlist tracked HEU collision only; no second-collision class |
| S2 | 88 | Lebanon clause enters MOU as binding obstacle | Became dominant Fork D' blocker through Day 102 | Israeli spoiler tracked as kinetic, not diplomatic-clause vector |
| S3 | 88 | Abraham Accords "mandatory" demand (Trump) | Fork B-multilateral 13-20 → 11-18 | No Trump-initiated-demand class on any list |
| S4 | 90 | CENTCOM self-defense strikes inside Iran | Fork C 15-22 → 18-25 | US-side kinetic initiation absent from Day 88 list (Israel-side and IRGC-side were listed) |
| S5 | 101-102 | Iran ballistic missiles at Israel (new direct axis) | PROBE-16 fired; third accident surface; Fork C upper band | Day 100 list had IRGC-vs-US and Gulf-strike branches; no Iran-vs-Israel branch |
| S6 | 119 | Senate WPR passes 50-48 (first WPR to clear both chambers) | T9 VALIDATED → CONTESTED flag (Day-105 reachable trigger b: second single-chamber on-merits passage) | SITREP watchlists carried no domestic war-powers re-trigger branch; the Day-115 sweep PROBE-10 skip-note flagged it but it was not a ledger-ready signal row |

Pattern: the first five surprises are escalation-side and adversary-vector (toll, clause, axis). S6 is the first domestic-institutional surprise: a US-side constitutional-track event (not an adversary option) forced a trend move. The watchlist gap is now two-sided, over-indexing on resolution-side discriminators while under-indexing both adversary option-generation AND domestic-institutional re-triggers. Routed to `/audit` Source C; extends the Day-105 watchlist-construction directive to require a domestic-institutional branch alongside the adversary-new-vector branch.

---

## Open predictions

| ID | Logged | Carried-to | Type | Claim | Pre-committed move | Resolve-by |
|---|---|---|---|---|---|---|
| P84-07 | 84 | 123 | signal | Vahidi direct named statement on HEU disposition | A4 HEU-axis resolved; synthesis revision candidate | standing; absent again D123 (12th); A4 now structurally-opaque (v4.5) |
| P87-01 | 87 | 123 | signal | White House readout using "full dismantlement" / "all HEU removed" | A2-resurrection: WH asserting maximalist terms absent from the signed text | standing; A2 demoted to inherited (v4.5); evidence-against again D123 (US struck on its own shipping framing, not Israeli terms) |
| P85-02 | 85 | 123 | signal | Israeli unilateral strike on Iranian nuclear/military site | Fork D' and Fork B collapse; mass into Fork A | standing tail-watch; did-not-fire D123 (Israel signed Lebanon framework; no Iran strike even during the US-Iran exchange) |
| P86-03 | 86 | 123 | signal | IDF air-refueling tempo / F-35-F-15 forward-positioning escalation | Israeli pre-emption rhetorical → operational; Variant B reprices toward 38-50% | standing; no signal D123 |
| P93-04 | 93 | 123 | signal | US KIA in any kinetic exchange | Fork C resolves into Fork A entry; deal track collapses; matrix resets | standing; did-not-fire D123 (IRGC base strikes zero US KIA) |
| P97-02 | 97 | 123 | signal | Tehran Grand Bazaar full closure confirmed T1/T2 | BS-1b activates; BS-15 Iran-side threshold breached | open; did-not-fire D123 |
| P100-09 | 100 | 123 | signal | Hezbollah accepts South Litani withdrawal framework | Lebanon triple-block partially resolves; Fork D' lower bound recovers toward 26-34% | open; did-not-fire D123 (state-level framework signed June 26 but Hezbollah rejects "null and void") |
| P102-02 | 102 | 123 | signal | Second Iran-Israel direct exchange without successful Trump halt | Fork C → 22-32%; deal-direction breaking; synthesis revision required | next Lebanese provocation cycle; did-not-fire D123 (the exchange was US-Iran) |
| P102-03 | 102 | 123 | signal | Netanyahu coalition fracture (far-right resignation) | Caretaker accelerates; Lebanon clause → Zamir authority; Fork D' recovery conditional | open; did-not-fire D123 (Ben Gvir/Smotrich reject, no resignation), watch rising |
| P102-09 | 102 | 123 | signal | Saudi public support for US military action | BS-18 fractures; Fork A re-elevates; Fork B-multilateral collapses | standing; did-not-fire D123 (Gulf condemned Iran's Gulf-soil strikes; did not endorse the US strikes on Iran) |
| P105-01 | 105 | 123 | signal | CENTCOM names a new operation (any name abandoning self-defense framing) | Fork A ACTIVATED; Fork A 22-34% → 40-55%; Fork D' < 5%; deal track terminal | standing; did-not-fire D123 (strikes self-defense framed, no operation name) |
| P105-05 | 105 | 123 | signal | Brent >$100/bbl sustained (close, not intraday touch) | Oil-price-geostrategy trigger-read activated; domestic US pressure inflection | standing; did-not-fire D123 (Brent ~$73.21) |
| P108-03 | 108 | 123 | signal | Missile-program-limit clause enters the 60-day-talks text | New Fork D' collision class (adversary-new-vector); reprices post-signing deferral path | talks window; did-not-fire D123 (still excluded) |
| P110-01 | 110 | 123 | signal | Third-party demand enters the ceremony/talks text as a precondition (Gulf security guarantee, Israeli Lebanon carve-out formalized, frozen-assets conditionality hardened) | New collision class (adversary-new-vector); reprices D'-i/D'-v | did-not-fire D123 |
| P115-01 | 115 | 123 | signal | Iran links a new MoU term pair via cross-surface compliance leverage (beyond Hormuz-Lebanon) | Promotes the provisional §5.30 4th collision class; reprices D'-v | standing (adversary-new-vector); did-not-fire D123 |
| P119-01 | 119 | 123 | signal | Federal court grants WPA standing OR a veto-override-capable WPR majority forms | T9 → DISCONFIRMED / full falsification; 6/12m Fork A prior → /revise | standing (domestic-institutional vector); did-not-fire D123 (no court; executive struck Iran free of constraint) |
| P123-01 | 123 | - | signal | Iran no-shows or formally withdraws from the June-30 Doha round | D'-i reprices toward the lower band; Fork C re-arms toward the upper band | June 30 - July 2 |
| P123-02 | 123 | - | signal | Hezbollah converts its "null and void" rejection into a kinetic breach of the June-26 framework drawing an Iranian-aligned response | Lebanon residual re-arms; Fork C upper band | next Lebanese provocation cycle (adversary-new-vector) |
| P123-03 | 123 | - | signal | Named MBS-MBZ split on a specific decision following the Gulf-soil strikes | BS-18 fractures; Fork A re-elevates; Fork B-multilateral caps | standing |
| P123-04 | 123 | - | signal | Authenticated apex-direct term-level statement (Mojtaba or Vahidi) owning/repudiating a specific MoU term | A4 resurrection; principal-locus re-opens | next 1-2 cycles (successor to superseded P115-03) |

(Standing rows P85-02, P86-03, P93-04, P97-02, P100-09, P102-09, P105-01, P105-05, P119-01, P123-03 subsume verbatim re-listings in future SITREPs; resolve once, at event or framework retirement.)

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
| P115-02 | 115 | signal | Iran fires on / interdicts US or allied vessel in the closed strait | 123 | fired-partial | Iran drone-hit two third-flag commercial vessels (Ever Lovely/Singapore, Kiku/Panama) and struck US bases in Kuwait/Bahrain, but no US/allied warship and zero US KIA; successor warship/KIA watch stands (P93-04) | partial: Fork C re-arm applied (14-22 → 18-28); Fork A reset withheld pending a US/allied-warship firing + KIA (justified) |
| P119-02 | 119 | signal | IAEA-access dispute hardens | 123 | fired-partial | Grossi: MoU "explicitly" mandates IAEA supervision and inspections will happen; Iran (Gharibabadi) sustained deferral to a final agreement, neither conceding nor terminally rejecting; dispute firms | partial: D'-v held 22-30 as the leading variant; not yet upper-band repriced absent a sustained denial-to-terminal |
| P115-03 | 115 | signal | Authenticated apex-direct term-level statement | 123 | superseded | A4 demoted provisional → structurally-opaque at v4.5 (June 25); the principal-locus-resolution premise is retired; replaced by the A4-resurrection watch P123-04 | n.a. |
| P109-03 | 109 | signal | HEU down-blend verification dispute | 119 | fired | Vance claims Iran agreed to re-admit IAEA inspectors; Iran's ambassador denies, defers to a post-sanctions-relief stage; zero current IAEA access at the four declared sites; successor P119-02 | y: Fork D'-v 20-28 → 22-30 applied |
| P108-04 | 108 | signal | Brent >$92 on signing/ceremony failure | 119 | did-not-fire | Monday June-22 reprice resolved inverse: Brent fell to ~$73-75 ("Brent erases wartime gains as Hormuz reopening boosts supply"); the deal held and the closure was unenforced | n.a. |
| P108-02 | 108 | signal | Iranian apex named statement owning/repudiating MoU | 115 | fired-partial | Mojtaba attributed message: "different view in principle" but approved after SNSC/Pezeshkian assurances; attribution discount applies; successor P115-03 | n.a.: synthesis-revision candidate; A4 narrows to SNSC/Pezeshkian-functional, Mojtaba ratifying-shield |
| P105-02 | 105 | signal | Iran Hormuz formal closure / fires on US vessel | 115 | fired-partial | Formal closure re-declared June 20 as Lebanon-clause leverage; firing/enforcement sub-condition unmet (CENTCOM "traffic flows"); successor P115-02 | partial: Fork C re-arm applied (14-22 → 16-26); Fork A reset withheld pending an actual firing (justified) |
| P109-01 | 109 | signal | MoU formal ceremony executes (Geneva) | 115 | fired-partial | No Geneva ceremony; substance realized via electronic signature June 17 (Trump-Pezeshkian) + June-21 talks convening | partial: D'-i floor held; mass shifted to D'-v on surface friction |
| P109-02 | 109 | signal | Ceremony slips OR hardliner forces apex repudiation before ceremony | 115 | did-not-fire | Ceremony superseded by electronic signature (not a deal-collapsing slip); apex approved with reservation, no repudiation | n.a. |
| P93-01 | 93 | signal | Trump signs 60-day MOU / LOI | 109 | fired | MoU digitally signed June 15 (Trump+Vance / Ghalibaf); blockade lift + Hormuz reopen 30d + 60-day talks; ceremony June 20 | y: Fork D' 34-46 → 50-64 applied; decomposed to D'-i/D'-v variant table; A2 demotion supported |
| P108-01 | 108 | signal | MoU signing slips past June 17 without Iranian acceptance | 109 | did-not-fire | Signature occurred June 15, ahead of the window; inverse of the slip condition | n.a. |
| P105-03 | 105 | signal | Araghchi favorable engagement on Oman counteroffer post-strikes | 108 | fired | "Sign remotely"; agreed 60-day MoU final text (Sharif June 12); exceeded floor-preservation | y: LOI text moved, upward-revision condition met; Fork D' 12-20 → 34-46 applied |
| P105-04 | 105 | signal | CENTCOM strike round explicitly targeting Iranian nuclear sites | 108 | did-not-fire | De-escalation cycle; no nuclear-site strike; "next cycle" window closed | n.a. |
| P102-08 | 102 | signal | Iran hard exit from talks (SNSC/Araghchi T1 refusing Pakistan channel) | 108 | did-not-fire | Strongly inverse: Iran engaged, agreed 60-day MoU final text via Pakistan/Qatar channel | n.a. |
| P102-01 | 102 | signal | Araghchi T1 corroboration of Trump "near-signed" / 72h window | 105 | did-not-fire | Iran rejected proposal June 9; Araghchi "ceasefire meaningless" June 10; Hormuz formally closed June 11 | y: Fork D' declining applied; inverse of pre-committed 24-33% upward move; impasse read confirmed |
| P90-04 | 90 | signal | BS-9.3 fires (Putin <2 appearances/month, 3rd consecutive month) | 105 | did-not-fire | Meduza confirmed 60+ public events April+May; threshold not reached; T6 holds | n.a. |
| P90-04a | 90 | signal | BS-9.3 April count instrumentation retrieval | 105 | resolved-late (was expired-unresolved) | Meduza June 9 confirmed count before second /audit escalation threshold; removed from expired-unresolved | n.a. |
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

*Backfill notes.* (1) Rows carried verbatim across multiple SITREPs are logged once from first appearance; 45 unique rows compress ~110 list entries. (2) Day 89, 91-92, 94, 98-99, 101 had no SITREP; windows bridge per supersede chain. (3) The two `n.a.`-heavy blocks are healthy: most did-not-fire rows pre-committed moves only on the fire branch.
