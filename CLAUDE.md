# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

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
- `design-system/figma-links.md` — Figma file/page/node references for all three Figma files

Never invent a colour, spacing, or type value that isn't already in
design-tokens.md or components.md. If a screen needs something not yet
documented, extract it live from Figma and add it — don't estimate.

## Three Figma files in play
1. **BESTMED Design System** (`9XibHmB1A7hcflpo0wBeKx`) — legacy component library. Source for component measurements in components.md and for medication classification colours (no equivalent in File 3).
2. **BestDOSE** (`3mEBxpW3AU6agtPHiikZD5`) — the actual application. Source for individual screen layouts, page chrome, and real content structure.
3. **Untitled UI Pro** (`zLah46S6FFoCXki3YQrtnw`) — licensed foundation. Source of truth for design-tokens.md structure (colour semantic layer, typography, spacing, radius, widths, containers). Do not commit exported assets from this file into a public repo — redistribution to unlicensed users is restricted.

## Screen-building workflow
Screens are built one at a time: supply a screen name and a Figma frame URL (with node-id), Claude extracts layout, cross-checks values against the design system files, flags anything undocumented, then generates HTML. See `design-system/build-screen-prompt.md` for the exact prompt template.

Written specs in `specs/` are optional — used only when a screen needs context Figma can't show (business logic, edge cases, copy that isn't finalised).

Generated HTML goes in `output/`.

## Known limitations
- Claude cannot browse Figma URLs passively — every value comes from a
  live, explicit extraction via the Figma MCP connector against a
  specific file key and node ID. If a link has no node-id, ask for one.
- Real button heights (34/38/48px) fall below the 44px touch-target
  rule in accessibility.md — this is an open, unresolved conflict
  between the Figma library and the stated accessibility standard.
  Don't silently resolve it either way; flag it per screen if it's load-bearing.

## Output conventions
- Semantic HTML5 elements (`main`, `section`, `nav`, `button`, `table` where tabular data is genuinely tabular)
- BEM-style class names (`block__element--modifier`) — maps cleanly to Angular component/host class conventions later
- CSS custom properties for every token value, defined at `:root`, referenced everywhere else — never hardcoded hex/px values in component rules
- Comment each major section of the HTML with the component name it maps to
