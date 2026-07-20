# Component Definitions — BESTMED Design System v3

Untitled UI Pro fully replaces the original BESTMED Design System as
source of truth for all UI component specs. Every measurement below is
extracted directly from the Untitled UI Pro Figma file, 20 July 2026 —
none are BESTMED's own production measurements anymore. Medication
classification colours remain BESTMED-specific (design-tokens.md) — that
is the only category with no Untitled UI equivalent, and stays exempt
from this replacement.

This is a deliberate redesign decision, not a documentation correction.
BESTMED's currently-shipping app uses different proportions throughout
(2px button radius vs. 8px, 120px table rows vs. 72px, etc.). Screens
built from this file won't visually match production until the real app
is updated to follow it.

Policy going forward: any UI component not yet listed here defaults to
Untitled UI Pro. Extract it the same way — on demand, when a real screen
needs it — not preemptively. No more per-component confirmation needed;
this file's existence is the standing instruction.

## Button

| Size | Height | Padding V | Padding H | Radius | Gap (icon-label) |
|---|---|---|---|---|---|
| Small | 36px | 8px | 12px | --radius-md (8px) | 4px |
| Medium | 40px | 10px | 14px | --radius-md (8px) | 4px |
| Large | 44px | 10px | 16px | --radius-md (8px) | 4px |
| Extra Large | 48px | 12px | 18px | --radius-md (8px) | 4px |

```html
<button class="btn btn--md btn--primary">Administer dose</button>
```

Hierarchy variants confirmed: Primary, Secondary, Tertiary, Link color,
Link gray — colour pairings not yet extracted per hierarchy.
States confirmed: Default, Disabled, Focused — not yet individually extracted.

Accessibility: Large (44px) and XL (48px) clear the 44px touch-target
minimum. Small (36px) and Medium (40px) still fall short — default to
Large/XL for primary clinical actions.

## Badge

| Size | Height | Padding V | Padding H | Radius (Pill) | Radius (Badge) |
|---|---|---|---|---|---|
| Small | 22px | 2px | 8px (Pill) / 6px (Badge) | 9999px | 6px |
| Medium | 24px | 2px | 10px | 9999px | 6px |
| Large | 28px | 4px | 12px | 9999px | 6px |

```html
<span class="badge badge--pill badge--md badge--brand">Administered</span>
<span class="badge badge--sm badge--gray">Due 14:00</span>
```

Colour variants confirmed: Brand, Gray, Gray blue — error/warning/success
not yet extracted. Icon (dot) variant confirmed to exist, adds ~10px
width, not yet measured in isolation.

Medication classification badges keep BESTMED's own clinical colours —
only shape/size geometry changes, not what colour means clinically.

## Modal / Dialog

Confirmation-dialog pattern ("Stacked left aligned") — other modal types
in the library (centered photo, checkboxes, file upload, etc.) follow
different internal structures, extract separately if needed.

**Outer container:** 400px width (this pattern specifically — not
surveyed across other modal types), --radius-2xl (16px), close button
44×44px top-right.

**Header:** 24px padding, 16px internal gap. Featured icon (48×48px)
stacked above title + description, left-aligned. 20px bottom padding,
1px full-width divider below.

**Actions footer:** 32px top padding, buttons horizontal with 12px gap.
Two buttons (Cancel/Confirm), width is content-driven — don't hardcode.

```html
<div class="modal modal--confirmation">
  <button class="modal__close" aria-label="Close">×</button>
  <div class="modal__header">
    <div class="modal__icon"></div>
    <div class="modal__text">
      <h3 class="modal__title"></h3>
      <p class="modal__description"></p>
    </div>
  </div>
  <div class="modal__divider"></div>
  <div class="modal__actions">
    <button class="btn btn--lg btn--secondary">Cancel</button>
    <button class="btn btn--lg btn--primary">Confirm</button>
  </div>
</div>
```

## Modal — Panel types (form + data)

Distinct from the confirmation dialog above — used when a modal must carry a
form or a data table rather than a featured icon + message. Shares the
confirmation dialog's shell primitives (radius, close button) at a wider width.

*Source: defined from the v3 modal shell primitives for the panel use cases
(Insulin Sliding Scale form; BGL/INR History tables). Not itself an isolated
Figma extraction — reconcile against Untitled UI Pro's form/data-modal
components when those are pulled.*

**Outer container:** --width-lg (640px), --radius-2xl (16px), close button
44×44px top-right.

**Header:** title only (--text-xl), 24px padding, 20px bottom padding, 1px
full-width divider below. No featured icon (unlike the confirmation dialog).

**Body:** 24px padding, --spacing-lg (12px) internal gap. Carries either:
- Form content — stacked input fields (Medium, 44px), a value-display block for
  read-only calculated values, and/or a warning strip; or
- A data table — v3 Table rows (72px, 16/24 cell padding) in a horizontal
  scroll wrapper.

**Actions footer:** 24px padding, 32px top padding, buttons horizontal with
12px gap, Large (44px). One (Close) or two (Cancel/Confirm) buttons, width
content-driven — don't hardcode.

```html
<div class="modal modal--panel">
  <button class="modal__close" aria-label="Close">×</button>
  <div class="modal__panel-header"><h3 class="modal__title"></h3></div>
  <div class="modal__divider"></div>
  <div class="modal__body"><!-- form fields OR data table --></div>
  <div class="modal__actions">
    <button class="btn btn--lg btn--secondary">Cancel</button>
    <button class="btn btn--lg btn--primary">Confirm</button>
  </div>
</div>
```

Reference implementations: form panel = Insulin Sliding Scale Directions;
table panel = BGL / INR History (output/dose-round-tab-states.html, specimens
E/F/G).

## Input field (text)

| Size | Field height | Padding V | Padding H | Radius |
|---|---|---|---|---|
| Medium | 44px | 10px | 14px | --radius-md (8px) |
| Small | 40px | 8px | 12px | --radius-md (8px) |

```html
<div class="input-field input-field--md">
  <label class="input-field__label">Resident name</label>
  <input class="input-field__control" type="text">
  <span class="input-field__helper"></span>
</div>
```

States confirmed: Placeholder, Filled, Disabled, Destructive (error).
Type variants confirmed: Default, Payment input. Colour pairings for
Destructive not yet extracted — pair with --border-error /
--text-error-primary from design-tokens.md, verify against Figma.

## Table row

72px row height, consistent across every cell style variant (text,
badge, avatar, checkbox, radio, toggle). Cell padding: 16px vertical,
24px horizontal.

```html
<tr class="table-row">
  <td class="table-row__cell">...</td>
</tr>
```

Cell style variants confirmed to exist: Lead text, Text, Badge, Avatar
group, Badges multiple, Lead checkbox, Lead avatar, Payment method, Lead
avatar checkbox/radio/toggle — column content type varies by which
variant a screen's spec calls for.

BESTMED's real Dose Rounds table (120px rows, 584/200/250/150/200px
columns) is superseded. Rebuilding that screen under v3 will produce a
noticeably more compact table — 72px vs. 120px is a real, visible
density change, not a rounding difference. Flag this before regenerating
Dose Rounds.

## Not yet extracted

Button colour pairings per hierarchy, badge colour variants beyond
Brand/Gray/Gray blue, other modal type patterns, input Destructive-state
colours, and anything outside these five components — Tabs, Page
headers, Avatars, Checkboxes, Tooltips, Dropdowns, etc. all exist in the
Untitled UI Pro library and follow the same extraction method. Pull on
demand.