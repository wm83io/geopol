---
description: Execute the Iran 2026 probe cycle against Appendix B and write a sweep JSON
---

# Iran 2026 — Probe Runner

Executes the probe cycle against Appendix B's blind-spot inventory. Produces structured output
consumed by the SITREP composer and auditor skills. Probe scope per cycle is governed by the tier
model below; not every probe runs every cycle.

**Output schema:** `probes/probe-schema.md` — read before writing any finding card.

---

## Pre-flight

Load into working context before any probe runs. All paths are relative to the repo root.

1. **Strategic trends baseline:** read `reference/strategic-trends.md` FIRST. Read the summary
   table in full; read in full only the trend entries changed since the last sweep
   (`git diff <last-sweep-commit>..HEAD -- reference/strategic-trends.md`). Weekly full-read floor
   per CLAUDE.md. Each fired trigger this sweep produces must be classified against current trend
   states at Step 6.
2. **Anchor synthesis:** read highest-versioned file in `synthesis/`
   Record current probability values and assumption states — probes are deltas against this baseline.
   Full re-read on version change; otherwise the probability-matrix and assumption sections suffice
   (weekly full-read floor).
3. **Appendix B:** read the state tables (Confidence Architecture Summary, tier table once the
   audit adds one) plus the full directive entry for each probe in scope this cycle.
   `appendix/appendix-b-blind-spots.md` is the authoritative probe spec; execute only probes
   listed there. Full re-read at the weekly floor or when the last `/audit` postdates the last sweep.
4. **Last SITREP:** read highest day-number file in `sitreps/`
   Establishes current operational baseline.
5. **Output schema:** read `probes/probe-schema.md`
   and `probes/probe-schema-json.json` — governs output format.

After completing the sweep, write output to `probes/sweeps/sweep-{YYYY-MM-DD}.json` using the Write tool.
Confirm write succeeded before reporting completion.

---

## Probe Execution Loop

For each probe in scope, execute all six steps in order. Log any deviation with a reason.

### Step 1 — Read probe spec

Pull the probe definition from Appendix B: target signal, source ladder, framework revision conditions.
Treat as authoritative. If a source ladder looks incomplete, note it for the auditor. Do not silently expand.

### Step 2 — Source-tier search (3–5 calls per probe)

Execute in tier order. Stop when signal is sufficient — do not exhaust lower tiers if tier 1 is decisive.

**Tier 1 (primary):** Government statements, CENTCOM, named-official quotes (Araghchi, Ghalibaf, Vahidi direct),
Kremlin readouts, Treasury/OFAC, court filings.

**Tier 2 (investigative):** FT, Reuters, AP, WaPo, NYT, Bloomberg, NBC/ABC with named sources. WSJ Faucon-tier
specialist reporting.

**Tier 3 (analytical):** ISW, ICG/Vaez, Foreign Affairs, Foreign Policy, Chatham House, CSIS, Lawfare, HCR,
Anders Puck Nielsen, Sinocism (Bishop — Chinese signals), The War Zone (defense operational).

**Tier 4 (specialist data):** Kpler/Vortexa (tanker tracking), S&P Global/Platts (oil-flow and Hormuz throughput),
USNI News (fleet), Bonbast (rial parallel rate), ACLED (incidents), Polymarket (prediction markets), CISA advisories.

**Iranian internal:** Iran International, IranWire, Radio Farda, BBC Persian, Al-Monitor Iran desk,
Tasnim (read against the grain).

**Israeli internal:** Haaretz, Times of Israel, Channel 12, Jerusalem Post.

**Russian internal:** Meduza (siloviki dynamics, BS-9 primary), iStories/OCCRP (security-service investigative),
The Insider (GRU attribution).

### Step 3 — Apply discount rules

Apply before scoring. When sources conflict, report the conflict explicitly — do not average.

| Source type | Discount |
|---|---|
| Exile-source-only claim | −50% confidence |
| Single-source Iranian internal politics | −70% confidence |
| Single-source classified content (IRGC briefings, Mossad, Belousov-Talaei) | −50% confidence |
| Trump diplomatic statement (no tape action / CENTCOM / non-US corroboration) | near-zero informational value |
| Israeli intel leak on Iranian reconstitution (not multi-source) | −50% confidence |
| Anonymous "sources familiar" (outlet without track record) | −50% confidence |
| Polymarket / prediction market | signal, not gospel — weight as one analytical source |

