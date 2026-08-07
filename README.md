# keynote-deck

A Claude skill for building a **self-contained, presentation-ready HTML slide
deck** — full-screen slides, arrow-key navigation, a considered dark editorial
look, and a clean landscape PDF export. No build step, no framework, no external
assets. The presenter opens one `.html` file, presses **F**, and talks.

## What it produces

A single HTML file that is a real deck:

- **Scroll-snap slides**, one per viewport, with a progress rail and page counter.
- **Keyboard navigation** — arrow keys / space / `PageUp` / `PageDown` to move,
  `Home` / `End` to jump, `F` for full screen.
- **One considered look** — a warm dark "roast" keynote palette with a single
  clay accent, a sans/mono type pairing, and subtle ambient atmosphere. Retheme
  by editing tokens, not by scattering hex values.
- **One-click PDF export** — a landscape PDF, one slide per page, that matches
  the screen. Share it in chat or email as easily as you present it.

It is a method, not one template: a design system, a library of slide
archetypes to compose from, motion and keyboard mechanics, and the print rules
that keep the PDF faithful to the screen.

## Using it

Ask Claude (with this skill available) to build a presentation:

> "Build me a slide deck introducing our new eval tool to a launch audience."

Claude copies the skeleton, writes the arc, composes each slide from a distinct
archetype, numbers the pages, and verifies the PDF exports cleanly.

## What's inside

| File                            | Purpose                                                        |
| ------------------------------- | ------------------------------------------------------------- |
| `SKILL.md`                      | The method: design system, build moves, copy craft.           |
| `reference/deck-template.html`  | The working skeleton — full CSS, nav script, print rules.     |
| `reference/slide-patterns.md`   | Copy-paste HTML for every slide archetype.                    |
| `reference/pdf-export.md`       | How to export a clean PDF, and the one gotcha that blanks a slide. |

## Try the template on its own

`reference/deck-template.html` is a runnable two-slide deck. Open it in any
browser to see the look, the navigation, and the PDF export before writing a
single slide of your own.

## License

MIT — see [LICENSE](LICENSE).
