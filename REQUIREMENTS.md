# Project Requirements — elecplan (Electrical Planning)

## Repo
- GitHub: https://github.com/Vinayrnani/elecplan (PUBLIC)
- Local: /home/ubuntu/projects/elecplan
- Branch: main

## Skills (installed in OpenCode)
- `drawio` — general draw.io XML diagramming
- `engineering` — professional electrical schematics / electrical planning stencils

## Files
- drawings/farmhouse_electrical_sld_16way_v4.drawio — refined SLD: Page-1 Master Electrical SLD kept intact; Page-2 Panel Layout & Sub-DB Details restored with REAL electrical symbols (MCBs, 63A 4P changeover, generator inlet 32A 5-Pin IP67, OV/UV protector, Type-2 SPD, 100A busbar, Serplex split hubs, earth pit, sub-DBs) uniformly re-positioned to eliminate negative coordinates (min top-level 60,60) while preserving all relative positions; all 155 vertices / 82 edges preserved
- drawings/Central_DB_SLD.drawio / .pdf / .svg — legacy Central DB SLD
- SKETCHUP_MODEL_KNOWLEDGE.md — project knowledge + summary of changes
- REQUIREMENTS.md — this file (update for every change/new requirement)

## Open tasks
1. [x] Restore page-2 real electrical setup (MCB/changeover/DB) + de-congest grid + fix negative coords; keep page-1
2. [ ] Create custom BOM as Excel sheet (.xlsx) — user said "no excel for now"
3. [x] Push draw.io to GitHub on every change
4. [x] Write summary of changes in SKETCHUP_MODEL_KNOWLEDGE.md (project knowledge)

## Rules
- Never compress context.
- Update REQUIREMENTS.md for every change or new requirement; refer to it when context is lost.
- Commit and push to GitHub by default after every change.
- draw.io must open correctly in app.diagrams.net via GitHub.
