---
name: ia-presenter
description: Generate markdown presentations compatible with IA Presenter. Use when the user requests to create an IA Presenter presentation, generate an IA Presenter document, or convert content into an IA Presenter markdown file. Also use when the user asks to create a presentation in markdown format without specifying a tool.
license: MIT
metadata:
  version: "1.1.0"
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
- Lines without tabs are speaker notes (invisible to audience)
- Headings always appear and don't need tabs

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

### Formatting

Standard Markdown works within IA Presenter:
- `**bold**` for bold text
- `*italic*` for italic text
- `[link text](url)` for hyperlinks
- Backtick code blocks with optional language: ` ```python `
- Ordered lists: `1.`, `2.`, etc.
- Unordered lists: `-` or `*`

## Output Format

Create a `.md` file containing the IA Presenter formatted content using the host agent's designated output directory or file-writing mechanism. Do not assume a fixed path such as `/mnt/user-data/outputs/`. If the host agent cannot create files, return the complete Markdown content in the response and clearly label it as an IA Presenter Markdown document.

Use a short, descriptive filename with the `.md` extension. Preserve actual tab characters wherever IA Presenter requires visible slide content.

## Reference Example

See `references/Example_IA_Presenter_Deck.md` for a complete working example demonstrating all syntax features.

## Additional Resources

Full IA Presenter markdown documentation: https://ia.net/presenter/support/basics/markdown
