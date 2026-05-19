# Iran 2026 — Geopolitical Intelligence Framework

Active analytical framework tracking the 2026 US-Iran conflict and its strategic aftershocks.

**Current status:** Day 81 | Gulf state troika halted scheduled May 19 US strike | 72-hour brake-decay window active | Fork B leading (20-30%, 30d) | Kinetic Escalation Composite 52-67% (30d)

---

## Repository Structure

```
geopol/
├── synthesis/              ← Versioned base framework (anchor document)
│   └── staging/            ← Pre-revision change manifests; archive/ for consumed manifests
├── sitreps/                ← Daily annexes (track drift, validate/revise assumptions)
├── probes/                 ← Intelligence probe schema + sweep outputs
│   ├── sweeps/             ← JSON probe sweep outputs per cycle
│   └── structural/         ← Single-node deep probes (non-routine, analyst-invoked)
├── appendix/               ← Appendix B blind-spot inventory; Appendix C methodology
├── output/                 ← Blog output artifacts (day-N.md, day-N-image-prompt.md)
│   └── blog/
└── reference/              ← Theoretical frameworks, tools, source lists
    └── tools/              ← Stage 1/2/3 analytical tool catalogs
```

---

## Workflow

1. **Probe sweep** → `probes/sweeps/sweep-YYYY-MM-DD.json`
2. **Daily SITREP** → `sitreps/day-N.md` (consumes probe sweep)
3. **Blind-spot audit** → patch against `appendix/appendix-b-blind-spots.md` (monthly or on trigger)
4. **Synthesis revision** → `synthesis/synthesis-vX-Y.md` (on framework rotation or 5+ annex accumulation)
5. **Blog transform** → `output/blog/day-N.md` + `day-N-image-prompt.md`, then copy to myblog inbox

---

## Key Documents

| Document | Purpose |
|---|---|
| `synthesis/synthesis-v4-0.md` | Current base framework — anchor for all analysis |
| `appendix/appendix-b-blind-spots.md` | Structural blind spots + probe directives (18 BSs, 20 probes) |
| `appendix/appendix-c-methodology.md` | Methodology provenance: bargaining theory, two-level games, system effects |
| `probes/probe-schema.md` | Probe output contract (markdown spec) |
| `reference/quality-sources.md` | Tiered source ladder |
| `reference/costly-signaling-framework.md` | Fearon-Slantchev theoretical apparatus |
| `reference/tripolar-realignment-whitepaper.md` | Tripolar reordering thesis; unaligned-middle dynamics |
| `reference/russia-pole-architecture.md` | Russia-pole veto-player map; succession typology |

**Latest operational outputs:**

| Output | File | Date |
|---|---|---|
| Synthesis | `synthesis/synthesis-v4-0.md` | May 18, 2026 |
| SITREP | `sitreps/day-81.md` | May 18, 2026 |
| Probe sweep | `probes/sweeps/sweep-2026-05-18.json` | May 18, 2026 |
| Blind-spot audit | `appendix/appendix-b-blind-spots.md` | May 19, 2026 (Day 82) |
| Blog | `output/blog/day-81.md` | May 19, 2026 |

---

## Framework Version History

| Version | Date | Key Change |
|---|---|---|
| v1.0 | Mar 2026 | Initial constraint-architecture model |
| v2.0 | Apr 2026 | Three constraint layers; faction misalignment as Layer 4 |
| v2.5 | Apr 2026 | Legal/procedural exit innovation |
| v2.6 | May 4, 2026 | Operational-doctrine level innovation; Fork A leading |
| v3.0 | May 8, 2026 | Fearon-Slantchev integrated; Fork B leading; Layer 5 PA-gap |
| v3.1 | pending | Trump-Xi trigger; Netanyahu principal-penetration; eschatological-coalition; HEU physical-state; multilateral E3/IAEA; Kinetic Escalation Composite |
| v4.0 | May 18, 2026 | Methodology correction: substrate-as-agent voice retired; materialist bargaining model with Bayesian updates; Gulf state troika brake mechanism (§5.25); Cooper T1 proxy-connectivity discount; Appendix C methodology provenance |

**Pending v4.1 triggers (post-May 20-21 outcomes):**
- §5.25 Gulf State Troika Brake Mechanism activation/decay
- Cooper T1 proxy-connectivity Layer 2 revision
- Ford (not Truman) CSG-10 factual patch in §1.2 and §3.1

---

## Blind Spot Inventory Summary

18 blind spots (BS-1a through BS-18). 20 standing weekly probe directives (PROBE-1 through PROBE-20).

**Critical (4):** BS-1b (Iranian internal economic transmission), BS-15 (US-side threshold and red-line), BS-16 (Eschatological-coalition domestic capture), BS-18 (Gulf state troika / unaligned-middle pivot capacity, added Day 82)

**High (3):** BS-1a (Iranian apex decision-making), BS-9 (Russian internal succession), BS-13 (Proxy-front operational connectivity)

Full inventory: `appendix/appendix-b-blind-spots.md`

---

*Analysis conducted via Claude claude.ai project. Daily annex cycle targets 0800 ET.*