### Step 3b — Source-provenance trace (mandatory for every multi-outlet anonymous claim)

Tier ladder rates outlet quality, not source independence. Multi-outlet pickup of one anonymous cluster = one source. Record in `discounts_applied`:

1. **Originating reporter/outlet.** Who broke it; which are wire-pickups.
2. **Cluster identity.** "Anonymous senior X sources" across 5 outlets = 1 cluster.
3. **Independence test.** Genuinely distinct anonymous clusters (different sourcing language, different outlet ecosystems) → partial mitigation of -50% discount. Same cluster → full discount applies regardless of outlet count.

Same originating cluster in 3+ cycles without distinct corroboration → flag for `/premortem` source-cluster-collapse review. Canonical near-miss: D84 Mojtaba HEU (5 outlets, 1 cluster).

### Step 4 — Score the finding

Assign:
- **Status:** `fired` / `partial` / `null` / `gap`
- **Confidence:** `H` / `M` / `L`
- **Trigger match:** which Appendix B trigger row fires, if any
- **Direction:** variable moves `up` / `down` / `no change`

Schema definitions are in `probes/probe-schema.md`. Read that file before writing cards.

### Step 5 — Write finding card

One card per probe. Use the schema in `probes/probe-schema.md` exactly. No length freelancing.

### Step 6 — Trigger escalation

If a probe fires a framework revision trigger: flag immediately, do not defer. Recommend the specific
Appendix A revision and assign urgency (`immediate` / `next cycle` / `next audit`). The auditor skill
consumes this via the trigger digest.

### Step 7 — Reference-trend cross-check (mandatory for every fired trigger)

Name which trend in `reference/strategic-trends.md` the finding advances, holds, or contradicts. Apply:

| Finding type | Action |
|---|---|
| Advances VALIDATED | Standard trigger digest entry |
| Holds VALIDATED | Standard entry; note consistency in `conflict_notes` if counter-hypothesis was live |
| Contradicts VALIDATED, single-cycle | `urgency: next_audit` regardless of operational urgency; cite trend + reference source in `conflict_notes`; do NOT propose BS revision |
| Contradicts VALIDATED, multi-cycle (this cycle + ≥1 prior, or 2+ independent clusters in one cycle) | `urgency: immediate`; propose trend-state transition (VALIDATED → CONTESTED) |
| Closes PENDING-trend instrumentation gap | Flag for audit promotion of trend to VALIDATED |

Canonical failure case the rule prevents: D77 BS-12 "apex-veto" revision against T3 on single-cycle ISW tier-3 evidence; corrected D83. Six cycles of mis-stated PA-gap mechanism resulted.

Add `reference_trends` array to sweep JSON `sweep_metadata` listing relevant trends and net effect (`advance` / `hold` / `contradict_single` / `contradict_multi` / `close_pending_gap`).

### Step 7b — Principal-validation cross-check (mandatory for fired triggers involving named principals)

Principal IDs (Mojtaba, Trump, Netanyahu, Vahidi, MBS, Munir, Xi, Putin) are inherited from media framing. For each fired trigger attributing a decision to a named principal, record in `conflict_notes`:

