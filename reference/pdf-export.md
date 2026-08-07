# Exporting a clean PDF

The deck is landscape, one slide per page. There are two ways to export, and one
gotcha that silently ruins the output if you skip the check.

## The easy way: the button

Open the deck in a browser and click **Save as PDF** (top-left), or press
`Cmd/Ctrl-P`. In the print dialog:

- **Destination:** Save as PDF
- **Layout:** Landscape
- **Margins:** None
- **Background graphics:** ON (this is what makes the dark slides render)

The `@media print` rules in the template already force one slide per page and
re-reveal every slide, so what you see on screen is what lands in the PDF.

## The scriptable way: headless Chrome

For a repeatable export (CI, a build step, generating on a server):

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="Deck.pdf" \
  "file:///absolute/path/to/deck.html"
```

On Linux use `google-chrome` or `chromium`. The `@page { size: 1280px 720px }`
rule in the template fixes the page geometry, so you do not need to pass a paper
size.

## The one gotcha: a slide that blanks in the PDF only

**Symptom:** a slide looks perfect on screen but comes out empty (or badly
overflowing) in the PDF — usually the tallest, most content-dense one.

**Cause:** headless print evaluates `@media (max-width: …)` queries against a
narrow layout width, not your monitor. Every responsive grid in the deck
(`.two`, `.mech`, `.qcontrast`, `.reports`, `.stat-grid`) has a mobile
breakpoint that collapses it to a single column. When that fires during print,
the slide's content stacks vertically, grows past the fixed 720px page height,
and the overflow is clipped to nothing.

**The fix is already in the template** — this block re-asserts the desktop grids
at print time so nothing collapses:

```css
@media print {
  .two { grid-template-columns: 1.05fr 1fr !important; }
  .mech, .qcontrast, .reports { grid-template-columns: 1fr 1fr !important; }
  .stat-grid { grid-template-columns: repeat(4, 1fr) !important; }
  .tags, .valuechips { flex-wrap: nowrap !important; }
}
```

If you add a **new** archetype with its own responsive breakpoint, add a
matching `!important` desktop override to this block, or that slide will be the
next one to blank.

## Always do the final check

Export the PDF and look at **every** page, not just the first. Confirm:

- No blank pages (the gotcha above).
- Page numbers in the footer read correctly — they come from each slide's
  `data-page` attribute, which you set by hand, so a wrong `TOTAL` shows here.
- Dark backgrounds rendered (Background graphics was on).
- No slide's content is clipped at the bottom edge.

A deck is a thing people share as a PDF as often as they present it live. The
export is not an afterthought; it is half the deliverable.
