---
name: ui-design
description: Use when building or changing a user interface beyond a one-line tweak - a new page, screen, component, dashboard, landing page, form, redesign, or when asked to make a UI look less generic or less AI-made. Covers direction, typography, colour, layout, motion, states, controls, responsive behaviour and the pre-delivery check.
---

# UI design

`.claude/rules/ui.md` holds the Floor, Reflex and Finish tiers and always applies. This skill is the working method and the numbers.

## 1. Direction before pixels

1. Read what exists: design tokens, components, a design or brand document, the product's own copy. Existing public names (tokens, URLs, form field names) are protected.
2. Decide what kind of surface this is; it sets the ambition.
   - Persuade (landing, marketing): one strong idea, real imagery, distinctive type.
   - Operate (app, dashboard, settings): precision and restraint; layout follows the decisions the user makes on this screen.
   - Read (docs, articles): measure, rhythm and navigation.
3. Write the direction in three to five lines before building: audience, the one thing the first viewport must say, colour strategy, type choice, the single authored motion moment, and any Reflex item deliberately allowed with its reason.
4. With no direction and a vague brief, ask (see CLAUDE.md "Asking") or offer up to three options from different families. Never invent a logo, people, statistics or testimonials; use an obvious placeholder (`[LOGO]`, initials, `[REAL DATA]`).

Purpose test for every technique: "what does this serve?" Hierarchy, identity or readability are answers. "It looks modern" is not.

## 2. Typography

- Body 16 px minimum on the web; line height 1.45 to 1.6; 45 to 75 characters per line. Inputs at least 16 px.
- At most five sizes, with clearly different steps; display about 3 to 4 times body. One family unless a second has a distinct role.
- Headings `text-wrap: balance`, body `text-wrap: pretty`. Tabular numerals for data.
- Emphasis comes from weight or size, not gradient text.
- Fluid sizes with `clamp()`; load only the weights used.
- CJK text: line height toward 1.7, no letter-spacing tricks borrowed from Latin display type, and fonts that cover Traditional Chinese glyphs.

## 3. Colour

- Two or three core colours plus one accent, neutrals aside. The accent has one job and covers a small part of any viewport; the primary action colour is not reused as decoration.
- Tinted neutrals; secondary text on a coloured surface is mixed from that hue, not plain grey.
- Semantic tokens over hard-coded values. Dark mode is designed, not inverted.
- Compute contrast for every text and control pair in every theme.

## 4. Layout and spacing

- One spacing scale on a 4 px base; off-scale values are a tell. Tighter inside groups than between them; more space above a heading than below it.
- One focal point per screen. Squint test: primary, secondary and groups still read when blurred.
- Sibling spacing with `gap`. Grid children get `min-width: 0`. Grids use `minmax()` / `auto-fit`.
- Shadow marks elevation only; a border or a shadow, not both. Nested radius equals outer radius minus padding.
- Named z-index scale. `100dvh`, not `100vh`.
- Charts: the title states the question the chart answers; bars start at zero.
- Limits: about four options per decision, five top-level navigation items, one primary action per view.

## 5. Motion

- One authored moment per surface. Everything else is feedback.
- Durations: 100 to 150 ms immediate feedback, 150 to 300 ms state changes, 300 to 500 ms layout and overlays. Exits faster than entrances. Ease-out curves; no bounce by default.
- Animate transform and opacity, not width, height, top, left or margin.
- Content is visible without scripts. Loops stop off-screen. Anything moving longer than 5 seconds can be paused.

## 6. States and behaviour

- Every control: default, hover, focus, active, disabled, loading, error, success. Every data view: empty, loading, error, each saying what happened and what to do next.
- State changes never change geometry. Pressed feedback within about 100 ms. Show a skeleton only when a wait passes about 300 ms.
- Forms: validate on blur, keep the user's input on failure, block double submission, validate again on the server.
- No function that exists only on hover.
- Test with worst-case content: 100-character names, unbreakable strings, counts of 0 and 1, empty and huge lists, CJK and RTL text, 30 to 40 percent longer translations.

## 7. Controls with an icon

Anything that must stay equal is held by one number or by layout, never by two constants kept equal by hand.

- A flex box with one `padding-inline`; text `flex: 1; min-width: 0`; the icon is the last flex child.
- No `position: absolute; right: 12px` icons, background-image chevrons, negative-margin nudges or `line-height` used for vertical centring.
- One height token per row of controls.

## 8. Responsive

- Phone is its own layout, not a shrunken desktop. Breakpoints go where the content breaks.
- Section padding roughly halves on phones. Navigation collapses to a labelled menu or bottom bar that respects the safe area.
- Images and media declare width and height or an aspect ratio; the main image is not lazy-loaded.

## 9. Before delivering

Run it and look. Report each line as passed, failed or not checked:

- Floor items from `ui.md`, with computed contrast values.
- Widths 320, 390, 768, 1280 px; every theme; keyboard only; reduced motion; 200% text.
- Every control clicked, every link followed, every state seen.
- Every number, name, logo and quote is real or visibly a placeholder.
- Each Reflex item used, with its reason.

Unmeasured performance or accessibility scores are reported as "not measured".
