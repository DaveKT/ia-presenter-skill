# Tables and Charts

Use this reference when creating or editing native tables and charts in iA Presenter. Charts require version 1.6 or later. The ten examples below reproduce the Markdown data and metadata from a user-supplied iA Presenter example document. All example data is fictional.

## Table structure and placement

- Write a header row, an alignment/divider row, and data rows using pipe (`|`) separators. Keep a consistent number of columns and each cell on one line.
- Start table rows at column one, without tabs or spaces before the first pipe. These blocks are visible content, unlike ordinary unindented speaker-note paragraphs.
- Use the first column for category labels and subsequent columns for numeric series. The blank top-left cell in the examples is intentional.
- Use `:---`, `---:`, or `:---:` in the divider row for left, right, or center alignment respectively.
- Place chart metadata immediately after the final table row, one setting per line, without indentation or an intervening blank line. Separate other slide content with a blank line and slides with `---`.
- The code fences below delimit examples in this reference only. Omit them when inserting a table or chart into a generated presentation.
- Preserve the user's labels, values, units, and ordering. Ask for missing data when needed; do not silently replace it with invented values. Identify fictional examples in speaker notes.

## Supported metadata

| Key | Values demonstrated | Usage |
| --- | --- | --- |
| `chart` | `line`, `bar`, `pie` | Omit for a plain table. |
| `Line-Type` | `steps` | Only with `chart: line`; omit for ordinary lines. |
| `Orientation` | `vertical`, `horizontal` | Only with `chart: bar`. |
| `Bar-Type` | `stacked` | Only with `chart: bar`; omit for ordinary, non-stacked bars. |
| `Color-Type` | `categorical`, `sequential`, `differential` | Demonstrated with horizontal stacked bars below. |

Use the spelling shown here. The source contains both `Color-type` and `Color-Type`; the examples normalize to `Color-Type`, which also appears in the source. This is not a general guarantee of case-insensitive parsing. Do not invent values such as `normal` or `grouped`, or assume that every option works with every chart type. CSV blocks and other chart options are not specified by this reference.

## Choosing a representation

- **Table:** exact values or mixed textual and numeric comparisons.
- **Bar:** comparison between categories. Default to vertical, non-stacked bars; horizontal bars can accommodate longer category names.
- **Line:** an ordered progression, such as time. Default to ordinary lines; use steps only when the data represents discrete changes or the user requests them.
- **Stacked bar:** additive components whose combined total is meaningful, or an explicitly requested stacked view.
- **Pie:** a small, simple set of nonnegative parts of one meaningful whole. Prefer a single numeric series for new pie charts. The two-series pie below is retained from the supplied syntax example; do not silently discard a supplied series.
- Leave color metadata out by default. Use an explicit color variant when requested, preserving the demonstrated combination until other combinations have been verified.

Keep slides readable and avoid overcrowding. Preserve the requested representation when valid; explain a data mismatch instead of changing or aggregating values silently.

## Complete examples

### Plain table

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
```

### Line chart

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: line
```

### Stepped line chart

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: line
Line-Type: steps
```

### Vertical bar chart

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: bar
Orientation: vertical
```

### Stacked vertical bar chart

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: bar
Orientation: vertical
Bar-Type: stacked
```

### Horizontal bar chart

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: bar
Orientation: horizontal
```

### Stacked horizontal bar chart with categorical colors

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: bar
Bar-Type: stacked
Orientation: horizontal
Color-Type: categorical
```

### Stacked horizontal bar chart with sequential colors

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: bar
Bar-Type: stacked
Orientation: horizontal
Color-Type: sequential
```

### Stacked horizontal bar chart with differential colors

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: bar
Bar-Type: stacked
Orientation: horizontal
Color-Type: differential
```

### Pie chart

```markdown
|         | Series 1 | Series 2 |
| :------ | :------- | :------- |
| Group A | 10       | 15       |
| Group B | 15       | 20       |
| Group C | 25       | 30       |
chart: pie
```

## Sources and verification

- [iA Presenter Markdown Guide](https://ia.net/presenter/support/basics/markdown): table syntax and alignment.
- [Tables and Charts](https://ia.net/presenter/support/story/tables-and-charts): native tables, charts, and editor controls.
- [Version History](https://ia.net/presenter/support/help/version-history-release-notes): chart support in version 1.6.
- The ten examples above use the data and metadata from a user-supplied `charts.iapresenter/text.md`; package identifiers and thumbnails are intentionally excluded.

When changing these examples, compare the data and options against that source and check rendering in iA Presenter. Check values and series, line steps, bar orientation and stacking, color variants, and pie rendering. Also check an ordinary tab-prefixed text slide with speaker notes. Report text-only validation separately if visual validation is unavailable.
