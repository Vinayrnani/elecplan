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
6. [x] Applied neutral-direct pole reduction to Page-2 (4P→3P ×4, 3P→2P ×2, 2P→1P ×2); neutral bypasses MCBs to Neutral Link; removed neutral pass-through wires 63 & 70; updated box mod-count labels; RCCB/changeover/RCBO left untouched.

## Rules
- Never compress context.
- Update REQUIREMENTS.md for every change or new requirement; refer to it when context is lost.
- Commit and push to GitHub by default after every change.
- draw.io must open correctly in app.diagrams.net via GitHub.

## Recent changes (wire numbering)
- Removed all 178 old edge labels and re-added 164 labels (82 source + 82 target) with perpendicular offset (-12px) to avoid overlapping arrow heads.
- Labels positioned at x=0 (source exit) and x=1 (target entry) with y=-12 perpendicular offset.
- Commit 886e1ee pushed to GitHub.

## Recent changes (sub-DB box labels with mod counts)
- Updated Box 4, 5, 6 labels to include modular (mod) counts matching Box 1-3 format.
- Box 4: 40A 4P RCCB + 9x 20A 1P MCB + 6A 1P MCB = 13 Mod
- Box 5: 25A 4P MCB + 5x 6A/16A 1P MCB = 9 Mod
- Box 6: 20A 1P MCB + 25A 3P MCB + 16A 2P RCBO = 6 Mod
- Commit 3211213 pushed to GitHub.

## Recent changes (standard mod width in box labels)
- Added @17.5mm standard mod width specification to all 6 box labels (Box 1-6).
- Standard DIN rail module = 17.5mm (Schneider, ABB, Legrand, Siemens).
- Commit b5498d8 pushed to GitHub.

## Recent changes (Way notation for all boxes)
- Added Way notation to Box 4 (13-Way), Box 5 (9-Way), Box 6 (6-Way) labels.
- All 6 boxes now follow "X-Way Box N: Name" format.
- Commit 40a4a63 pushed to GitHub.

## Recent changes (standard enclosure sizes)
- Changed Box 4 from 13-Way to 16-Way (standard size, 13 mods used)
- Changed Box 5 from 9-Way to 12-Way (standard size, 9 mods used)
- Box 6 stays 6-Way (standard size, 6 mods used)
- Standard DB enclosure sizes: 4, 6, 8, 12, 16, 24, 36, 48, 72 Way
- Commit 28a6555 pushed to GitHub.

## Recent changes (street light MCB consolidation)
- Removed Main St L MCB, kept single Main St MCB (renamed from Main St R)
- Removed associated Main Lane Left street light icon
- Each street light MCB now labeled: 8 lights x 36W (288W = 1.25A, well within 6A)
- MCBs: North St, Main St, Gate Lights (each 6A, 8 lights)
- Box 5 updated: 25A 4P MCB + 4x 6A/16A 1P MCB = 8 Mod used
- Commit 7207c24 pushed to GitHub.

## Recent changes (neutral-direct pole reduction — COMPLETE)
- Neutral fully bypasses all MCBs to Neutral Link (Page-2). Removed ALL neutral-to-MCB wires: changeover N→MCB 35 (wire 57), MCB 35→serp_N_1 (wire 72), serp_N_2→MCB 11 (wire 77), MCB 11→RCCB N (wire 81), serp_N_3→MCB 82 (wire 87), MCB 82→MCB 90 neutral pass-through (wire 94), serp_N_4→MCB 141 (wire 186).
- Fixed changeover Y/B entry re-anchoring after 4P→3P shape change (wires 55, 56).
- Added changeover N → Neutral Link -226 (wire 83) and Neutral Link → serp_N_1 through serp_N_11 (wires 84-94) across both Neutral Link groups (-225 extended to 12 terminals, -137 existing).
- Pole counts already applied: 4P→3P (×4: 63A/40A/25A/25A MCB), 3P→2P (×2: 25A MCB), 2P→1P (×2: 32A/20A Amphi).
- Previously removed: neutral pass-through wires 63 & 70. Box mod labels: Box 1=7, Box 3=13, Box 5=10, Box 6=5 Mod. OV/UV + SPD = OPTIONAL / NOT INSTALLED.
- Conflicts untouched: RCCB (4P, RCD needs neutral through sensor), changeover (4P, neutral must switch), RCBO pool pump (2P).
- XML validated: well-formed, all 11 serp_N terminals have exactly 1 incoming edge from Neutral Link, 0 edges target any MCB N position.
- Committed & pushed commit 0e477e4 to main.
