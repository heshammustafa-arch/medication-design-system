# Component Definitions — BESTMED Design System v2

Real BESTMED measurements, extracted from Figma component instances,
expressed in the new v2 token scale. Every value below landed exactly on
a defined spacing/radius step — no rounding needed.

## Button

Three sizes, all sharing --radius-xxs (2px).

| Size | Height | Padding V | Padding H | Gap (icon-label) |
|---|---|---|---|---|
| Small | 34px | --spacing-md (8px) | --spacing-lg (12px) | --spacing-md (8px) |
| Medium | 38px | --spacing-md (8px) | --spacing-xl (16px) | --spacing-md (8px) |
| Large | 48px | --spacing-lg (12px) | --spacing-3xl (24px) | --spacing-md (8px) |

```html
<button class="btn btn--medium btn--primary">Administer dose</button>
```

Colour/state variants (Active/Hover/Pressed/Disabled/Destructive) exist
in Figma, colour pairings not yet extracted — cross-check against
--bg-brand-solid (primary), --bg-error-solid (destructive), --bg-disabled
(disabled) before hardcoding.

### Icon-only / circular button

- 30px or 40px square, --radius-full
- Padding: --spacing-md (8px) all sides

## Badge

Three sizes, two styles (Filled / Outline). Radius differs by style, not size.

| Size | Height | Padding V | Padding H | Radius (Filled) | Radius (Outline) |
|---|---|---|---|---|---|
| Small | 22px | --spacing-xxs (2px) | --spacing-md (8px) | --radius-2xl (16px) | --radius-3xl (20px) |
| Medium | 26px | --spacing-xxs (2px) | --spacing-md (8px) | --radius-2xl (16px) | --radius-3xl (20px) |
| Large | 32px | --spacing-xs (4px) | --spacing-md (8px) | --radius-2xl (16px) | --radius-3xl (20px) |

```html
<span class="badge badge--medium badge--filled badge--success">Administered</span>
<span class="badge badge--medium badge--outline badge--warning">Due 14:00</span>
```

Only "Success" geometry confirmed. Other status types (Warning, Danger,
Info) follow the same pattern — pair with --bg-warning-primary,
--bg-error-primary etc., verify exact colour pairing against Figma
before finalising.

## Modal / dialog

Three size variants, all sharing identical padding, radius, and internal
spacing — only width and content height change.

| Size | Width | Padding | Radius | Internal gap |
|---|---|---|---|---|
| Small | 368px | --spacing-3xl (24px) | --radius-xs (4px) | --spacing-xl (16px) |
| Medium | 568px | --spacing-3xl (24px) | --radius-xs (4px) | --spacing-xl (16px) |
| Large | 768px | --spacing-3xl (24px) | --radius-xs (4px) | --spacing-xl (16px) |

```html
<div class="modal modal--medium">
  <div class="modal__body">...</div>
</div>
```

Height is content-driven in all three variants — don't fix a height,
let it hug content. A "Form + warning" variant exists at 768px width
with a taller default height (468px observed) — treat as a content
scenario, not a separate size token.

Backdrop, title bar, and dual-signature/confirmation sub-patterns exist
on this page but weren't individually extracted — pull on demand.

## Input field (text)

Two sizes (Small/Medium), structure is label row → field → helper text
row, stacked with --spacing-xs (4px) gap between rows.

| Size | Field height | Padding V | Padding H | Radius |
|---|---|---|---|---|
| Medium | 48px | --spacing-md (8px) | --spacing-lg (12px) | --radius-xs (4px) |
| Small | not yet measured — component exists (320×68 total), field-only height not isolated |

```html
<div class="input-field input-field--medium">
  <label class="input-field__label">Resident name</label>
  <input class="input-field__control" type="text">
  <span class="input-field__helper"></span>
</div>
```

Other input types exist as separate components, not yet extracted:
Date, Dropdown (single/multi), Multiline Text Field, Checkbox. Pull each
on demand — don't assume they share the Text input's padding/radius.

## Table row (Dose Rounds / resident list — confirmed from BestDOSE app file)

Not a BESTMED library component — real row structure from the live Dose
Rounds screen. Row height 120px, horizontal layout, --spacing-xxs (2px)
gap between cells, --radius-xs (4px) corner radius.

| Column | Width | Content |
|---|---|---|
| Resident (photo + badge + name) | 584px | Avatar, warning badge, "LASTNAME, Firstname" |
| DOB | 200px | Date |
| Facility/Ward | 250px | Facility name |
| Room | 150px | Room number |
| MIN | 200px | Medical identifier number |

Column widths sum to 1384px + 4×2px gaps = 1392px, matching the app's
confirmed content width (24px real padding — see figma-links.md
conflict note against the 32px v2 container default).

This is a resident-level list, not a per-medication list — confirm which
one a new screen actually needs before reusing this structure.

## Not yet extracted

- Card component (standalone, if one exists outside table rows)
- Checkbox / Radio input styling
- Date and Dropdown input variants
- Tabs, page header, header/nav components seen in Dose Rounds
- Small input field's isolated field height (only total component
  height measured so far)

Extract as they come up in a screen build, not preemptively.