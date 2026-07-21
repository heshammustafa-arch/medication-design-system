# Design Tokens — BESTMED Design System v2

Foundation architecture adopted from Untitled UI Pro (licensed,
PRO STUDIO/BUSINESS tier confirmed for team use), repopulated with
BESTMED's actual brand and clinical colours. Genuine Figma Variables
structure with Light/Dark mode support, not static Styles — extracted
20 July 2026. This file is now source of truth; the old BESTMED Design
System file (static Styles) is superseded for design-tokens purposes.

Migration note: neutral text greys and tinted status backgrounds had no
BESTMED equivalent (BESTMED only ever defined solid brand and clinical
colours, no grey text scale or light-tint status backgrounds) — these are
adopted from Untitled UI's neutral scale as structural/neutral choices,
not brand decisions. Brand and clinical colours remain BESTMED's own
throughout.

## Colour — Semantic (Light mode)

### Text

| Token | Hex | Source |
|---|---|---|
| --text-primary | #181D27 | Adopted — BESTMED has no text-grey scale |
| --text-secondary | #414651 | Adopted |
| --text-tertiary | #535862 | Adopted |
| --text-disabled | #717680 | Adopted |
| --text-white | #FFFFFF | BESTMED Greys/White |
| --text-brand-primary | #003B95 | BESTMED Primary/Base |
| --text-brand-secondary | #022664 | BESTMED Primary/Dark |
| --text-error-primary | #CD1719 | BESTMED Primary/Red Base |
| --text-warning-primary | #F08F00 | BESTMED Medications/Edit Medication (repurposed as generic warning) |
| --text-success-primary | #067242 | BESTMED Medications/S8 (repurposed as generic success) |

### Border

| Token | Hex | Source |
|---|---|---|
| --border-primary | #D0D4DC | BESTMED Greys/Secondary 2 |
| --border-secondary | #EEEFF2 | BESTMED Greys/Secondary Background |
| --border-disabled | #D0D4DC | BESTMED Greys/Secondary 2 |
| --border-brand | #003B95 | BESTMED Primary/Base |
| --border-error | #CD1719 | BESTMED Primary/Red Base |

### Background

| Token | Hex | Source |
|---|---|---|
| --bg-primary | #FFFFFF | BESTMED Greys/White |
| --bg-secondary | #F7F7F9 | BESTMED Greys/Base |
| --bg-tertiary | #EEEFF2 | BESTMED Greys/Secondary Background |
| --bg-disabled | #EEEFF2 | BESTMED Greys/Secondary Background |
| --bg-brand-primary | #E0EEFF | BESTMED Primary/Light |
| --bg-brand-solid | #003B95 | BESTMED Primary/Base |
| --bg-brand-solid_hover | #022664 | BESTMED Primary/Dark |
| --bg-error-primary | #F8E7E9 | BESTMED Primary/Red Light |
| --bg-error-solid | #CD1719 | BESTMED Primary/Red Base |
| --bg-warning-primary | #FFFAEB | Adopted — BESTMED has no tinted status background |
| --bg-success-primary | #ECFDF3 | Adopted |

### Medication classification (BESTMED-specific — no Untitled UI equivalent exists)

Carries clinical meaning. Don't reuse decoratively, don't invent a colour
for a medication type not listed here — extract and flag instead.

| Token | Hex | Medication type |
|---|---|---|
| --color-med-prn | #FFA500 | PRN Medication |
| --color-med-cytotoxic | #3B0944 | Cytotoxic |
| --color-med-hazardous | #A500A8 | Hazardous |
| --color-med-nutritional | #FF6DD2 | Nutritional |
| --color-med-warfarin | #FAEE5A | Warfarin |
| --color-med-insulin | #B2704E | Insulin |
| --color-med-s8 | #067242 | S8 |
| --color-med-short-course | #C25B76 | Short course |
| --color-med-s4d | #800000 | S4D |
| --color-med-syringe-driver | #8DE1AF | Syringe Driver |
| --color-med-new | #2196F3 | New Medication |
| --color-med-edit | #F08F00 | Edit Medication |
| --color-med-high-risk | #FF5F1F | High Risk Medication |
| --color-med-reviewed | #70AD47 | Reviewed Medication |
| --color-med-vaccination | #14967F | Vaccination |

## Typography

Font family: Inter — adopted as part of this migration, replacing Open
Sans across the entire system, including screens already built (those
need regenerating to match, tracked separately, not urgent).

```css
--font-family-base: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", sans-serif;
```

Weights: Regular, Medium, Semibold, Bold (Medium is new — didn't exist in
the old Open Sans ramp)

### Body text

