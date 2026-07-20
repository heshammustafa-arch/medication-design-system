# Screen Build Prompt Template

Figma is used only for the BESTMED Design System (tokens, components) —
not for extracting individual screen layouts. Screen structure comes
entirely from the written spec in specs/. Fill in the brackets.

---

Build the screen described in `specs/[SCREEN-FILE].md`.

Read `design-system/design-tokens.md`, `design-system/components.md`,
`design-system/accessibility.md`, and `CLAUDE.md` first. Use only the
tokens and components defined there — flag anything the spec needs that
isn't already covered instead of guessing a value.

Do not attempt to open, browse, or infer content from any BestDOSE
application Figma URL, even if one is referenced for context elsewhere —
layout must come from the spec only.

[Optional: attach a screenshot for visual reference. This helps close
the gap that written-only specs leave open, especially for layout
judgement calls the spec might describe ambiguously.]

Output: single self-contained HTML file with embedded CSS, saved to
output/[FILENAME].html. Semantic HTML5, BEM class naming, CSS custom
properties for every token reference, comments marking each component
section.

Constraints:
- No JS frameworks, plain HTML/CSS only
- Must map cleanly to later Angular conversion — no inline styles
- Meet every rule in accessibility.md without exception