1. **Alternative principal hypothesis.** Who else could be deciding? Examples: Mojtaba HEU → SNSC / Ali Khamenei / IRGC vertex; Trump A1 → unmodeled driver (financial exposure, family, classified intel); Netanyahu Penetration → IDF chief Zamir / Mossad.
2. **Discriminating evidence.** What signal distinguishes the named principal from the alternative? "Behavior consistent with X having decided" = curve-fitting, not validation.
3. **Confidence note.** No discriminating evidence this cycle → mark as `inherited, not validated this cycle`. 4+ consecutive such cycles on a load-bearing principal → flag `/premortem` wrong-principal review.
4. **Action-routing on 5th consecutive cycle (added 2026-05-27 via /premortem; Mitigation 1).** When the same principal-validation flag reaches its 5th consecutive cycle without discriminating evidence, the sweep must produce, in the same finding card's `conflict_notes`, an explicit **discriminating-evidence forcing question for the next cycle**: "What signal in the next cycle would falsify the current attribution?" Concrete and named, not "more evidence." The next `/audit` must then stage a synthesis manifest demoting the attribution to provisional, not re-flag for a 6th cycle. "Flagged for /premortem" is not an indefinite holding state; the 5th-cycle threshold converts the flag to a routed action (forcing question this cycle + manifest at next audit). Canonical case: A2 Netanyahu-relay and A4 Vahidi-direct-HEU absence reached this threshold on Day 90 and were staged at `synthesis/staging/v4-3-principal-validation-manifest.md`.
5. **Forcing question persists through the provisional window (added 2026-06-11 via /premortem; Day 105 Mitigation 4).** Demotion to provisional is not the end of the obligation; it carries a clock (A4/A2 demote to opaque/inherited within 6 cycles of v4.3 absent discriminating evidence). For the entire duration of that provisional window, **every** sweep touching the provisional principal must restate the named discriminating-evidence forcing question in `conflict_notes`; "provisional" is not a new indefinite holding state any more than "flagged" was. Each provisional cycle states what would resolve the candidate set *this* cycle. Where the principal's decisions span multiple escalation surfaces, name the axis-level discriminator explicitly. Canonical case: the A4 GCC-axis attribution. Apex public claim/ownership of the GCC-base strikes (apex-directed; narrows toward council/command) vs apex silence with Aerospace-Force-only attribution (delegated rules of engagement; leaves the apex a black box). The escalation-control reading (whether a US-KIA-triggering strike is apex-intended or agent-autonomous) is load-bearing on Fork A entry probability, so the provisional principal cannot be parked.

6. **A structurally-opaque principal is silence, not a causal variable (added 2026-06-29 via /premortem; Day 123 Failure 2).** Once a principal is demoted to `structurally-opaque` (the provisional window closed with discriminating evidence absent), the framework must hold the node as UNKNOWN, not draw on it as a positive explanatory variable. The opaque node may NOT be the subject of control/intent verbs ("the council controls/calibrates/consents to/orders"); that re-imports the attribution the demotion retired, and a node that explains both escalation ("the council brandishes") and de-escalation ("the council controls the off-ramp") is unfalsifiable. Escalation-control reads must rest on **observable agent behavior** stated as such (IRGC attribution; claimed-vs-actual effect; timing; which command issued the statement), with the apex node held as unknown until the resurrection condition (an authenticated apex-direct term-level statement) fires. This is the substrate-as-agent prohibition (CLAUDE.md voice discipline) extended to demoted-opaque principals: "opaque" is the endpoint, not a new holding state that quietly carries load. Canonical case: the Day-123 base strikes were IRGC-attributed and apex-unowned; the disciplined read names the IRGC behavior and the claimed-vs-zero-damage gap, and does NOT attribute "council-level control of the off-ramp" to the structurally-opaque apex.

The step does not require resolving the principal question every cycle; it requires not pretending it is settled when discriminating evidence is absent, not treating an opaque endpoint as an explanatory node, and routing the absence into structural change once the 5th-cycle threshold trips and through the provisional window thereafter.

Probe specs live in Appendix B. Do not maintain parallel definitions here.

### Probe cadence tiers (added 2026-06-11; replaces the static frequency table)

Tier assignments are owned by `/audit` (Step 5c) and recorded against each directive in Appendix B.
Until the next audit writes them there, the interim assignments below govern.

| Tier | Cadence | Membership rule |
|---|---|---|
| D (daily) | Every sweep | Default. Mandatory for probes attached to CRITICAL-priority BSs and any probe that fired within the last 3 cycles |
| E (event-triggered) | Only when its activation condition is met | Probes whose target signal is a discrete event, not a flow. Activation condition stated per directive |
| M (monthly) | First sweep of the calendar month, plus on activation | Structurally opaque or long-horizon probes |

Operating rules:

- **Auto-upshift.** Any fire, or any external signal touching a probe's target, runs it this cycle
  and holds it at Tier D for 3 cycles. Upshift requires no approval.
