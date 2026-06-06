# Iran 2026 Framework Pre-Mortem — 2026-05-27 (Day 90)

First diagnostic file written under the formal `/premortem` cadence. The v4.2 manifest (May 22, staged) was /premortem-derived but did not produce a preserved diagnostic; this file establishes the artifact discipline going forward. 30-day window: Day 62 (sweep-2026-04-27) → Day 90 (sweep-2026-05-27); 14 SITREPs (day-62 → day-90), 13 sweeps. Synthesis anchor: v4.2.

Six-month-forward frame: imagine that by November 2026 the framework's 30-day and 6/12-month projections from Day 70 onward were materially wrong. What is the most likely cause?

---

## Mitigation manifest

| # | Failure mode | Routing | File to patch | Status |
|---|---|---|---|---|
| 1 | A2 / A4 fifth-cycle wrong-principal commitments unactioned | slash-command-patch + synthesis-manifest | `.claude/commands/sweep.md` Step 7b + `synthesis/staging/v4-3-principal-validation-manifest.md` | **approved 2026-05-27; executed** |
| 2 | Replacement-attribution thinness (IRGC-council apex inherits Mojtaba's failure mode at deeper layer) | reference-patch | `reference/quality-sources.md` (Source-Independence Discipline rule 5) | **approved 2026-05-27; executed** |
| 3 | Trend-rigidity hidden in operational reading swings (T1 Accords "strain"→"calendar-structural" within 2 cycles uncounted in disc-ratio) | reference-patch | `reference/strategic-trends.md` (reading-swing counter + T1 Day 90 drift-log entry) | **approved 2026-05-27; executed** |
| 4 | Fork D' decomposition rule on verge of firing without pre-staged variants | slash-command-patch | `.claude/commands/sitrep.md` (Fork D' pre-staging rule at 2 of 4 cycles above 30%) | **approved 2026-05-27; executed** |
| 5 | 6/12-month matrix frozen across T12 promotion without explicit reasoning | slash-command-patch | `.claude/commands/revise.md` (explicit-reasoning per trend transition in §8.1b Version Notes) | **approved 2026-05-27; executed** |

---

## Failure-mode finding cards

### Failure 1: Wrong-principal lock-in on A2 (Netanyahu-relay) and A4 (Vahidi-direct-HEU absence)

**Likelihood:** high (incipient evidence in current outputs)

**What happened.** By Nov 2026 the framework's 30-day projections from Day 70 onward routinely mis-priced Israeli pre-emption and Iranian deal-terms posture because the load-bearing principals were misidentified. The Netanyahu "full dismantlement" private-assurance relay turned out to be Netanyahu coalition-language translation of a non-committal Trump reassurance; the framework had effectively been pricing Trump's HEU posture from Netanyahu's mouth for months. Separately, the Iranian apex was neither Mojtaba nor a Vahidi-led IRGC military council but a different faction configuration (e.g., Aerospace Force commander + supreme-leader-office staff retaining substantive decision authority); the IRGC-council attribution was inherited from one outlet's framing and held at M confidence through five cycles without the discriminating Vahidi-direct HEU statement ever arriving.

**Root cause.** v4.2 manifest S7 created the principal-validation discipline (4+ cycles without discriminating evidence → `inherited, not validated` flag → /premortem review). Day 90 audit and Day 90 SITREP both flag A2 and A4 at the 5th-plus consecutive cycle. The rule is being applied (flag set) but is not yet routing to action: no synthesis manifest staged, no slash-command enforcement, no scheduled discriminating-evidence forcing. "Flagged for /premortem" became its own form of holding.

**Evidence in current outputs.** day-90.md Section 7 ("Operative Judgment"): "Two principal-validation items now sit at the /premortem threshold and should be actioned at next audit. The Netanyahu-relayed Trump maximalist private assurance is in its 5th-plus consecutive cycle without White House corroboration... And the Vahidi-direct HEU statement... is absent for a comparable run, leaving the IRGC-council functional-apex attribution 'inherited, not validated.'" sweep-2026-05-27.json PROBE-13 conflict_notes: "the /premortem wrong-principal review threshold (4+ cycles) is met and should be actioned." Day 90 appendix audit note: "A2 and A4 principal-validation flags at 5th-cycle /premortem threshold." Three artifacts naming the same pending action; none has staged it.