| Token | Size | Line-height |
|---|---|---|
| --text-xs | 12px | 18px |
| --text-sm | 14px | 20px |
| --text-md | 16px | 24px |
| --text-lg | 18px | 28px |
| --text-xl | 20px | 30px |

### Display / headings

| Token | Size | Line-height |
|---|---|---|
| --display-xs | 24px | 32px |
| --display-sm | 30px | 38px |
| --display-md | 36px | 44px |
| --display-lg | 48px | 60px |
| --display-xl | 60px | 72px |
| --display-2xl | 72px | 90px |

Old BESTMED heading tokens (--text-h1 through --text-h5, Open Sans) don't
map 1:1 to this scale — pick deliberately per screen, don't auto-convert.

## Spacing

| Token | Value |
|---|---|
| --spacing-none | 0px |
| --spacing-xxs | 2px |
| --spacing-xs | 4px |
| --spacing-sm | 6px |
| --spacing-md | 8px |
| --spacing-lg | 12px |
| --spacing-xl | 16px |
| --spacing-2xl | 20px |
| --spacing-3xl | 24px |
| --spacing-4xl | 32px |
| --spacing-5xl | 40px |
| --spacing-6xl | 48px |
| --spacing-7xl | 64px |
| --spacing-8xl | 80px |
| --spacing-9xl | 96px |
| --spacing-10xl | 128px |
| --spacing-11xl | 160px |

## Radius

| Token | Value |
|---|---|
| --radius-none | 0px |
| --radius-xxs | 2px |
| --radius-xs | 4px |
| --radius-sm | 6px |
| --radius-md | 8px |
| --radius-lg | 10px |
| --radius-xl | 12px |
| --radius-2xl | 16px |
| --radius-3xl | 20px |
| --radius-4xl | 24px |
| --radius-full | 9999px |

BESTMED's real button radius (2px) and badge radii (16px/20px) map
approximately to --radius-xs and --radius-2xl/--radius-3xl — confirm
against actual components before assuming an exact match.

## Widths (breakpoints / max-widths)

| Token | Value |
|---|---|
| --width-xxs | 320px |
| --width-xs | 384px |
| --width-sm | 480px |
| --width-md | 560px |
| --width-lg | 640px |
| --width-xl | 768px |
| --width-2xl | 1024px |
| --width-3xl | 1280px |
| --width-4xl | 1440px |
| --width-5xl | 1600px |
| --width-6xl | 1920px |

## Containers

| Token | Value |
|---|---|
| --container-padding-mobile | 16px |
| --container-padding-desktop | 32px |
| --container-max-width-desktop | 1280px |

Conflict flag: the actual BestDOSE Dose Rounds screen (extracted earlier,
live from the production app) used 24px content padding, not 32px. This
32px is the new system's default, not a confirmed BestDOSE value. Check
per screen — don't assume 32px is correct for existing app patterns.

## Shadow

Untitled UI "Effect styles" — extracted from File 3 (Untitled UI Pro,
node 1532:352912 "Shadows") on 21 July 2026. Supersedes the earlier BESTMED
shadow values (File 1, node 423:6344) for the v3 system. Every layer uses
`rgba(10,13,18, α)` — a near-black slate, not pure black — and the larger
steps stack multiple drop-shadow layers (copy the whole value verbatim).

| Token | Value |
|---|---|
| --shadow-xs | 0 1px 2px 0 rgba(10,13,18,0.05) |
| --shadow-sm | 0 1px 3px 0 rgba(10,13,18,0.10), 0 1px 2px -1px rgba(10,13,18,0.10) |
| --shadow-md | 0 4px 6px -1px rgba(10,13,18,0.10), 0 2px 4px -2px rgba(10,13,18,0.06) |
| --shadow-lg | 0 12px 16px -4px rgba(10,13,18,0.08), 0 4px 6px -2px rgba(10,13,18,0.03), 0 2px 2px -1px rgba(10,13,18,0.04) |
| --shadow-xl | 0 20px 24px -4px rgba(10,13,18,0.08), 0 8px 8px -4px rgba(10,13,18,0.03), 0 3px 3px -1.5px rgba(10,13,18,0.04) |
| --shadow-2xl | 0 24px 48px -12px rgba(10,13,18,0.18), 0 4px 4px -2px rgba(10,13,18,0.04) |
| --shadow-3xl | 0 32px 64px -12px rgba(10,13,18,0.14), 0 5px 5px -2.5px rgba(10,13,18,0.04) |

Old BESTMED shadow tokens (--shadow-sm/md/lg = 0 1px 6px / 0 2px 12px /
0 4px 16px rgba(0,0,0,0.1)) are retired — do not use.