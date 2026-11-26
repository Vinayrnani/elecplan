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

## Current approved MCB schedule (supersedes older pole/curve notes above)
Validated with electrical skills and IEC 60898 trip curves for the ACTUAL loads — NOT the user's purchase list:
- All inverter ACs (3-star 1.5T, max ~10.6A each) → B curve is sufficient everywhere except fixed-speed pumps.
- Main: 3 Pole 63 A MCB B Curve (neutral bypasses MCBs — 4P symbol corrected to 3P).
- Container feeder: 3 Pole 32 A MCB B Curve; 10 sqmm Al derated ~28–32A. Worst phase = 2 inverter ACs (~21A max) + ONE shared 2 kW geyser (8.7A) ≈ 30A.
- Box 4 incomer: 3 × 1P 32 A MCB B Curve (one per phase) — the old 1-pole 40A symbol was wrong and was split into three 1P breakers. Box 4 has only 4 rooms + 2 stage circuits active; Container South/West circuits removed.
- Outdoor feeder/distribution: 3 Pole 25 A MCB B Curve ×2 (labels corrected from 1P to match real 3-phase wiring/symbols).
- North-East/Amphi feeders: 2 Pole 25 A MCB B Curve ×2 (labels corrected from 1P to match real 2-pole wiring/symbols).
- Shed feeder: 1P 32 A MCB B Curve. Rooms 1–4 + Stage L/R: 20A 1P MCB B Curve. Street lights + inverter line: 6A 1P MCB B Curve.
- Fixed-speed pumps need C curve: pump (1.5 HP submersible) 16A 1P C; pond pump 10A 1P C; swimming pool pump 16A 1P+N 30 mA RCBO C.
- Shared geysers: one 2 kW per two rooms; each needs its own dedicated 16A 1P B-curve circuit (AC + geyser on one 20A MCB would be ~19A — too tight).
- Future South/West container extension: run a separate feeder from the Main DB; do NOT tee off Rooms 1–4 (feeder already ~30A worst phase).
- RCCB still optional/not used; 16A pool RCBO stays; changeover/OV/UV/SPD remain OPTIONAL / NOT INSTALLED.

## Recent changes (box arrangement + 4P main)
- User can fit the 4P main MCB + 2 Serplex units in one 16-way box → Box 2 is now the single Main Distribution Board: 63A 4P B-curve main [4 Mod] + 2x Serplex 11x2 [12 Mod] = 16 Mod @17.5mm.
- Main restored from 3P to 63A 4P with phase + neutral through the breaker: incoming N from generator, outgoing N to Serplex N bar and Neutral Link; Box 1 no longer contains the main.
- Box 1 is now ONLY the optional changeover + OV/UV + Type-2 SPD enclosure, dashed and marked OPTIONAL / NOT INSTALLED, placed at top-left.
- Box 3 (Outgoing Feeders) moved directly below Box 2 in the same column; Box 4/5/6 unchanged. Wire routing recomputed for the moved feeder box.
- Label overlap cleanup: small breakers labelled beside the device, MCCBs below with white label background; redundant box-name text cells removed; schedules A/B/C provide full breaker details. No breaker-to-breaker label overlap in rendered PNG.

## Recent changes (Cu/Al wire material rule)
- User rule: wires inside DB/boxes = copper; all underground/field cables = aluminium.
- Relabeled 15 underground/field wires from Cu to Al with Al-correct gauges: main incoming 3x 16mm²Al, container feeder 3x 10mm²Al, North-shed feeder 3x 6mm²Al, Amphi feeder 2x 6mm²Al, street-light/pump field wires 4x 4mm²Al.
- The 3 main-incoming wires (Ha-54/55/56) feeding the 63A MCB relabeled 16mm²Al per user ('main incoming is 16mm² aluminium'); R/Y/B outgoing from 63A MCB to Serplex stay 16mm²Cu (internal panel link).
- 37 internal panel links remain copper (63A=16, 40A=10, 32A=6, 25/20A=4, 16A=2.5, 10/6A=1.5 mm² Cu).
- Page-2: 313 vertices / 84 edges, XML valid (15 Al + 37 Cu labeled wires).
## Recent changes
- Replaced 63A 1P MCB (incoming main) with 63A 4P MCB (Main). Changeover switch (amiciSmart) marked OPTIONAL/NOT INSTALLED (future). Combined into one 16-way box: 63A 4P MCB Main [4 Mod] + 2x Serplex 11x2 [12 Mod] = 16 Mod. 6 wires reconnected (3 incoming 16mm² Al + 3 outgoing 16mm² Cu R/Y/B). Removed redundant 63A 1P MCB.
- Added copper gauge labels to all feeder wires in Page-2 (52 wires labeled). Gauge sized to the breaker the wire feeds: 63A→16mm²Cu, 40A→10mm²Cu, 32A→6mm²Cu, 25A/20A→4mm²Cu, 16A→2.5mm²Cu, 10A/6A→1.5mm²Cu. Incoming R/Y/B phase wires from 63A MCB→16mm²Cu. Existing phase/wire-number labels preserved (appended). 32 internal busbar/fuse/neutral-link wires without a breaker rating left as-is.
- Fixed Page-2 wire routing inside Serplex 11x2 modules: the 5 previously horizontal Serplex edges now use vertical exit/entry points (exitY 0 or 1 instead of 0.5; entryY 0 instead of 0.004). No wire now crosses any module interior; no overlapping segments. Commit d9bd626 + follow-up fix.
- Added wire numbers 1-82 to all 82 edges, with labels visible at both source (x=0.05) and target (x=0.95) ends. Commit 6eb0477.
- Installed `electrical` and `electrical-engineering` skills for professional electrical planning.

## Recent changes (single-pole breaker optimisation)
- Converted all multipole MCBs to single pole for cost saving. Kept ONLY: 63A 4P changeover, 3 Pole 32A container feeder main DB, and 16A RCBO (pool — user confirmed RCBO stays).
- 63A 3P incoming MCB → 1 Pole 63A; 25A 3P ×2 → 1 Pole 25A ×2; 25A 2P ×2 (Amphi) → 1P 25A ×2; 40A 4P RCCB → 1 Pole 40A MCB (RCCB optional / not used — user: "Not using any rccb now all they are optional. But RCBo is there").
- Box mod-count labels updated: Box1 63A 1P 1 Mod; Box3 10 Mod; Box4 12 Mod; Box5 6 Mod; Box6 4 Mod.
- 63A 4P OV/UV remains an OPTIONAL / NOT INSTALLED note only.

## Recent changes (container feeder breaker 40A → 32A 3P)
- Container feeder cable = 10 sqmm 1C Al PVC ×5 in ONE buried HDPE conduit, 45 m → derated ampacity ~28–32A (grouping + buried + warm soil).
- A 40A breaker would not protect this cable → changed container feeder MCB from "3 Pole 40 A MCB C Curve" to "3 Pole 32 A MCB C Curve" in the draw.io diagram; Box 3 label updated "40A 3P" → "32A 3P".
- Added "CURRENT SETUP vs ACTUALLY SUPPORTED" comparison table to SKETCHUP_MODEL_KNOWLEDGE.md audit section.
- Pole reduction to 3P/1P was intentional (neutral not needed) — NOT a defect.

## Open tasks
0. [x] Container feeder breaker 40A → 32A 3P (matches derated cable) + current-vs-supported table
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
