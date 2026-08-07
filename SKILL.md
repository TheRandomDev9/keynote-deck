---
name: keynote-deck
description: Build a self-contained, presentation-ready HTML slide deck with an editorial dark-keynote aesthetic, keyboard navigation, scroll-snap slides, and one-click PDF export. Use when someone asks to make a presentation, slide deck, keynote, or to turn notes into slides they will present live or share.
version: 1.0.0
license: MIT
triggers:
  - build a slide deck
  - make a presentation
  - create a keynote
  - turn this into slides
  - presentation deck
  - pitch deck
---

# Keynote Deck

Produce a single self-contained `.html` file that is a real, presentable slide
deck: full-screen slides, arrow-key navigation, a considered dark editorial
look, and a clean landscape PDF export. No build step, no framework, no
external assets. The presenter opens the file, presses **F**, and talks.

This skill encodes a complete method, not a single template: a design system,
a set of slide archetypes to compose from, keyboard and scroll mechanics, and
the print rules that make the PDF match the screen. Follow it and the output
looks intentional, not generated.

## When to use it

Reach for this whenever the deliverable is a deck someone will stand in front
of or paste into a chat: a talk, a pitch, a product walkthrough, a readout.
Not for a document meant to be read top to bottom (that is prose), and not for
a dashboard (that is a UI).

## Build it in four moves

1. **Copy the skeleton.** Start from `reference/deck-template.html`. It is a
   working deck: the full CSS design system, the navigation script, the print
   rules, and one example slide. Everything below fills it in.
2. **Write the arc, then the slides.** Decide the story first, one idea per
   slide, five to eight slides for most talks. Open on the problem or the hook,
   not on your product. Then build each slide from an archetype in
   `reference/slide-patterns.md` (cover, two-column, contrast cards, value
   chips, anatomy table, two-mechanism, role-split, terminal, report cards).
   Compose, do not repeat: identical card grids read as filler.
3. **Number the pages.** Give every `<section class="slide">` a
   `data-page="N / TOTAL"` attribute. The on-screen counter is automatic, but
   the PDF footer reads this attribute, so keep it correct.
4. **Verify the PDF.** Export once and look at every page (see
   `reference/pdf-export.md`). The single most common defect is a slide that
   renders on screen but goes blank in the PDF; that file explains exactly why
   and how the template already prevents it.

## The design system

The template ships one committed look: a warm dark "roast" keynote, espresso
grounds with a clay-orange accent. It is deliberately not the default
cream-and-terracotta or acid-on-black that generated decks fall into. You may
retheme it, but change the tokens, never scatter hex values through the slides.

**Color** lives in CSS custom properties on `:root`:

- Grounds: `--ground` (page), `--panel` (cards). Deep, warm, never pure black.
- Text: `--paper` (headings), `--sand` (body), `--muted` (captions),
  `--faint` (chrome).
- One accent: `--clay` for text accents, `--clay-deep` for fills. Spend it
  sparingly; an accent used everywhere stops being one.
- Semantic only where meaning is carried: `--ok` `--warn` `--err`. These are
  not decoration and are separate from the accent.

To retheme, pick a new ground hue and a single accent, tint the neutrals
slightly toward the accent so they read as chosen, and keep the semantic
colors. A calm subject wants a calmer accent; a bold one can drench.

**Type**: one strong grotesque sans for headings and body, one mono for
labels, code, and data. Headings are large with tight negative tracking; mono
labels are small with wide positive tracking and uppercase. That contrast, sans
display against mono metadata, carries the whole personality. Cap body lines
near 65 characters.

**Ambient**: a faint radial accent glow and a low-opacity dotted grid, fixed
behind the slides. Atmosphere, not noise. Leave it subtle.

## Motion

One reveal on slide entry, staggered by a few milliseconds per element, easing
out. That is enough. Do not animate on every element or every transition;
scattered motion is the tell of a generated deck. The template already respects
`prefers-reduced-motion` and reveals everything for print.

## Copy craft

- One idea per slide. If a slide has two ideas, it is two slides.
- Open on the problem, the tension, or a concrete hook. Earn the product later.
- Write real content, never placeholder. Specific beats clever.
- Active voice. A stat means something only next to what it is compared to.
- Keep punctuation calm: prefer colons, periods, and parentheses to dashes.

## What good output looks like

A file you would be proud to present: every slide composed from a distinct
archetype, the accent used two or three times total, headings that balance
onto two lines cleanly, a PDF whose pages match the screen exactly, and copy
that sounds like a person talking, not a spec sheet. If a slide could be any
deck's slide, rewrite it until it could only be this one's.

## References

- `reference/deck-template.html` — the working skeleton to copy and fill.
- `reference/slide-patterns.md` — copy-paste HTML for every slide archetype.
- `reference/pdf-export.md` — how to export a clean landscape PDF, and the one
  print gotcha that silently blanks a slide.
