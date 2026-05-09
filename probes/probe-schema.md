# Iran 2026 Framework — Output Schema

*Shared output contract between the Probe Runner and Blind-Spot Auditor skills. Both skills read this; the SITREP composer (future skill) consumes outputs structured this way.*

---

## Probe finding card

One card per probe per cycle. Fixed format. No freelancing length.

```
PROBE-N | <probe short name>
Cycle: <YYYY-MM-DD>
Status: fired | partial | null | gap
Confidence: H | M | L
Sources: [<tier-1 source>, <tier-2 source>, ...]

Finding: <2-3 sentences. What surfaced or did not. Specific named-source quotes
if tier-1; characterized if tier-2; flagged as analysis if tier-3.>

Trigger match: <Appendix B framework revision trigger fired? yes/no/partial>
  If yes: <which trigger row, what specific framework variable moves, direction>
  If partial: <what would close the gap to a full match>

Discounts applied: <list any discount rules invoked>

Conflict notes: <if sources disagreed, where and which side has stronger sourcing>
```

### Status definitions

- **fired** — probe surfaced material signal that moves a framework variable. Trigger may or may not have fired in the formal Appendix B sense; what matters is that the probability matrix or assumption state needs adjustment.
- **partial** — signal surfaced but is below the threshold for confident framework movement. Worth logging, not worth revising on.
- **null** — probe ran, no relevant signal in the cycle window. Status quo is the finding.
- **gap** — probe could not reach the target signal due to source-ladder limitations. Distinguished from null because gap implies the source ladder is the problem, not the absence of news.

### Confidence definitions

- **H (High)** — multi-source tier-1 or tier-2, no significant discounts applied, no conflict between sources.
- **M (Medium)** — single-source tier-1, or multi-source tier-2/3, some discounts applied, minor conflict.
- **L (Low)** — single-source tier-2/3, significant discounts applied, or material source conflict unresolved.

L-confidence findings can still fire framework revisions if the trigger criteria are met, but the revision should be flagged provisional pending corroboration.

### Direction

When trigger match is yes, specify which framework variable moves and by how much:

```
Variable: <e.g., "Probability of negotiated off-ramp by mid-May">
Prior value: <e.g., "25%">
New value: <e.g., "18%">
Driver: <one-line reason from probe finding>
```

If the move is qualitative (e.g., assumption status changes from "validated" to "revised"), state it that way. Numbers are not always available; precision is not always available; do not invent it.

---

## Probe sweep summary table

Aggregated across all probes in a cycle. Goes into the daily SITREP.

```
| PROBE | Status | Confidence | Trigger Fired? | Variable Moved |
|-------|--------|------------|----------------|----------------|
| PROBE-1 Mojtaba | fired | M | yes (pattern confirmation) | A4 mechanism |
| PROBE-2 IRGC factional | partial | L | no | none |
| ... | | | | |
```

Keep cell content short. Detail lives in finding cards.

---

## Trigger digest

Sub-output for cycles where one or more triggers fire. Goes to the auditor at next audit; goes to the SITREP composer immediately for the daily annex.

```
TRIGGER FIRED: <Appendix B trigger row>
Source probe: PROBE-N
Confidence: H/M/L
Proposed Appendix A revision:
  Section: <e.g., "Section 3.4 Iranian Faction Structure">
  Edit: <specific text change or score change proposed>
Urgency: immediate | next cycle | next audit
```

Immediate urgency goes into the next SITREP. Next-cycle goes into a backlog the auditor reviews. Next-audit gets folded into structural Appendix B revisions.

---

## Gap log entry

Sub-output for probes returning "gap" status. Feeds the auditor.

```
PROBE-N gap: <one line on what could not be surfaced>
Cycles dark: <how many consecutive cycles this has been gap>
Sources tried: <which tiers were attempted>
Sources not yet tried: <if any>
Recommendation: <add new source / change frequency / accept structural opacity>
```

Three or more consecutive cycles of gap on the same probe escalates to the auditor as a candidate for new BS, source ladder revision, or structural opacity acknowledgment.

---

## Blind-spot record

Format for each BS in Appendix B. Auditor maintains; runner reads only the probe directives section.

```
### BS-N: <Short name> — <PRIORITY>

What we cannot see: <one paragraph framing>

Specific gaps:
- <bulleted list of discrete dark areas under this BS>

Confidence we have adequate visibility: <X-Y%>

Framework risk if blind spot breaks: <Low/Medium/Medium-High/High>
  <one-paragraph explanation of what moves if the BS surfaces>

Standing probe directive: PROBE-N (see runner skill)
  Frequency: <weekly/bi-weekly/monthly/event-triggered>
  Target signal: <bulleted list>
  What changes the framework: <bulleted list of conditional revisions>
  Sources to probe: <bulleted list of source ladder>
```

The probe directive section is the operational link to the Probe Runner skill. Keep it self-contained: the runner should be able to execute the probe by reading only this section, without consulting other parts of Appendix B.

---

## Audit delta record

Auditor output format for blind-spot scoring changes.

```
BS-N: <name>
Visibility: <prior%> → <new%>
Risk: <prior> → <new>
Priority: <prior> → <new>
Justification: <one line — what probe data or framework movement drove the change>
```

Skip BSs with no movement. The audit is the deltas, not the full inventory. The full inventory lives in Appendix B; the audit modifies it.

---

## Audit summary

Top-of-audit narrative, three to five sentences. Frames at the epistemic level:

- What did we learn about what we know?
- What did we learn about what we cannot know?
- Did the framework's confidence architecture move, and in which direction?
- Are we more, less, or differently exposed than at last audit?

This is the executive summary of the audit, not a list of changes. Lists go in the delta records.

---

## Notes on stability

This schema should not change every cycle. Schema churn breaks the contract between skills and forces the SITREP composer to re-learn parsing each time. Propose schema changes as a discrete task, not as a side effect of a probe or audit run. If a probe finding cannot fit the schema, that is information about the schema's limits, not license to ad-hoc the format.
