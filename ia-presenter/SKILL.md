---
name: ia-presenter
description: Create or edit markdown presentations compatible with iA Presenter, including native tables and charts. Use when the user requests an iA Presenter presentation, adds tables or charts to an iA Presenter deck, or converts content into an iA Presenter markdown file. Also use when the user asks to create a presentation in markdown format without specifying a tool.
---

# IA Presenter

## Overview

This skill generates markdown files formatted for IA Presenter, a presentation tool with specific markdown syntax requirements. IA Presenter uses standard markdown with unique conventions for slide separation, content visibility, and layout control.

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

Before generating, ask clarifying questions:
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
- If user provides images, ask what each depicts to place appropriately
- If no images provided, skip image syntax (user will add later)

### Tables and Charts

For native tables and charts, read [Tables and Charts](references/tables-and-charts.md) before generating or editing them. Chart support requires iA Presenter 1.6 or later.

- Generate editable Markdown tables with chart metadata directly below the final data row, without indentation or code fences in the output deck.
- Use tables for exact values, bars for category comparisons, lines for trends, and pies for simple parts of a whole.
- Preserve supplied labels and values. Clearly identify invented example data as fictional in speaker notes.
- Use only the documented metadata values and combinations in the reference. Do not invent CSV-block syntax or additional chart options.

### Formatting

Standard markdown works within IA Presenter:
- `**bold**` for bold text
- `*italic*` for italic text
- `[link text](url)` for hyperlinks
- Backtick code blocks with optional language: ` ```python `
- Ordered lists: `1.`, `2.`, etc.
- Unordered lists: `-` or `*`

## Output Format

Create a `.md` file with the IA Presenter formatted content in the output directory specified by the user; otherwise use the current working directory.

## Reference Example

See `references/Example_IA_Presenter_Deck.md` for a complete working example demonstrating core syntax, a table, and the three chart types.

## Additional Resources

Full IA Presenter markdown documentation: https://ia.net/presenter/support/basics/markdown

Tables and charts documentation: https://ia.net/presenter/support/story/tables-and-charts
