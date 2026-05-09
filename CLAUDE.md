# CLAUDE.md — Iran 2026 Geopolitical Framework

Instructions for Claude Code operating on this repository.

---

## Role

File operations layer for the Iran 2026 geopolitical intelligence framework.
Analytical work is conducted in the claude.ai project (canonical source).
This repo is the versioned output store. Do not revise analytical content without explicit instruction.

---

## Repo Structure

```
synthesis/          ← Base framework. Versioned. synthesis-vX-Y.md naming.
sitreps/            ← Daily annexes. day-N.md or day-N-am/pm.md naming.
probes/sweeps/      ← JSON probe sweep outputs. sweep-YYYY-MM-DD.json naming.
appendix/           ← Appendix B. Single file, patched in-place. Version in git history.
reference/          ← Theoretical frameworks and source lists. Do not modify.
reference/tools/    ← Stage tool catalogs. Do not modify without instruction.
```

---

## File Naming Conventions

| Type | Convention | Example |
|---|---|---|
| Synthesis | `synthesis-vX-Y.md` | `synthesis-v3-1.md` |
| SITREP | `day-N.md` or `day-N-am.md` / `day-N-pm.md` | `day-71.md` |
| Probe sweep | `sweep-YYYY-MM-DD.json` | `sweep-2026-05-09.json` |
| Appendix B | `appendix-b-blind-spots.md` (single file, no versioning in filename) | — |

---

## Permitted Operations

- Write new SITREP files to `sitreps/`
- Write new probe sweep JSON to `probes/sweeps/`
- Write new synthesis versions to `synthesis/` (never overwrite, always new version file)
- Patch `appendix/appendix-b-blind-spots.md` in-place (git history tracks versions)
- Read any file for context

## Do Not

- Modify `reference/` or `reference/tools/` without explicit instruction
- Overwrite existing synthesis or SITREP files
- Delete files
- Modify `CLAUDE.md` or `README.md` without explicit instruction

---

## Probe Sweep JSON Schema

Canonical schema lives at `probes/probe-schema.md`.
JSON sweeps must validate against `probes/probe-schema-json.json`.

Key fields per finding card:
```json
{
  "probe_id": "PROBE-1",
  "probe_name": "Mojtaba functional status",
  "cycle_date": "2026-05-09",
  "status": "fired|partial|null|gap",
  "confidence": "H|M|L",
  "sources": [],
  "finding": "",
  "trigger_match": true,
  "trigger_detail": "",
  "variable_moved": {
    "variable": "",
    "prior_value": "",
    "new_value": "",
    "driver": ""
  },
  "discounts_applied": [],
  "conflict_notes": ""
}
```

---

## Context Primers

When operating on this repo, read these files first for analytical context:
1. `synthesis/synthesis-v3-0.md` — current base framework
2. `appendix/appendix-b-blind-spots.md` — active blind spots and probe directives
3. Most recent file in `sitreps/` — last known state

The synthesis is the anchor. All SITREP and probe output is delta against it.
