# Figma Reference Log

Three files in play. None can be opened passively — every value in
design-tokens.md and components.md came from a live, explicit extraction
against a specific file key and node ID via the Figma MCP connector.

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
Typography, Spacing, Radius, Widths, Containers) as of the v2 migration.
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
| ❖ SHARED COMPONENTS | 1030:33572 | Not extracted — BESTMED's own component measurements used instead |
| ❖ APPLICATION EXAMPLES | 1664:398801 | Reference/inspiration only, not extracted |
| _Primitives | — | Not extracted directly (407 vars) — accessed only via alias resolution from Spacing/Widths/Containers |

## How this gets used

For design-tokens.md changes: re-run extraction against File 3 (structure)
and File 1 (BESTMED-specific colours) if either source file changes in
Figma — this is an ongoing sync step, not one-time.

For screen builds: get the node-specific URL for a one-off Figma
exception from File 2, or build from a written spec per the current
spec-only workflow. Update this table's "Notes"/"Status" columns as
pages get located and extracted.