**Mitigation.**
- Stage `synthesis/staging/v4-3-principal-validation-manifest.md` with two items: (a) demote A2 to provisional pending a White House direct readout using "full dismantlement" / "all HEU removed" language, and treat the Penetration mechanism's intensity as Netanyahu-coalition-projected rather than Trump-committed until corroborated; (b) demote A4 to provisional principal-uncertain (functional apex within {IRGC military council, Aerospace Force command, supreme-leader-office staff}, not committed), pending a Vahidi-direct named statement on HEU OR a second-source on the IRGC-council structure independent of Iran International.
- Patch `.claude/commands/sweep.md` Step 7b: when a principal-validation flag reaches the 5th consecutive cycle, the next /sweep must produce an explicit discriminating-evidence forcing question (what would falsify the current attribution this cycle?) and the next /audit must stage a manifest, not re-flag.

**Routing.** `slash-command-patch` + `synthesis-manifest`.

---

### Failure 2: Replacement-attribution thinness — IRGC-council apex inherits Mojtaba's failure mode at a deeper layer

**Likelihood:** high (evidence-based pre-mortem)

**What happened.** The Mojtaba HEU-stays directive was correctly retired on Day 88 under the v4.2 source-independence discipline (multi-outlet pickup of one anonymous cluster = one source). The framework then re-attributed the directive to an "IRGC military council of senior officers controlling Mojtaba's access," carried at M confidence for five cycles. By November the IRGC-council framing turned out to be Iran International's editorial reading of a thinner factual base (one or two diaspora-aligned sources). The replacement attribution had the same failure structure as the retired one — inherited from one outlet's framing, lacking discriminating evidence — but was protected from scrutiny because it arrived as the discipline's "correction" output rather than as the input the discipline was built to catch.

**Root cause.** The source-independence discipline checks the *retired* attribution for cluster-laundering but does not re-check the *replacement* attribution against the same standard. The retirement event creates a halo: the new principal is treated as "validated by the discipline" when in fact only the old one was invalidated. The Iran International T3 + WSJ-sourced US reporting cluster used for the IRGC-council attribution has not been independently corroborated by a second intelligence-ecosystem source the way the Day 88 ToI Israeli-IC cluster independently corroborated the Day 84 CNN US-IC reconstitution-faster claim.

**Evidence in current outputs.** synthesis-v4-2.md §3.5: "An IRGC military council of senior officers controls all access to Mojtaba (Iran International T3)" — single primary outlet. PROBE-1 sources in sweep-2026-05-27.json carry "Iran International (T3 — IRGC military council apex-access control, carry)" as a single source-line across cycles. The same v4.2 release that codifies the principal-validation discipline (manifest S7) is itself making a principal commitment on a thinner source base than the one it retired.

**Mitigation.**
- Patch `reference/quality-sources.md` Source-Independence Discipline section: add an addendum that every retirement-and-replacement event must satisfy independent-cluster sourcing for the *replacement* attribution at the moment of substitution, not at later cycles. If the replacement attribution is single-cluster, it enters at L (low) confidence and "provisional from inception," not at M with halo. The Day 88 A4 re-identification would have entered as "L provisional from inception" under this rule, and the 5-cycle wait for Vahidi-direct discriminating evidence would have been priced into the confidence rather than treated as drift.

**Routing.** `reference-patch`.

---

### Failure 3: Trend rigidity hidden in operational-reading swings (T1 Accords "strain" → "calendar-structural")

**Likelihood:** medium (incipient pattern; not yet a fail)

**What happened.** By November T1 (tripolar realignment, VALIDATED) had absorbed several rounds of contradicting evidence by re-explaining each contradiction within the trend's pivot-capacity framing. The disc-ratio counter remained 0:n through the window because the framework's *operational reading* swung to absorb each contradiction rather than the *trend state* contracting it. The eventual prediction failure was on the Gulf brake's durability under the Abraham Accords demand: the framework had repeatedly walked back its own near-term reads on MBS strain ("Day 88 strain" → "Day 90 calendar-structural") and lost the signal that the brake itself was contracting under cumulative reciprocity-asymmetry pressure.

**Root cause.** The disc-ratio rule (`reference/strategic-trends.md`) counts cycles where contradicting evidence is discounted. It does not count cycles where the operational reading itself reverses across consecutive cycles within an unchanged trend state. A reading reversal within 2 cycles ("strain" → "calendar-structural") is epistemically equivalent to a single-cycle contradiction discounted: in both cases the trend state was preserved while the framework's commitment to the trend's *operational implication* moved. The disc-ratio undercounts this class of evidence.

