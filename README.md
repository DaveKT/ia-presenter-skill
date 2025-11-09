# IA Presenter Skill for Claude

A Claude skill that generates markdown presentations compatible with [IA Presenter](https://ia.net/presenter), enabling rapid creation of professional presentations from any content source.

## Overview

This skill extends Claude's capabilities to create properly formatted IA Presenter markdown files. IA Presenter uses a specific markdown syntax with unique conventions for slide separation, content visibility, and layout control. This skill ensures Claude generates presentations that follow these conventions correctly.

## Features

- **Automatic Format Compliance**: Generates markdown that follows IA Presenter's specific syntax requirements
- **Intelligent Content Structuring**: Creates presentations with logical flow (cover, executive summary, content, conclusion)
- **Concise Presentation Design**: Focuses on impactful keywords and minimal text per slide
- **Flexible Input**: Works with plain text, documents (PDF/Word), data reports, or conversational prompts
- **Image Integration**: Handles image paths and placement with proper IA Presenter syntax
- **Interactive Generation**: Asks clarifying questions to tailor presentations to your needs

## Installation

1. Download the `ia-presenter.skill` file from the releases
2. In Claude.ai, click on your profile and navigate to Settings
3. Go to the "Skills" section
4. Click "Upload Skill" and select the `ia-presenter.skill` file
5. The skill will now be available in all your conversations

## Usage

### Trigger Phrases

The skill activates when you ask Claude to:
- "Create an IA Presenter presentation about [topic]"
- "Generate an IA Presenter document from this content"
- "Convert this to IA Presenter format"
- "Make a markdown presentation about [topic]"

### Example Prompts

```
Create an IA Presenter presentation about our Q4 sales results
```

```
Generate an IA Presenter deck from this meeting transcript [attach file]
```

```
Convert this report into a 10-slide IA Presenter presentation
```

### What Claude Will Ask

Before generating your presentation, Claude may ask:
- What's the presentation topic and target audience?
- What are the key messages or objectives?
- How many slides do you need?
- Do you have any images to include? (and what they depict)
- Any specific content structure preferences?

### Output

Claude creates a `.md` file with proper IA Presenter formatting that you can:
- Open directly in IA Presenter
- Edit with any text editor
- Version control with Git
- Share with your team

## IA Presenter Syntax Highlights

The skill handles these IA Presenter-specific conventions:

- **Slide Separation**: Uses `---` to separate slides
- **Content Visibility**: Tab characters make content visible on slides; non-tabbed lines are speaker notes
- **Side-by-Side Layouts**: Separates tabbed sections with non-tabbed lines
- **Image Paths**: All images use `/assets/` prefix
- **Cover Slides**: `# Title` and `## Subtitle` format

## Example Output Structure

```markdown
# Quarterly Business Review
## Q4 2024 Results

---
### Executive Summary

	Revenue exceeded targets by 15%
	Customer satisfaction at all-time high
	Three new strategic partnerships formed

---
### Revenue Growth

	Q4 Revenue: $2.5M
	Year-over-year growth: 23%

/assets/revenue-chart.png
size: contain
```

## Contents

This skill includes:
- **SKILL.md**: Complete instructions for Claude on generating IA Presenter markdown
- **references/Example_IA_Presenter_Deck.md**: A working example demonstrating all syntax features

## Best Practices

When using this skill:
1. Provide clear context about your presentation topic and audience
2. If you have images, describe what they depict so Claude can place them appropriately
3. Specify if you need a particular number of slides or structure
4. Review and customize the generated markdown as needed

## Resources

- [IA Presenter Official Site](https://ia.net/presenter)
- [IA Presenter Markdown Documentation](https://ia.net/presenter/support/basics/markdown)

## Contributing

Feedback and contributions are welcome! If you find issues or have suggestions for improving the skill:
1. Open an issue describing the problem or enhancement
2. Include example prompts and expected vs. actual behavior
3. For bugs, include the generated markdown that's causing issues

## License

This skill is provided as-is for use with Claude and IA Presenter.

## Version History

- **v1.0.0** (2024-11-09): Initial release
  - Core IA Presenter markdown generation
  - Tab character handling for content visibility
  - Image path formatting with `/assets/` prefix
  - Interactive question-based generation
  - Example reference file included

---

Built for Claude by users who believe in the power of great presentations.
