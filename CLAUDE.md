# CLAUDE.md

## Project
Design system and screen-generation project for BestDOSE, a medication
management application inside an aged care administration platform.
Output is HTML/CSS, later ported into Angular components by the
engineering team. Build markup and class structure with that conversion
in mind — semantic HTML, predictable component boundaries, no inline
styles, no JS frameworks.

## Audience
Primary users are aged care facility staff (nurses, care workers), often
time-pressured, on shared devices, varying in digital literacy. Default
assumption is staff-facing unless a screen brief says otherwise.

## Source of truth
- `design-system/design-tokens.md` — colour, typography, spacing, radius, shadow
- `design-system/components.md` — component specs (buttons, badges, tables — expanding as screens are built)
- `design-system/accessibility.md` — non-negotiable accessibility rules
- `design-system/figma-links.md` — Figma file/page/node references for both the design system library and the live application file

This design system has no Figma Variables layer — all values come from
Figma Styles (paint/text/effect) and direct component inspection. Never
invent a colour, spacing, or type value that isn't already in
design-tokens.md or components.md. If a screen needs something not yet
documented, extract it live from Figma and add it — don't estimate.

## Two Figma files in play
1. **BESTMED Design System** — the component library (buttons, badges,
   tables, etc. in isolation). Source for design-tokens.md and components.md.
2. **BestDOSE** — the actual application, screens built from that library.
   Source for individual screen layouts, page chrome, and real content
   structure. See figma-links.md for both file keys.

## Screen-building workflow
As of this stage, screens are built one at a time, prompt-only: the
person supplies a screen name and a Figma frame URL (with node-id), and
Claude extracts layout, cross-checks values against the design system
files, flags anything undocumented, then generates HTML. See
prompts/build-screen-prompt.md for the exact template. Written specs in
specs/ are optional now — used only when a screen needs context Figma
can't show (business logic, edge cases, copy that isn't finalised).

## Known limitations
- Claude cannot browse Figma URLs passively — every value comes from a
  live, explicit extraction via the Figma MCP connector against a
  specific file key and node ID. If a link has no node-id, ask for one.
- Real button heights (34/38/48px) fall below the 44px touch-target
  rule in accessibility.md — this is an open, unresolved conflict
  between the Figma library and the stated accessibility standard.
  Don't silently resolve it either way; flag it per screen if it's load-bearing.

## Output conventions
- Semantic HTML5 elements (main, section, nav, button, table where
  tabular data is genuinely tabular)
- BEM-style class names (block__element--modifier) — maps cleanly to
  Angular component/host class conventions later
- CSS custom properties for every token value, defined at :root,
  referenced everywhere else — never hardcoded hex/px values in
  component rules
- Comment each major section of the HTML with the component name it maps to