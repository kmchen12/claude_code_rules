---
paths:
  - "**/*.html"
  - "**/*.css"
  - "**/*.scss"
  - "**/*.jsx"
  - "**/*.tsx"
  - "**/*.vue"
  - "**/*.svelte"
---

# UI

Applies to any user interface work. Follow the project's existing design system and stack first; unless the project says otherwise, deliver self-contained HTML/CSS. For new screens, redesigns and audits, load the `ui-design` or `ui-audit` skill.

The aim is an interface that looks decided, not generated: every gradient, section, animation and adjective has a reason specific to this product. If it would work unchanged for a competitor, it is not decided.

## Floor: never ship

- Contrast below WCAG AA: body text 4.5:1, large text and non-text controls 3:1. Compute it, do not eyeball it.
- Missing visible focus state; `outline: none` without a `:focus-visible` replacement; a flow that cannot be completed by keyboard.
- Ignoring `prefers-reduced-motion`. Provide fewer and gentler animations there; do not kill feedback that carries meaning.
- A broken phone layout: horizontal scroll, text leaving its container, overlapping elements, tap targets under 44×44 px, disabled zoom.
- Fabricated data: invented numbers, testimonials, logos, customers, compliance or performance claims. Sample content is labelled as sample.
- Controls that do nothing, links that go nowhere, forms that fake success.
- Data views without empty, loading and error states.
- Status conveyed by colour alone; clickable `div`s instead of `button` or `a`; inputs without a visible label; images without `alt`.

## Reflex: avoid by default

Break one only with a reason specific to this product, and record the reason in the reply or the design notes.

- A small eyebrow label above every heading; all-caps tracked labels; a single coloured or gradient word in a heading.
- Blue-to-purple gradients, glows, glassmorphism, gradient text, emoji or sparkle icons, monospace as a "technical" costume.
- The template page: hero plus three identical cards, fixed three-step "how it works", three pricing tiers with "most popular", logo bar of trusted-by, cards nested in cards, every section built the same.
- Empty frames or soft rounded rectangles standing in for content; all-photo pages; a first viewport whose text does not match its image.
- A newsletter signup forced onto the end of every page.
- The same entrance animation on every section; bounce or elastic easing; hover effects that move neighbours.
- Dark mode, a second font family, or a new colour without a stated reason.
- Stock CTAs and buzzwords (see `writing.md`).

## Finish: polish, does not block shipping

Spacing rhythm, alignment, type scale, optical balance, micro-interactions.

## Process

- Read the existing project and its design direction first. With no direction, ask; do not invent a brand.
- Complete the first viewport on its own before building the rest.
- Check at phone, tablet and desktop widths (at least 320, 390, 768, 1280 px), in every theme shipped, by keyboard, with reduced motion and at 200% text size.
- Look before saying done: run it, render it, click every control. Say what you could not check.
