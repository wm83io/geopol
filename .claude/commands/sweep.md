---
description: Execute the Iran 2026 probe cycle against Appendix B and write a sweep JSON
---

# Iran 2026 — Probe Runner

Executes the weekly probe cycle against Appendix B's blind-spot inventory. Produces structured output
consumed by the SITREP composer and auditor skills.

**Output schema:** `probes/probe-schema.md` — read before writing any finding card.

---

## Pre-flight

Load into working context before any probe runs. All paths are relative to the repo root.

1. **Strategic trends baseline:** read `reference/strategic-trends.md` in full FIRST. The trend
   state table is the multi-week anchor for this cycle's findings. Each fired trigger this
   sweep produces must be classified against current trend states at Step 6.
2. **Anchor synthesis:** read highest-versioned file in `synthesis/`
   Record current probability values and assumption states — probes are deltas against this baseline.
3. **Appendix B:** read `appendix/appendix-b-blind-spots.md`
   This is the authoritative probe spec. Execute only probes listed here.
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

### Step 3b — Source-provenance trace (MANDATORY for every multi-outlet anonymous claim)

The tier ladder rates outlet quality, not source independence. Multi-outlet pickup of the same originating reporter or anonymous-source cluster is cluster-laundering, not independent confirmation.

For each finding sourced to "multiple outlets" with anonymous attribution, record in the finding card's `discounts_applied` field:

1. **Originating reporter / outlet.** Who broke the story? Which other outlets are wire-pickups or cite the originator?
2. **Source-cluster identity.** "Anonymous senior Iranian sources" across 5 outlets = 1 source cluster, not 5 sources.
3. **Independence test.** Are there genuinely independent anonymous clusters (different sourcing language, different outlet ecosystems) reporting the same finding? If yes, partial mitigation of the standing -50% discount. If no, full discount applies regardless of outlet count.

Examples of cluster-laundering to watch for:
- Haaretz lead → Reuters wire → geo.tv / Al Arabiya / Daily Sabah / Times of Israel pickup = 1 cluster
- CNN US-officials report → Axios corroboration "from same call" = 1 cluster
- ISW assessment → multiple T3 outlets summarizing ISW = 1 cluster

When the same originating cluster appears in 3+ cycles without a distinct corroborating cluster, flag for `/premortem` source-cluster-collapse review.

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

### Step 7 — Reference-trend cross-check (MANDATORY for every fired trigger)

For every probe that fires (status `fired` or trigger digest entry generated), name which trend in
`reference/strategic-trends.md` the finding advances, holds, or contradicts. Apply the discipline:

- **Finding advances a VALIDATED trend:** standard trigger digest entry; no special handling.
- **Finding holds a VALIDATED trend:** standard trigger digest entry; note the consistency in the
  finding card's `conflict_notes` field if surprise was high or counter-hypothesis was live.
- **Finding contradicts a VALIDATED trend on single-cycle evidence:** flag in trigger digest as
  `urgency: next_audit` regardless of operational urgency; require multi-cycle confirmation before
  proposing the BS mechanism revision the contradiction would imply. Log the divergence in the
  finding card's `conflict_notes` with a one-line citation of which trend and which reference
  source predicted the opposite. Do NOT propose mechanism revisions to Appendix A on the basis
  of single-cycle contradiction of a VALIDATED trend.
- **Finding contradicts a VALIDATED trend on multi-cycle evidence (this cycle + at least one prior
  cycle):** elevate to `urgency: immediate`; propose the trend-state transition (VALIDATED →
  CONTESTED) in the trigger digest; this becomes an audit-cycle item that may also justify a BS
  mechanism revision.
- **Finding closes a PENDING-trend instrumentation gap:** flag in trigger digest for audit
  promotion of the trend to VALIDATED.

The rule exists because the Day 77 → Day 83 sequence demonstrated that single-cycle ISW analytical
evidence (tier-3 single-source) produced a BS-12 "apex-veto" mechanism revision against T3
Fearon-Slantchev prediction; Day 83 Vahidi silence-break confirmed the trend, not the revision.
Six cycles of mis-stated PA-gap mechanism resulted. This step blocks the failure mode.

Add a `reference_trends` array to the sweep JSON's `sweep_metadata` block listing the trends
relevant to this cycle and the cycle's net effect on each (`advance` / `hold` / `contradict_single`
/ `contradict_multi` / `close_pending_gap`).

### Step 7b — Principal-validation cross-check (MANDATORY for every fired trigger involving a named principal)

The framework treats specific named individuals as principals (Mojtaba, Trump, Netanyahu, Vahidi, MBS, Munir, Xi, Putin). Each principal identification was inherited from early media framing; the discipline of "actors as subjects of choice verbs" makes principal-misidentification more dangerous, not less, because the model commits to the named agent.

For every fired trigger where a named principal is the subject of a choice or decision claim, record in the finding card's `conflict_notes` field:

1. **Alternative principal hypothesis.** Who else could be making this decision? Examples:
   - Mojtaba HEU directive: alternative = SNSC consensus body; alternative = Ali Khamenei (if not incapacitated); alternative = IRGC vertex (Salami).
   - Trump A1 oscillation: alternative = unmodeled driver (financial exposure, family member, classified intel we don't have).
   - Netanyahu Penetration mechanism: alternative = IDF chief Zamir; alternative = Mossad chief.
2. **Discriminating evidence.** What signal in the cycle distinguishes the named principal from the alternative? If "behavior is consistent with the named principal having decided," that is curve-fitting, not validation.
3. **Confidence note.** If no discriminating evidence exists this cycle, mark the principal identification as `inherited, not validated this cycle`. After 4+ consecutive cycles without discriminating evidence on a load-bearing principal, flag for `/premortem` wrong-principal review.

This step blocks the failure mode where the framework treats a named principal as the apex / decision-maker on the basis of media framing alone. It does not require resolving the principal question every cycle; it requires not pretending the question is settled when discriminating evidence is absent.

Probe specs live in Appendix B. Do not maintain parallel definitions here. Frequency overrides:

| Probe | Default | Override |
|---|---|---|
| PROBE-1 through PROBE-8 | Weekly | — |
| PROBE-9 (Israeli internal) | Bi-weekly | — |
| PROBE-10 (WPA/constitutional) | Weekly through June 1, then monthly | — |
| PROBE-4 (London attribution) | Weekly first 3 weeks, then monthly if no confirmation | — |

If a trigger event fires on a skip week, run the probe regardless.

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
