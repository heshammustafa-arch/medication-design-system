# Accessibility Rules — Non-Negotiable

These apply to every generated screen regardless of what a spec, Figma
file, or component definition says. If anything conflicts with a rule
here, flag the conflict — don't silently resolve it either way.

## Colour contrast

- Body text on background: minimum 4.5:1 (WCAG AA)
- Large text (18px+ bold or 24px+ regular — i.e. --text-lg bold or
  --display-xs and above) and UI component boundaries: minimum 3:1
- Never convey status by colour alone — badges always carry text, never
  just a coloured dot
- New v2 semantic tokens (--text-error-primary, --bg-error-primary, etc.)
  were extracted for their brand/clinical meaning, not pre-verified for
  contrast as pairs — check any new text-on-background combination
  against its actual contrast ratio before shipping, don't assume a
  "primary/secondary" naming pair is automatically compliant

## Touch targets

- Project standard: minimum 44×44px for any interactive element
- KNOWN CONFLICT, UNRESOLVED: real BESTMED buttons measure 34px (Small),
  38px (Medium), 48px (Large) — see components.md. Small and Medium fall
  short. Don't silently pad button height to 44px in generated output,
  and don't silently accept 34px either.
- Default to Large (48px) for any primary clinical action unless a spec
  says otherwise. Flag Small/Medium usage per screen if the interaction
  is touch-critical (shared tablet, care staff use).
- If padding needs adjusting to hit 44px without changing font size,
  --spacing-lg (12px) vertical padding is the smallest step in the new
  scale that gets a Medium button (38px core) close to 44px with border
  included — still confirm the actual rendered height, don't assume the
  token math alone closes the gap.

## Keyboard and screen reader

- Every interactive element reachable via Tab, in logical order
- Every icon-only button needs an aria-label describing the action, not
  the icon
- Modals trap focus while open, return focus to the triggering element
  on close
- Tables use proper `<th>` with scope attributes, not styled divs

## Motion

- No auto-advancing carousels or timed dismissals on anything showing
  medication status
- Respect prefers-reduced-motion for any transition/animation

## Text

- Minimum 16px body text for primary clinical content (--text-md or
  larger) — --text-xs (12px) is metadata/captions only
- No text embedded in images
- Line length capped at roughly 80 characters for paragraph text
- Font is now Inter system-wide (see design-tokens.md) — Inter's x-height
  and default line-height differ slightly from the old Open Sans ramp;
  if a screen built under v1 tokens is regenerated under v2, re-check
  that text doesn't clip or overlap at the same container heights, don't
  assume line-height values transfer cleanly between the two fonts