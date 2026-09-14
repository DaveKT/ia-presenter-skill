---
name: ia-presenter
description: Create or edit Markdown presentations compatible with IA Presenter, including native tables and charts. Use when the user requests an IA Presenter presentation, adds tables or charts to an IA Presenter deck, or converts content into an IA Presenter Markdown file. Also use when the user asks to create a presentation in Markdown format without specifying a tool.
license: MIT
metadata:
  version: "1.2.0"
---

# IA Presenter

Create concise, well-structured Markdown presentations that follow IA Presenter's syntax. This is an Agent Skills-compatible skill; use the host agent's available file tools and output conventions rather than assuming a product-specific directory.

## Overview

This skill generates Markdown files formatted for IA Presenter, a presentation tool with specific Markdown syntax requirements. IA Presenter uses standard Markdown with unique conventions for slide separation, content visibility, and layout control.

## Core Syntax Rules

### Slide Structure

Use heading levels to control slide hierarchy:
- `# Title` and `## Subtitle` on the first slide create the cover page
- `---` separates slides
- `### Heading` creates content slide titles (always visible)

### Content Visibility

Control what appears on slides using tab characters:
- Lines starting with a **tab character** appear on the slide
- Ordinary text paragraphs without tabs are speaker notes (invisible to audience)
- Headings always appear and don't need tabs
- Markdown tables and their chart metadata start at the beginning of the line, without tabs; they are not ordinary speaker-note paragraphs

**Critical:** Use actual tab characters (`\t`), not the tab symbol or spaces.

### Layout Control

Create side-by-side layouts by separating tabbed content with a non-tabbed line:
```
	Left panel content

	Right panel content
```

Without the separator, content stacks vertically.

### Line Breaks, Blank Slide Lines, and List Separation

Use different syntax for these three cases:

- To insert a line break inside one paragraph, end the preceding line with two spaces or a backslash (`\`). Keep the tab prefix on both lines when the paragraph must appear on the slide.
- To create a visually blank line outside lists, insert a slide-content line containing exactly an actual tab character (`U+0009`) followed by an actual non-breaking space (`U+00A0`). Ordinary blank Markdown lines collapse in the HTML view and do not guarantee visible vertical space. Use the literal non-breaking space character, never an HTML entity spelling.
- To separate consecutive lists, use a blank line, a tab-prefixed standalone backslash, and another blank line before the next list. This prevents the HTML view from treating the second list as a continuation of the first.

The visually blank middle line below contains exactly `TAB + U+00A0`:

```markdown
	Text above the blank line
	 
	Text below the blank line
```

Separate list types like this:

```markdown
	1. First ordered item
	2. Second ordered item

	\

	**A separate list**
	- First bullet
	- Second bullet
```

Do not use the non-breaking-space spacer between lists because it can preserve unwanted list continuity. A standalone backslash is a list-boundary workaround, not a general-purpose way to add vertical space.

## Creating Presentations

### Standard Structure

Follow this typical flow:
1. Cover slide (# Title, ## Subtitle)
2. Executive summary or key message slide
3. Content slides with concise points
4. Conclusion or next steps slide

### Content Guidelines

Keep text minimal and impactful:
- Use bullets and short phrases over paragraphs
- Focus on keywords that reinforce spoken content
- Avoid long sentences that distract from the presenter
- Prioritize visuals (images, graphs) when available

### Gathering Information

Use the information already provided by the user first. Ask clarifying questions only when an answer is needed to produce a useful presentation:
- Presentation topic and target audience
- Key messages or objectives
- Number of slides needed
- Whether images are available (and what they depict)
- Any specific content structure preferences

### Images

Handle images as follows:
- All image paths start with `/assets/`
- Example: `/assets/myimage.jpg`
- Use `size: contain` on the line after the image path to fit the full image
- If the user provides images, ask what each depicts only when that context is needed for placement
- If no images are provided, skip image syntax; do not invent image paths

### Tables and Charts

For native tables and charts, read [Tables and Charts](references/tables-and-charts.md) before generating or editing them. Chart support requires iA Presenter 1.6 or later.

- Generate editable Markdown tables with chart metadata directly below the final data row, without indentation or code fences in the output deck.
- Use tables for exact values, bars for category comparisons, lines for trends, and pies for simple parts of a whole.
- Preserve supplied labels and values. Clearly identify invented example data as fictional in speaker notes.
- Use only the documented metadata values and combinations in the reference. Do not invent CSV-block syntax or additional chart options.

### Formatting

Standard Markdown works within IA Presenter:
- `**bold**` for bold text
- `*italic*` for italic text
- `[link text](url)` for hyperlinks
- Backtick code blocks with optional language: ` ```python `
- Ordered lists: `1.`, `2.`, etc.
- Unordered lists: `-` or `*`

## Output Format

Create a `.md` file containing the IA Presenter formatted content in the output directory specified by the user. If no output directory is specified, use the host agent's designated file-writing mechanism or current working directory. Do not assume a product-specific path such as `/mnt/user-data/outputs/`. If the host agent cannot create files, return the complete Markdown content in the response and clearly label it as an IA Presenter Markdown document.

Use a short, descriptive filename with the `.md` extension. Preserve actual tab characters wherever IA Presenter requires visible slide content.

## Reference Example

See `references/Example_IA_Presenter_Deck.md` for a complete working example demonstrating core syntax, a table, and the three chart types.

## Additional Resources

Full IA Presenter markdown documentation: https://ia.net/presenter/support/basics/markdown

Tables and charts documentation: https://ia.net/presenter/support/story/tables-and-charts