**Evidence in current outputs.** day-88.md (synthesis Version Notes): "Day 88 Trump's Abraham Accords 'mandatory' demand inverts the MBS accommodation-reciprocity logic, introducing a structural strain on the most durable brake actor." day-90.md PROBE-20 / Operative Judgment: "MBS's silence is calendar-structural — the demand landed May 24 at the start of the Hajj 96h no-escalation window... MBS cannot respond publicly during the Hajj no-escalation window and the Saudi Eid government holiday, so the silence is forced quiet, not refusal, and the Day 88 'strain' read should be held back rather than promoted to a brake-fracture." Both reads are defensible individually; the cycle-to-cycle swing is the failure surface.

**Mitigation.**
- Patch `reference/strategic-trends.md` Evidence asymmetry log: add a "reading-swing" counter alongside the disc-ratio. A reading-swing fires when the framework's operational implication on a VALIDATED trend reverses across 2 consecutive cycles without the trend state changing. Reading-swing ratio > 1:6 fires the same /premortem trend-rigidity review as disc-ratio > 1:3. Day 88 → Day 90 Accords reversal becomes T1's first logged reading-swing.

**Routing.** `reference-patch`.

---

### Failure 4: Fork D' decomposition rule on the verge of firing without pre-staged variants

**Likelihood:** medium (the trigger condition is two cycles away)

**What happened.** By Day 92 or 93 Fork D' midpoint had been above 30% on four consecutive cycles, triggering the manifest S4 decomposition rule. The decomposition was rushed under cycle pressure ("decompose at next SITREP") and produced incoherent variants: the framework split Fork D' into "LOI signed soon" vs "LOI signed but breaks" without distinguishing the dispositive Lebanon-clause-bridged vs Lebanon-clause-blocked branches that actually structure the 30-day path. The downstream probability bands inherited the rush and stayed mis-calibrated for several cycles.

**Root cause.** The decomposition rule fires reactively at the trigger threshold. The framework has no pre-staging requirement: there is no rule that says "when Fork D' midpoint is above 30% on 2 of 4 cycles, pre-stage the candidate variants in the SITREP appendix so the next firing can adopt rather than improvise." Currently Day 86 (31%), Day 88 (32%), and Day 90 (32%) are above 30% with Day 87 below, i.e. 3 of 4 above. One more cycle above 30% with Day 91 above forces decomposition.

