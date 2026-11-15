# Project Requirements — elecplan (Electrical Planning)

## Repo
- GitHub: https://github.com/Vinayrnani/elecplan (PUBLIC)
- Local: /home/ubuntu/projects/elecplan
- Branch: main

## Skills (installed in OpenCode)
- `drawio` — general draw.io XML diagramming
- `engineering` — professional electrical schematics / electrical planning stencils
- `electrical` — electrical systems and applications (planning installations, wiring, equipment selection)
- `electrical-engineering` — electrical engineering fundamentals and design (circuits, power systems, equipment spec)

## Files
- drawings/farmhouse_electrical_sld_16way_v4.drawio — Page-1 removed (per remote state a3f88cb); Page-2 Panel Layout & Sub-DB Details with REAL electrical symbols (MCBs, 63A 4P changeover, generator inlet 32A 5-Pin IP67, OV/UV protector, Type-2 SPD, 100A busbar, Serplex split hubs, earth pit, sub-DBs). Negative coordinates fixed (uniform shift so min top-level x,y → 60,60; relative layout preserved). Dangling edge bNfMxfX9K-qKM2XH7_Ha-55 fixed (added exitX=0.5;exitY=0). All 155 vertices / 82 edges preserved; re-serialized by draw.io web with new cell IDs.
- drawings/Central_DB_SLD.drawio / .pdf / .svg — legacy Central DB SLD
- SKETCHUP_MODEL_KNOWLEDGE.md — project knowledge + summary of changes
- REQUIREMENTS.md — this file (update for every change/new requirement)

## Recent changes
- Fixed Page-2 wire routing inside Serplex 11x2 modules: the 5 previously horizontal Serplex edges now use vertical exit/entry points (exitY 0 or 1 instead of 0.5; entryY 0 instead of 0.004). No wire now crosses any module interior; no overlapping segments. Commit d9bd626 + follow-up fix.
- Added wire numbers 1-82 to all 82 edges, with labels visible at both source (x=0.05) and target (x=0.95) ends. Commit 6eb0477.
- Installed `electrical` and `electrical-engineering` skills for professional electrical planning.

## Open tasks
1. [x] Accept remote state (Page-1 removed, Page-2 intact with real electrical symbols)
2. [x] Fix Page-2 negative coordinates (uniform shift min top-level x,y → 60,60)
3. [x] Fix dangling edge bNfMxfX9K-qKM2XH7_Ha-55 (added exitX=0.5;exitY=0)
4. [x] Fix Serplex module wire routing (vertical exits/entries, no crossings)
5. [ ] Create custom BOM as Excel sheet (.xlsx) — user said "no excel for now"
6. [ ] Awaiting user instructions on what updates to make next to Page-2

## Rules
- Never compress context.
- Update REQUIREMENTS.md for every change or new requirement; refer to it when context is lost.
- Commit and push to GitHub by default after every change.
- draw.io must open correctly in app.diagrams.net via GitHub.
