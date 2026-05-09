# Iran 2026 — Geopolitical Intelligence Framework

Active analytical framework tracking the 2026 US-Iran conflict and its strategic aftershocks.

**Current status:** Day 71 | Operation Epic Fury concluded | MOU negotiation window active | Fork B leading (30-40%)

---

## Repository Structure

```
geopol/
├── synthesis/          ← Versioned base framework (anchor document)
├── sitreps/            ← Daily annexes (track drift, validate/revise assumptions)
├── probes/             ← Intelligence probe schema + sweep outputs
│   └── sweeps/         ← JSON probe sweep outputs per cycle
├── appendix/           ← Appendix B blind-spot inventory (audited separately)
└── reference/          ← Theoretical frameworks, tools, source lists
    └── tools/          ← Stage 1/2/3 analytical tool catalogs
```

---

## Workflow

1. **Probe sweep** → `probes/sweeps/sweep-YYYY-MM-DD.json`
2. **Daily SITREP** → `sitreps/day-N.md` (consumes probe sweep)
3. **Blind-spot audit** → patch against `appendix/appendix-b-blind-spots.md` (monthly or on trigger)
4. **Synthesis revision** → `synthesis/synthesis-vX-Y.md` (on framework rotation or 5+ annex accumulation)

---

## Key Documents

| Document | Purpose |
|---|---|
| `synthesis/synthesis-v3-0.md` | Current base framework — anchor for all analysis |
| `appendix/appendix-b-blind-spots.md` | Structural blind spots + probe directives |
| `probes/probe-schema.md` | Probe output contract (markdown spec) |
| `reference/quality-sources.md` | Tiered source ladder |
| `reference/costly-signaling-framework.md` | Fearon-Slantchev theoretical apparatus |

---

## Framework Version History

| Version | Date | Key Change |
|---|---|---|
| v1.0 | Mar 2026 | Initial constraint-architecture model |
| v2.0 | Apr 2026 | Three constraint layers; faction misalignment as Layer 4 |
| v2.5 | Apr 2026 | Legal/procedural exit innovation |
| v2.6 | May 4, 2026 | Operational-doctrine level innovation; Fork A leading |
| v3.0 | May 8, 2026 | Fearon-Slantchev integrated; Fork B leading; Layer 5 PA-gap |

---

*Analysis conducted via Claude claude.ai project. Daily annex cycle targets 0800 ET.*
