# SketchUp Model Knowledge — Final Electrical Planning Correction

Source model: https://app.sketchup.com/share/tc/asia/6y6IdXm9Sb0?source=web&stoken=vmJI3GUsBvwDjpsPO6xulZbYtf9okO67ONPTfhGAJd_wMAch7h1ANbeGuR07Bghu

## Tags / Layers (from Tags panel)
1. 10 Sqmm 1 Core 4 Cables
2. 16 sqmm Armoured cable
3. 4 sqmm Street light cable
4. 6 Sqmm 2 Core Cable
5. AmphiTheater
6. Boundary
7. Boundary Dimensions
8. Boundary Poles
9. Containers
10. Current Trenches
11. Markings
12. Street Lights
13. Swimming Pool

## Boundary / Site Dimensions (from model)
- Top edge: ~186'-5 1/2"
- Top-right edge: ~15'-6 1/2"
- Left-center vertical: ~15'-9 1/2" (or 153' 9 1/2" depending read)
- Bottom edge: ~186'-3 1/2"
- Bottom: ~15'-4"
- Right-edge vertical stack (partial): ~12', 16', 20', 30' segments
- Bottom-right callout: Power Source (Meter)

## Trench / Cable Labels Observed (model)
South feeder (16 sqmm armoured):
- 40 m — 4 Core 16sqmm Armoured

Container feeder (10 sqmm single-core, 4 cables):
- 36 m — 1 Core 10 Sqmm, 4 Cables
- 9 m — 1 Core 10 Sqmm, 4 Cables
- Total ≈ 45 m (matches locked-in ~45 m)

North shed (6 sqmm 2-core):
- 45 m — 2 Core 6 Sqmm
- 8 m — 2 Core 6 Sqmm (branch/segment)

Street-light / pool / projector / pathway (4 sqmm 2-core segments):
- 8 m, 33 m, 26 m, 5/58 m, 21 m, 8 m, 13 m, 25 m, 17 m, 56 m, 55 m, 5 m, 12 m, 21 m (right-side segments), 9 m / 36 m are 10 sqmm not 4 sqmm

Note: several labels are partially obscured by viewer overlays; lengths are model-annotated and approximate (model based on satellite imagery).

## Cross-Verification vs Locked-In Layout
| Locked-in item | Locked length | Model label(s) | Status |
|---|---|---|---|
| South Feeder 16 sqmm armoured | 40 m | 40 m 4 Core 16sqmm Armoured | Match |
| Container Feeder 10 sqmm (5x) | ~45 m | 36 m + 9 m (1 Core 10 Sqmm, 4 Cables) | Match (~45 m) |
| North Shed 6 sqmm | ~48 m | 45 m 2 Core 6 Sqmm (+8 m branch) | Close (~45–53 m) |
| East/Pool/Projector/Street lights 4 sqmm | ~47 m trunk + drops | Multiple 4 sqmm 2-core segments | Segmented |

## Finalized Bill of Materials (BOM)