**Evidence in current outputs.** day-90.md Section 5a Fork D' row and the explicit `Fork D' midpoint ~32%; 2nd cycle above 30% with Day 88 (Day 87 below). The 4-consecutive-cycle decomposition rule is not triggered; if the midpoint sustains above 30% through the next two cycles, decompose into named variants.` sweep-2026-05-27.json PROBE-12' variable_moved restates the same. The trigger is acknowledged as approaching; no variants have been pre-thought.

**Mitigation.**
- Patch `.claude/commands/sitrep.md` to require: when Fork D' midpoint has crossed 30% on 2 of the last 4 cycles, the SITREP appendix must include a "Candidate decomposition" sub-block listing 3-5 named Fork D' variants the framework would adopt if the trigger fires next cycle. Candidates for Day 91: (a) LOI signed within 7 days with Lebanon clause deferred; (b) LOI signed within 7 days with Lebanon clause bridged via post-caretaker Zamir baseline; (c) LOI signed with Lebanon clause unresolved and breaks within 30 days; (d) LOI deferral via Iranian non-acceptance with talks continuing past 7 days; (e) LOI deferral via diplomatic-spoiler collapse into Variant B.

**Routing.** `slash-command-patch`.

---

### Failure 5: 6/12-month matrix frozen across T12 promotion without explicit reasoning

**Likelihood:** low-medium (correct discipline applied silently; reasoning gap is the failure surface, not the numbers)

**What happened.** By November the 12-month Fork A composite (43-53% in v4.1 baseline) turned out to have been mis-priced because T12 (reconstitution-speed amplifier) was promoted PENDING → VALIDATED at Day 88 and v4.2 held the 12-month number unchanged. The discipline rule (6/12m updates only on trend-state transitions) said the number *could* move; v4.2 chose not to move it but did not write down *why*. The implicit reasoning ("T12 was already priced as a pending candidate in v4.1") may have been correct, but absent explicit justification the rule's application drifted: subsequent SITREPs treated the 12-month numbers as canonically frozen rather than as a decision held under reasoning that bears re-examination.

**Root cause.** The two-matrix discipline (manifest S1-S2) correctly separates cycle-Bayesian updates from structural-prior updates. It does not require explicit reasoning when a stated trigger fires but the priors are held unchanged. The silence about why T12 promotion did not move the 12m Fork A number is the gap. Over multiple cycles, "no number change" becomes a pattern that masks whether the priors should have moved.

**Evidence in current outputs.** synthesis-v4-2.md §8.1b: "No trend-state transition this revision; values unchanged from the v4.1 structural-prior baseline (Day 84). Structure updated per manifest S2 (None-of-above row added; 15pp cap verified)." But the Day 88 /audit promoted T12 — a trend-state transition — and v4.2 was released the same day. The 12m Fork A row carries "reconstitution-speed Powell amplifier (standalone-promotion pending /audit)" in the driver column but holds the number; no Version Notes line explains the held number under a fired transition. day-90.md §5b reprints the v4.1 numbers and notes "no update this cycle" without re-engaging the v4.2 release-day question.

**Mitigation.**
- Patch `.claude/commands/revise.md` to require: at every synthesis revision, the 6/12-month matrix Version Notes line must explicitly state, per trend transition logged in `reference/strategic-trends.md` since the previous revision, whether the structural prior moved and why or why not (e.g., "T12 PENDING → VALIDATED on Day 88: 12m Fork A held at 43-53% because the v4.1 baseline already priced the reconstitution amplifier as pending candidate in the Fork A driver; formal promotion adds confidence, not magnitude"). One sentence per transition, mandatory.

**Routing.** `slash-command-patch`.

---

## Defensive-rule metastasis check

For each defensive rule in the framework, asking: is this rule, in the last 30 days of outputs, producing the failure it was designed to prevent?

| Rule | Failure-it-prevents | Current metastasis state |
|---|---|---|
| Multi-cycle confirmation | Recency bias | **Partially metastasizing** via reading-swings (Failure 3): the trend state holds while operational implications swing across cycles, preserving the trend by repeated mid-course corrections. The 30-day decay clause and symmetric demotion (v4.2) address the explicit-contradiction case; the implicit-reading-swing case is unguarded. |
| Source tiering / cluster-laundering check | Treating multi-outlet single-cluster pickup as multi-source | **Metastasizing at the replacement layer** (Failure 2): the check correctly fires on the retired attribution but the replacement attribution is granted halo confidence. The discipline catches the input; it does not catch the substitution. |
| Voice discipline / substrate-as-agent prohibition | Wrong-principal lock-in | **Working at structural layer; failing at routing layer** (Failure 1): the discipline correctly flags A2 and A4 at the 5-cycle threshold; the framework has not yet built the action-routing to convert flags into staged manifests. "Flagged" became a holding state. |
| Range-only probability (15pp cap, None-of-above floor) | Composite degeneracy, false precision | **Working;** no current degeneracy. KEC remains in the Section-8 footnote per v4.2; primitives lead. Fork D' decomposition rule will be tested in 1-2 cycles (Failure 4). |
| Two-matrix cadence (30d cycle-Bayesian, 6/12m structural-prior) | Cycle-noise miscalibrating long horizons | **Procedurally working; reasoning-gap visible** (Failure 5): the 6/12m matrix correctly does not update on cycle noise but does not produce explicit reasoning when a stated trigger (trend transition) fires and the numbers are held. The risk is silent priors mistaken for re-validated priors. |

Counter-rules proposed:
- Failure 1 → action-routing rule on 5-cycle principal-validation flags.
- Failure 2 → replacement-attribution provisional-from-inception rule.
- Failure 3 → reading-swing counter alongside disc-ratio.
- Failure 5 → explicit-reasoning requirement on held structural priors at every revision.

The metastasis pattern is consistent: each rule's *flag* fires correctly; each rule's *consequent action* is incompletely specified. The framework is good at noticing failure modes and weaker at routing the notice into structural change. This is the highest-leverage finding of the diagnostic.

---

## Closing note

Five failure modes, five mitigations, all routable inside the framework's own discipline architecture. No new lens is needed; the existing rules need their action-routing tightened. The wrong-principal failure (1) is the most urgent because it is two named items at the 5th-cycle threshold producing load-bearing synthesis statements. The replacement-attribution failure (2) is the deepest because it shows the v4.2 discipline correction has its own failure surface one layer below. The metastasis pattern (rule fires, action stalls) is what binds them together.

Total word count target ≤ 2,500; this file ~2,360 words excluding the table and metastasis grid.

*Compiled 2026-05-27 | Day 90 | next /premortem: monthly floor 2026-07-01 unless triggered earlier by major-version increment, drift event, or manual invocation.*
