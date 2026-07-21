# Figma Reference Log

Four files in play (File 4 added 21 Jul 2026). None can be opened
passively — every value in design-tokens.md and components.md came from a
live, explicit extraction against a specific file key and node ID via the
Figma MCP connector.

Note: CLAUDE.md still says "Three Figma files in play" — that predates
File 4 and is now stale; update it if File 4 becomes a standing source.

## File 1 — BESTMED Design System (legacy component library)

URL base: https://www.figma.com/design/9XibHmB1A7hcflpo0wBeKx/BESTMED-Design-System
File key: 9XibHmB1A7hcflpo0wBeKx

Superseded as the source for design-tokens.md (no Variables layer, static
Styles only — see File 3). Still the source for component measurements
(Buttons, Badges) mapped into components.md, and for the medication
classification colours, which have no equivalent in File 3.

| Page | Node ID | Status |
|---|---|---|
| ✅ Colours | 1:1164 | Superseded by File 3 for neutral/semantic colour — still source for Medication classification colours |
| ✅ Typography | 1:1165 | Superseded by File 3 (Inter adopted) |
| ✅ Layout and Spacing | 1:1166 | Superseded by File 3 spacing scale |
| ✅ Buttons | 1:1167 | Extracted — measurements feed components.md |
| ✅ Badges | 744:43348 | Extracted — measurements feed components.md |
| ✅ Tables | 211:10497 | Component reference only — real row structure came from File 2 instead |
| ✅ Modals | 521:5069 | Not yet extracted |
| ✅ Input | 1:1169 | Not yet extracted |
| ✅ Header | 1:1168 | Not yet extracted |
| ✅ Footer | 1:1170 | Not yet extracted |
| ✅ Shadows | 423:6344 | Extracted |
| ↳ Medication Profile | 19644:95088 | No matching 1440-wide frame found — components only |

## File 2 — BestDOSE (the actual application)

URL base: https://www.figma.com/design/3mEBxpW3AU6agtPHiikZD5/BestDOSE
File key: 3mEBxpW3AU6agtPHiikZD5

Source for real screen layouts — page chrome, actual content structure,
confirmed pixel dimensions. Use this file, not the component libraries,
when a one-off exception to spec-only screen building is agreed per screen.

| Page | Node ID | Notes |
|---|---|---|
| ✨ Login | 3635:10699 | — |
| ✨ Dashboards | 54:26907 | — |
| ✨ Dose Rounds | 721:22367 | Contains the confirmed 1440-wide resident/dose list screen (frame 9690:99808), 24px content padding — conflicts with File 3's 32px default, real value takes precedence for this screen |
| ✨ Syringe drivers | 4636:34344 | — |
| ✨ Time Sensitive Medications | 5239:57515 | — |
| ✨ Out of Dose Rounds | 5016:68231 | — |
| ✨ PRN | 5034:26538 | — |
| ✨ OBS | 5922:8514 | — |
| ✨ NIM | 5827:32406 | — |
| ✨ Emergency Stock | 5703:44956 | — |
| ✨ In-possession Meds | 14907:185740 | — |
| ✨ Resident Linking | 8753:151 | — |
| ✨ ASQSC Psychotropic Assessment Tool | 9593:35757 | — |
| ✨ Resident Document Management | 10134:40810 | — |
| ✨ Resident Photo Update | 10226:77802 | — |
| ✨ NIM Maintenance | 10918:8346 | — |
| ✨ Pharmacy Incident | 13838:2280 | — |
| ✨ Printable Forms | 14248:235597 | — |
| ✨ Medication Chart | 14073:50778 | — |
| ✨ S8 Destruction | 14248:244345 | — |
| ✨ MIMS | 12626:195825 | — |
| ✨ Resident Maintenance | 10446:32124 | — |
| ✨ Progress Notes | 18802:57717 | — |
| ✨ Care Team | 15444:187084 | — |
| ✨ MMR | 14013:2 | — |
| ✨ Vaccine Maintenance | 24285:50778 | — |

