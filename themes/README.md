# Themes

Four looks for thermonerds.com. Each is a self-contained Quarto SCSS theme:
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
- Tabular figures in tables, uppercase small-caps headers.

## Fonts

`_quarto.yml` loads all five families the four themes draw on: Source Serif 4,
IBM Plex Sans, IBM Plex Mono, Inter and JetBrains Mono. Once you have picked a
theme, delete the `<link>` lines for the families it does not use — each is a
separate request on every page load.

## Keeping one

Nothing depends on the filename. When you settle on one you can leave it in
`themes/`, or move it back to the project root as `theme.scss` and point
`_quarto.yml` at that.
