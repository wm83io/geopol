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

1. **Anchor synthesis:** read highest-versioned file in `synthesis/`
   Record current probability values and assumption states — probes are deltas against this baseline.
2. **Appendix B:** read `appendix/appendix-b-blind-spots.md`
   This is the authoritative probe spec. Execute only probes listed here.
3. **Last SITREP:** read highest day-number file in `sitreps/`
   Establishes current operational baseline.
4. **Output schema:** read `probes/probe-schema.md`
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

---

## Probe Rotation and Frequency

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

---

## Calibration Check

After all cards are written, ask: does the aggregate probe output suggest the framework's central thesis
is **holding**, **drifting**, or **breaking**?

- **Holding / drifting:** proceed to output artifacts.
- **Breaking:** do not overwrite the framework from within the runner. Flag the break, produce the
  trigger digest, and escalate to a synthesis revision request. The runner surfaces signal; it does not
  rewrite the framework.