## File 3 — Untitled UI Pro (foundation architecture, licensed)

URL base: https://www.figma.com/design/zLah46S6FFoCXki3YQrtnw/Untitled-UI-PRO-VARIABLES
File key: zLah46S6FFoCXki3YQrtnw

Licence: PRO STUDIO/BUSINESS tier confirmed for team use — verify seat
count matches actual team size before broader rollout. Do not commit
exported assets (icons, component screenshots) from this file into a
public repo — redistribution to unlicensed users is restricted, and a
public repo counts as that.

Source of truth for design-tokens.md structure (Colour semantic layer,
Typography, Spacing, Radius, Widths, Containers, Effects/Shadows) as of the
v2 migration.
Component patterns (Application Examples) are reference-only inspiration
for spec-writing, not extracted or used directly — BestDOSE screens are
still built from written specs, not from this file's example screens.

| Collection / Page | Node ID | Status |
|---|---|---|
| 1. Color modes | — | Extracted (Text/Border/Foreground/Background, Light mode) |
| 6. Typography | — | Extracted (font family, weights, size/line-height scale) |
| 3. Spacing | — | Extracted (17-step scale) |
| 2. Radius | — | Extracted (11-step scale) |
| 4. Widths | — | Extracted (breakpoint scale) |
| 5. Containers | — | Extracted (padding/max-width defaults) |
| ❖ Effect styles (Shadows) | 1532:352912 | Extracted 21 Jul 2026 → design-tokens.md Shadow section (7 tokens: xs–3xl; supersedes File 1 shadows 423:6344) |
| ❖ SHARED COMPONENTS | 1030:33572 | Component specs extracted here (v3). Confirmation modal extracted; **panel modal types (form + data/table) NOT yet extracted** — components.md "Modal — Panel types" is defined from shell primitives, needs a node-id to reconcile |
| ❖ APPLICATION EXAMPLES | 1664:398801 | Reference/inspiration only, not extracted |
| _Primitives | — | Not extracted directly (407 vars) — accessed only via alias resolution from Spacing/Widths/Containers |

## File 4 — Dose Rounds (production screen source)

URL base: https://www.figma.com/design/4yxqkYG3so5HxgTMvFzvh5/Dose-Rounds
File key: 4yxqkYG3so5HxgTMvFzvh5

Added 21 Jul 2026. A large multi-artboard file holding the real production
Dose Rounds screens (legacy BESTMED styling — Open Sans, 2px radii, slate
#39506E / teal #3DA8B8 accents). Used as a CONTENT/LAYOUT reference for
copying real screens and re-skinning them to the v3 system — not a token
source (design-tokens.md still comes from Files 1 + 3). Provenance vs the
licensed Untitled UI system is unverified; treat extracted legacy values
as reference only.

Dozens of artboards exist (Maindose desktop/tablet variants and states);
only the node below has been extracted so far.

| Page / Frame | Node ID | Status |
|---|---|---|
| BESTDose / Dose Rounds / Desktop (1440×804) | 1:17768 | Extracted → merged into output/dose-rounds.html (v3 skin, Figma content) |
| BESTDose / Dose Rounds / Desktop (tablet, 1024×768) | 1:17806 | Not extracted |
| Maindose - Desktop (1446×2825) | 1:17851 | Not extracted |
| Maindose - Tablet (many) | 1:18110, … | Not extracted |

## How this gets used

For design-tokens.md changes: re-run extraction against File 3 (structure)
and File 1 (BESTMED-specific colours) if either source file changes in
Figma — this is an ongoing sync step, not one-time.

For screen builds: get the node-specific URL for a one-off Figma
exception from File 2, or build from a written spec per the current
spec-only workflow. Update this table's "Notes"/"Status" columns as
pages get located and extracted.