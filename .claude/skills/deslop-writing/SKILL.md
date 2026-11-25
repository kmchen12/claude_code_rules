---
name: deslop-writing
description: Use when drafting or editing prose that people will read - README, documentation, reports, articles, emails, announcements, marketing or UI copy - or when the user says a text sounds AI-generated, generic, padded or over-explained, in Chinese or English. Also for cleaning code comments without touching code.
---

# Deslop writing

`.claude/rules/writing.md` always applies. This skill is the procedure for a whole text.

Slop is a default standing in for a decision: the stock word, the padded paragraph, the sentence that explains what the reader already sees.

Two rules bound everything: never add a fact that was not supplied or verified, and do not over-sterilize. Judge clusters of tells, not a single one. Keep the specific detail, the varied sentence length and the author's voice. A writing sample from the user overrides the style rules here.

## Pick the mode

- **Detect**: the user asks whether or why a text reads as AI. Name each pattern, quote the line, give the fix in a few words. Do not rewrite.
- **Edit**: the user's own draft. Make the minimum effective edit; two passes at most; preserve meaning, facts and voice. List what changed.
- **Draft**: new text. Lead with the point; use only supplied or verified facts; mark gaps with a visible placeholder or a question.

## Tests

- Delete: remove the sentence. Would the reader act differently? If not, cut.
- Portability: would the paragraph fit another product or topic unchanged? Then it says nothing yet.
- Reshuffle: can the paragraphs be reordered with no loss? Then there is no argument.
- Already shown: does the text repeat what the screen, table or code shows?

## Tells

Structure
- "Not X but Y", "it's not just X, it's Y", chains of negations.
- Forced triads; every paragraph the same length; staccato fragments for drama.
- Openers and closers that only announce or recap; a moral at the end of each section.
- Headings and bullets used as scaffolding: more than three headings under 300 words, or eight bullets under 200.
- `- **Label:** text` lists where a sentence would do; mechanical bold; emoji in headings.

Content
- Inflated significance ("plays a crucial role", "a testament to").
- Unnamed authority, speculative filler ("likely founded in"), false ranges ("from X to Y").
- Abstract subjects doing human things; passive voice hiding who acts.
- Synonym rotation for one concept; stacked hedges.
- Chat residue: praise, apologies, "I hope this helps", writing about the document itself.

Chinese
- Mainland vocabulary in a Taiwan text (see the list in `writing.md`).
- Translated-English scaffolding: 「值得注意的是」「總而言之」「不僅…更…」「在當今…的時代」「讓我們一起…」「扮演著重要的角色」「進行…的動作」.
- 「——」 as a dramatic pause; half-width punctuation in Chinese sentences.
- Four-character filler and slogan pairs that add no fact.

English
- Em dashes; the cut-on-sight words in `writing.md`; title-case list items; "in order to".

## Code comments

Only comments change. Never touch code, identifiers, formatting or whitespace.

- Remove: restated code, step narration, banners, empty labels, vague TODOs, signature echoes, emoji, end markers, edit history.
- Shorten: a paragraph around a one-line fact becomes that one line.
- Keep: business rules, constraints, protocol and API contracts, security and concurrency notes, workarounds, licences.

## Finish

Read the result once more against the user's request and language. Report which patterns were removed and anything that needs a fact from the user.