- **Downshift is audit-only.** The sweep never downshifts. 10+ consecutive cycles without a fire is
  the audit's downshift threshold (Step 5c), never crossed for CRITICAL-BS probes below Tier E.
- **Monthly floor for everything.** No probe goes unrun longer than a calendar month.
- **Skipped probes stay visible.** List every skipped probe in `sweep_metadata.probes_skipped`
  (probe id, tier, one-clause reason). Absence of a card must be distinguishable from a null.
  This extends sweep metadata per the `reference_trends` precedent; the probe-schema contract
  files are not modified.
- **Canonical probe IDs.** Use the exact ID spelling in Appendix B. The PROBE-12' /
  PROBE-12-prime / PROBE-12p fragmentation in historical sweeps breaks fire-rate computation;
  do not add variants.

Interim assignments (verified fire rates over 19 sweeps, May 11 - June 8):

| Probe | Tier | Basis / activation condition |
|---|---|---|
| PROBE-11 (Russian settlement) | M | 0 fires / 5 runs; BS-9 sub-probes carry the Russia surface |
| PROBE-17 (Russian siloviki) | M | 0 fires / 11 runs; activation: any BS-9.1-9.5 signal; BS-9.3 Putin count checked at the monthly run |
| PROBE-18 (Eschatological) | E | 0 fires / 5 runs; activation conditions are the eschatology trigger-read conditions in CLAUDE.md reference table |
| PROBE-21 (Paine death-ground) | D, flagged | 0 fires / 11 partials: fire bar unreachable or misdefined; threshold recalibration at next /audit, cadence unchanged until then |
| All others | D | Fire rates 17-88%; no downshift case |

---

## Output Artifacts

Produce three artifacts after all probes complete. Formats are defined in `probes/probe-schema.md`.

1. **Probe sweep table** — one row per probe, status/confidence/trigger summary. Goes in the daily SITREP
   under "Appendix B Intelligence Probe Status."
2. **Trigger digest** — revision triggers fired, with proposed Appendix A edits. Feeds the auditor and
   the next SITREP's revision section.
3. **Gap log** — null/gap probes with source-ladder notes. Feeds Appendix B's blind-spot inventory at
   next audit. Three consecutive gap cycles on one probe escalates to the auditor.

---

## Anti-patterns

- Do not synthesize across probes inside a single finding card. Cross-probe synthesis is the SITREP
  composer's job.
- Do not treat null as "status quo confirmed." Null means no signal surfaced this cycle.
- Do not paraphrase Appendix B probe definitions back to the user.
- Do not exceed 5 search calls per probe. If signal is not found, log `gap` and move on.
- Do not let probe runs become news summaries. Stay keyed to the specific framework variable. If
  unrelated big news surfaces, note it for the auditor and continue.
- **Do not treat multi-outlet pickup as independent confirmation without provenance.** Cluster-laundering
  (one originating reporter, multiple downstream pickups) is not multi-source. The discount applies
  to the originating cluster, regardless of outlet count. See Step 3b.
- **Do not treat principal identification as settled on inherited framing alone.** When a fired trigger
  attributes a decision to a named principal, the alternative-principal hypothesis is required in the
  finding card's conflict_notes. See Step 7b.

---

## Calibration Check

After all cards are written, ask two questions in order:

1. **Trend-state question:** does the aggregate sweep output suggest any trend in
   `reference/strategic-trends.md` should transition state (VALIDATED ↔ CONTESTED ↔ DISCONFIRMED,
   or PENDING → VALIDATED)? Single-cycle evidence does not justify transitions; multi-cycle
   pattern does. If a transition is warranted, flag for the next /audit run, do not enact it
   inside the sweep.
2. **Thesis question:** does the aggregate probe output suggest the framework's central thesis
   is **holding**, **drifting**, or **breaking**?

- **Holding / drifting:** proceed to output artifacts.
- **Breaking:** do not overwrite the framework from within the runner. Flag the break, produce the
  trigger digest, and escalate to a synthesis revision request. The runner surfaces signal; it does not
  rewrite the framework.

The trend-state question precedes the thesis question because trend states are the multi-week
anchors against which thesis-level "drift" or "break" claims must be measured. A single-cycle
break read that contradicts every VALIDATED trend is almost certainly recency bias, not a thesis
break.
