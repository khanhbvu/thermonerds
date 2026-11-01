# Themes

Eight looks for thermonerds.com. Each is a self-contained Quarto SCSS theme:
Bootstrap variables in `scss:defaults`, everything else in `scss:rules`.

## Switching

One line in `_quarto.yml`:

```yaml
format:
  html:
    theme:
      - cosmo
      - themes/theme-datum.scss     # <- change this
```

Then `quarto preview`. No other file changes.

| File | Look |
| --- | --- |
| `theme-preprint.scss` | Warm paper, Source Serif throughout, oxblood titles, rules between posts. The academic one. |
| `theme-datum.scss` | White, teal accent, Inter headings over serif body, listing posts as bordered cards. |
| `theme-obsidian.scss` | Dark. Cyan accent, JetBrains Mono headings, equations in bordered panels. |
| `theme-ledger.scss` | High contrast black on white, heavy tight Inter, single red accent, thick rules. |
| `theme-journal.scss` | A typeset paper. Crimson Pro at 21px on a 36em measure, justified with hyphenation, paragraphs indented rather than spaced, small-caps section heads. |
| `theme-lab.scss` | Engineering report. Cool greys, one steel blue, the IBM Plex family throughout, equations in bordered boxes, striped tables, mono captions. |
| `theme-monograph.scss` | Scholarly book. Spectral at 1.82 leading, deep green accent, small-caps heads, no boxes or cards anywhere. |
| `theme-eink.scss` | An e-reader panel. Warm paper rather than white, soft near-black rather than true black, Literata, and no colour at all — links are underlined, code is greyscale, nothing is rounded or shadowed. |

## On the e-ink one

`theme-eink.scss` imitates a Paperwhite under warm light, which drives three
choices. Contrast is deliberately held near 13:1 rather than pushed to 21:1,
because a real e-ink panel tops out around 15:1 and true black on true white
reads as a screen, not paper. **Nothing is coloured** — a greyscale display
cannot signal with hue, so links carry an underline and a highlighter block on
hover, and syntax highlighting is a range of greys. And text is **justified
with automatic hyphenation**, the way an e-reader sets a page; if that opens
rivers at your window width, change the single `text-align: justify` to `left`.

Table headers in this theme are deliberately *not* uppercased, unlike the other
seven. On a maths site `text-transform: uppercase` renders a header reading
"Δx range" as "ΔX RANGE", and ΔX is a different symbol from Δx.

## On the paper-like ones

`theme-journal.scss` makes two choices that are standard in print and unusual
on the web: text is **justified with automatic hyphenation**, and consecutive
paragraphs are **indented instead of separated by a blank line** (the first
paragraph after a heading is not indented, which is the correct convention).
It is the most authentically article-like of the set. If you want the look but
not the indents, delete the two `text-indent` rules; if you want it unjustified,
change `text-align: justify` to `left`.

## What they all share

- **Listing titles are visually distinct from body text** — larger, heavier,
  and in a different colour. This was the problem with the original
  `theme.scss`: nothing targeted `.listing-title`, so post titles inherited
  the body colour and the listing read as a wall of text.
- **Display equations scroll in their own box** rather than widening the page
  on a phone. Quarto's stock themes do not do this, and with derivations the
  width of `A_res` it matters.
- Tabular figures in tables, and small-caps headers (uppercased in every
  theme but `theme-eink.scss`, for the reason given above).

## Fonts

`_quarto.yml` loads every family the eight themes draw on: Source Serif 4,
IBM Plex Sans, IBM Plex Serif, IBM Plex Mono, Inter, JetBrains Mono, Crimson
Pro, Spectral and Literata. Once you have picked a theme, delete the `<link>`
lines for the families it does not use — each is a separate request on every
page load. `theme-eink.scss` needs only Literata and IBM Plex Mono.

## Keeping one

Nothing depends on the filename. When you settle on one you can leave it in
`themes/`, or move it back to the project root as `theme.scss` and point
`_quarto.yml` at that.
