# Synthesis v4-3 Manifest — Principal-Validation Demotion

**Staged:** 2026-05-27 (Day 90)
**Source:** `premortems/premortem-2026-05-27.md`, Failure 1 (wrong-principal lock-in) + Failure 2 (replacement-attribution thinness)
**Activation:** consume at next `/revise` (v4.2 → v4.3 minor increment, or rolled into next major if one fires sooner)

---

## Scope

Two named-principal commitments load-bearing in v4.2 have reached the 5th-plus consecutive cycle without discriminating evidence. Per the principal-validation discipline introduced in v4.2 manifest S7, both must be demoted from "carried at M confidence" to "provisional pending discriminating evidence." This is the discipline's first operational application at synthesis-revision scope; v4.2 applied it to A4 once at re-identification (Mojtaba → IRGC council) but did not specify what happens when the *replacement* attribution itself accumulates cycles without discriminating evidence.

---

## S1 — A2 Netanyahu-Penetration-relay demotion

**Current state (v4.2 §4.3 + A2):** the Netanyahu-relayed Trump "full dismantlement / all HEU removed" private-assurance claim is the load-bearing input to the Penetration mechanism's intensity reading. Day 84-90 SITREPs carry the claim at M confidence with `4th-plus cycle without White House corroboration` flag, escalated to 5th-plus on Day 90.

**Demotion:** A2 moves from "validated; reformulated state active-but-non-reversing" to **provisional**. Penetration mechanism's intensity is recharacterized as **Netanyahu-coalition-projected**, not **Trump-committed**, until the discriminating evidence arrives. The Penetration mechanism's existence is unaffected; its *content* (what Trump has actually committed to) is provisional.

**Discriminating evidence (any one resolves):**
- A White House readout, transcript, or press statement using "full dismantlement," "all HEU removed," or substantively equivalent language attributed to Trump directly.
- A second-source named US official (Rubio, Vance, NSC principal) corroborating the same maximalist commitment in the same language.
- Trump tape action consistent with the maximalist commitment (e.g., signed order, public ultimatum citing the same terms).

**If the discriminating evidence does not arrive within 6 cycles of v4.3 release:** A2 demotes from provisional to **inherited; mechanism reconstructed**. The Penetration mechanism then operates with Netanyahu-coalition-projection as its *input*, not Trump-commitment.

**Probability matrix effect:** Israeli unilateral pre-emption (14-21d) loses ~3-5pp of its Penetration-amplified loading; absorbed into the existing 15pp range, no row decomposition required. Fork A composite drift band unchanged.

---

## S2 — A4 IRGC-council-functional-apex demotion

**Current state (v4.2 §3.5 + A4):** the IRGC military council of senior officers controlling Mojtaba's access is the v4.2 re-identification of the Iranian functional apex; the Day 84 HEU-stays directive was reattributed to IRGC origination. Carried at M confidence since Day 88; the Vahidi-direct named statement on HEU (the named discriminating evidence) has been absent across Day 88, 89, 90 cycles (~5th cycle if Days 84-87 inherited-Mojtaba period is counted as the same attribution-uncertainty window; ~3rd cycle if counted from Day 88 re-identification only — the principal-validation rule covers both readings).

**Source-base thinness (Failure 2):** the IRGC-council attribution rests primarily on Iran International T3 (single primary outlet) plus WSJ-sourced US reporting on Mojtaba's incapacitation. No second-cluster intelligence-ecosystem corroboration of the council-structure claim has arrived (contrast Day 88 ToI Israeli-IC second cluster on reconstitution-faster).

**Demotion:** A4 moves from "re-identified; IRGC-council functional apex" to **principal-uncertain provisional**. The Iranian functional apex sits within a candidate set: {IRGC military council per Iran International, Aerospace Force command, supreme-leader-office staff retaining substantive authority, Vahidi-led but more diffuse than the council framing implies}. The two-level structure (T3) is unaffected; only the principal identity within the apex layer is provisional.

**Discriminating evidence (any one resolves):**
- Vahidi-direct named statement on HEU disposition (already named in v4.2 §A4).
- A second-source intelligence-ecosystem corroboration of the IRGC-council structure claim, independent of Iran International (e.g., US-IC named-source, Israeli-IC named-source, Reuters/AP investigative with non-diaspora-aligned sourcing).
- Authenticated visual Mojtaba appearance (revises toward functional Mojtaba-apex, retiring the council attribution).
- Pezeshkian re-gaining apex access (revises toward elected-government-apex, retiring both Mojtaba and council).

**If the discriminating evidence does not arrive within 6 cycles of v4.3 release:** A4 demotes from principal-uncertain provisional to **structurally-opaque; principal-identity un-knowable at current sourcing**. The two-level structure remains; the apex-principal slot is treated as a black box for synthesis purposes.

**Probability matrix effect:** Fork B-bilateral and Fork B-multilateral ranges hold (the deal-terms floor's *content* is unaffected). Fork D' 30d may marginally tighten as principal-uncertainty raises the value of structured deferral. No row decomposition.

---

## S3 — Replacement-attribution discipline cross-reference

v4.3 Methodological Note (§2a) must cross-reference the new `reference/quality-sources.md` Source-Independence Discipline replacement-attribution addendum (Mitigation 2 of the same /premortem). The cross-reference is the synthesis-level acknowledgment that the v4.2 source-independence discipline correctly retired one attribution and the v4.3 discipline correctly resists granting halo confidence to its replacement. Single sentence; no new content.

---

## S4 — A4 re-identification halo retraction

v4.2 Version Notes characterized the A4 re-identification as the principal-validation discipline "working as designed: a named-principal commitment inherited from media framing, re-validated against discriminating evidence, and corrected." v4.3 Version Notes must note that the re-validation was against *replacement* framing of comparable thinness, and the discipline has now been tightened (Mitigations 1 and 2 of the 2026-05-27 /premortem) to require replacement attributions enter at L provisional, not M with halo. Single paragraph in v4.3 Version Notes; no synthesis-body content change.

---

## Activation conditions

Consume on next `/revise`. If `/revise` is deferred (no trend transition, no reference apparatus change, no other manifest trigger), the demotion still applies at the audit layer: the next `/audit` and `/sweep` must treat A2 and A4 as provisional per S1 and S2 in finding-card commentary, even before synthesis absorption. Audit-layer treatment lags synthesis absorption by the normal cadence; the discipline is the same in either case.

If a Vahidi-direct HEU statement arrives before consumption, S2 retires; v4.3 absorbs A4 as **validated** rather than demoted. If a White House "full dismantlement" readout arrives before consumption, S1 retires similarly.

---

*Manifest consumes from `premortems/premortem-2026-05-27.md` Failures 1 + 2. Archive to `synthesis/staging/archive/` after v4.3 write.*