### Cables (100% Aluminium, IS 7098 / IS 694)
| Item | Spec | Qty | Notes |
|---|---|---|---|
| South feeder cable | 16 sq.mm 4-Core Al Armoured | 40 m (50 m coil purchased) | Direct-buried on sand bed |
| Container feeder wires | 10 sq.mm 1-Core Al | 5 × 45 m (R,Y,B,N,E) | In 1.25" HDPE pipe |
| Container feeder comms | Cat6 | 45 m | In same 1.25" HDPE pipe |
| North shed cable | 6 sq.mm 2-Core Al | 48 m (model ~45 m) | In 3/4" HDPE pipe |
| North shed earth | No. 8 SWG GI earth wire | 48 m | In same 3/4" HDPE pipe |
| Street-light / pool / projector / pathway cable | 4 sq.mm 2-Core Al | ~200 m total (model segments) | Loop-in drops, no buried T-joints |
| Room drops (container) | 4 sq.mm 2-Core Al | Per room (1/2" drops) | Qty by room count |
| Stage sideboards | 6 sq.mm 2-Core Al | 2 runs | 16A industrial sockets |

### Conduit / Pipes
| Item | Spec | Qty |
|---|---|---|
| Container feeder pipe | 1.25" HDPE | 45 m |
| North shed pipe | 3/4" HDPE | 48 m + two 90° pull boxes |
| East trunk pipe | 3/4" HDPE | 47 m |
| Light pole drops | 1/2" HDPE loop-in/out | Per pole |

### Central Main DB (free-standing on MS/GI pedestal)
| Item | Rating |
|---|---|
| Manual changeover switch | 63A 4-Pole (with 32A 5-Pin 415V IP67 gen inlet) |
| Auto over/under voltage protector | 270V high cutoff, auto-reclose |
| Surge protection (SPD) | Type-2, 40kA, 4-Pole |
| Busbar | 100A |
| Container sub-DB feeder MCB | 40A 4P |
| North shed feeder MCB | 32A 2P |
| Pool pump RCBO | 16A 2P, 30mA |
| Projector & sound MCB | 16A 2P |
| Street light circuits MCB | 3 × 6A/10A SP |
| Pathway lights MCB | 1 × 6A/10A SP |
| ESP32 SMPS & sensors MCB | 1 × 6A SP |

### Container Backside Sub-DB
| Item | Rating |
|---|---|
| RCCB | 40A 4P, 30mA |
| Earth electrode | 3 m GI earth pipe bonded to container chassis |
| Room circuits | 4 sq.mm 2-Core Al per room (1/2" drops) |
| Stage sideboards | 2 × 16A industrial sockets on 6 sq.mm 2-Core |

### Earthing
| Item | Spec | Qty |
|---|---|---|
| GI earth pipe | 3 m | 1 (container) |
| GI earth wire | No. 8 SWG | 48 m (North trench) |

### Internal DB wiring
- 10 sq.mm / 6 sq.mm flexible multi-strand copper jumpers with bootlace ferrules
- Bimetallic / pin lugs everywhere (Al-to-Cu transitions)

### Breaker summary (all C-curve, 10kA, no MCCBs)
- 63A 4P changeover
- 40A 4P MCB (container feeder)
- 32A 2P MCB (north shed)
- 16A 2P RCBO 30mA (pool pump)
- 16A 2P MCB (projector & sound)
- 6A/10A SP MCB × 5 (street lights ×3 + pathway ×1 + spare as needed)
- 6A SP MCB (ESP32 SMPS & sensors)
- 40A 4P 30mA RCCB (container sub-DB)

---

## Summary of Changes — draw.io Refinement (farmhouse_electrical_sld_16way_v4.drawio)

**Date:** 2026-11-15
**Repo:** https://github.com/Vinayrnani/elecplan (PUBLIC)
**File:** drawings/farmhouse_electrical_sld_16way_v4.drawio

### What changed (2026-11-15 — accept remote state a3f88cb + fix page-2 rendering)
- Accepted remote state (commit a3f88cb): Page-1 removed, Page-2 intact (155 vertices / 82 edges) with real electrical symbols (MCBs, 63A 4-Pole manual changeover, generator inlet 32A 5-Pin IP67, OV/UV protector 63A 4P, Type-2 SPD 40kA, 100A tinned copper busbar R/Y/B/N/E, central earth pit, Serplex 11x2-Way split hubs #1 R&Y and #2 B&N, Container/North East/Amphi/Shed/Outdoor sub-DBs). Page-2 re-serialized by draw.io web with new cell IDs.
- FIXED negative coordinates: uniformly translated all top-level cells so min top-level x,y → 60,60 (27 vertices were off-canvas causing 'blank page' appearance). Relative layout preserved.
- FIXED dangling edge bNfMxfX9K-qKM2XH7_Ha-55: added missing exitX=0.5;exitY=0 (was an open/disconnected wire).
- FIXED all 161 edge waypoints: shifted by (142.5, 440) to match the node coordinate shift (were at old pre-shift coordinates causing wires to route to wrong places).
- Overlapping edge groups already staggered (different exit/entry points) — no change needed.
- All 82 edges have valid source/target references.

### Status
- XML validated (well-formed, 1 diagram Page-2; 155 vertices / 82 edges; 0 top-level negative coordinates).
- Committed and pushed to GitHub (main branch).
- Opens in draw.io web via: https://app.diagrams.net/?github=Vinayrnani/elecplan&file=drawings/farmhouse_electrical_sld_16way_v4.drawio

### Recent changes (draw.io Page-2 wire routing fix)
- Fixed all Serplex 11x2 module wire connections to use vertical exit/entry points (straight up or down).
- 5 edges updated: 189 (entryY 0.004→0), 190 (exitX 1→0.5, exitY 0.5→1, entryY 0.004→0), 195/198/199 (exitX 0→0.5, exitY 0.5→0, with 198 re-routed downward to avoid crossing terminal R5).
- No wire now crosses any Serplex module interior; no overlapping segments (verified).
- Commit d9bd626 + follow-up fix pushed to GitHub.
- Installed `electrical` and `electrical-engineering` skills for professional electrical planning.

### Pending
- Custom BOM Excel sheet (.xlsx) — deferred per user ("no excel for now").
- Awaiting your instructions on what updates to make next to Page-2.

