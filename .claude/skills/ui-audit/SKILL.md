---
name: ui-audit
description: Use when asked to review, critique, audit or score an existing user interface, screen, page or screenshot, or to explain why a UI looks generic or AI-made. Produces numbered findings with severity and evidence and changes nothing until the user picks which findings to fix.
---

# UI audit

An audit records; it does not fix. Deliver numbered findings, then wait for the user to choose which to fix. Findings not chosen are not touched.

## Method

1. Read the product context and any design direction. State in one line what the surface is for and who uses it.
2. Look at the real thing: run or render it at 390 and 1280 px, in each theme, by keyboard. Say what could not be run.
3. Judge the design before reading automated tool output, so the tools do not anchor the judgment.
4. Name each problem, point at the element (`file:line` or selector), give the fix in a few words. "It looks AI" is a guess; a named pattern is evidence.

## Severity

- P0 Blocking: a task cannot be completed, or a Floor item from `.claude/rules/ui.md` fails.
- P1 Major: a WCAG AA failure or a serious usability problem; fix before release.
- P2 Minor: a Reflex item with no stated reason, inconsistency, friction.
- P3 Polish: Finish items. Keep these few.

## Design critique

Score each heuristic 0 to 4 (total out of 40) with one line of evidence each:

1. Visibility of system status
2. Match with the real world
3. User control and freedom
4. Consistency and standards
5. Error prevention
6. Recognition rather than recall
7. Flexibility and efficiency
8. Aesthetic and minimalist design
9. Error recovery
10. Help and documentation

Mark a heuristic `n/a` when it does not apply to the surface and scale the total. Most real interfaces land between 20 and 32.

Add:

- Specificity verdict: is this authored for this product, or would it fit any product in the category? Test: swap the logo and product name.
- Cognitive load: single focus, chunks of four or fewer, clear grouping, clear hierarchy, one step at a time, four or fewer choices per decision, progressive disclosure. Count the failures.
- Two or three walkthroughs chosen from: first-time user, power user, keyboard or screen-reader user, user on a phone, user with worst-case data.

## Technical audit

Score each 0 to 4 (total out of 20):

- Accessibility: contrast, focus, keyboard, semantics, labels, alt text, zoom.
- Performance: layout shift, image sizing, blocking resources, animation cost. Report measured values only.
- Theming: tokens, hard-coded colours, completeness of every shipped theme.
- Responsive: overflow, tap targets, breakpoints, safe areas.
- Integrity: dead controls, fake submissions, invented data, missing states.

## Report

In Taiwan Traditional Chinese unless the project says otherwise:

1. Verdict in one or two lines, with both scores.
2. Two or three things that work.
3. Findings, numbered, most severe first: severity, location, what is wrong, the fix.
4. What was not checked.

Then ask which finding numbers to fix.
