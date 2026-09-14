# IA Presenter Agent Skill

An [Agent Skills](https://agentskills.io/) compatible skill for creating concise Markdown presentations that work with [IA Presenter](https://ia.net/presenter).

## What it does

The skill helps an agent:

- create IA Presenter Markdown from a topic, outline, report, transcript, or other source material;
- structure a presentation with a cover, key messages, content slides, and conclusion;
- apply IA Presenter's slide-separation, visibility, layout, and image conventions;
- keep visible slide content concise while preserving speaker notes;
- produce a `.md` file using the host agent's normal file-output mechanism.

## Skill layout

The canonical skill directory is [`ia-presenter/`](ia-presenter/):

```text
ia-presenter/
├── SKILL.md
└── references/
    └── Example_IA_Presenter_Deck.md
```

The repository root contains documentation, licensing, and distribution files. Clients that discover skills from directories should be pointed at `ia-presenter/`, not at the repository root.

## Installation

### Agent Skills-compatible clients

Copy or register the [`ia-presenter/`](ia-presenter/) directory in the location where your client discovers Agent Skills. The directory must remain intact so that `SKILL.md` and its `references/` directory stay together.

### Claude

The repository also contains [`ia-presenter.skill`](ia-presenter.skill), a packaged distribution for clients that support Claude's `.skill` upload format. Upload that file through the client's skill settings. The plain `ia-presenter/` directory is the canonical Agent Skills representation.

## Usage

The skill is relevant for requests such as:

- “Create an IA Presenter presentation about our Q4 sales results.”
- “Turn this meeting transcript into a presentation.”
- “Convert this report into a 10-slide IA Presenter Markdown file.”
- “Create a Markdown presentation about this topic.”

When essential information is missing, the agent may ask about the audience, objectives, slide count, available images, or preferred structure. It should use the context already supplied before asking questions.

## IA Presenter conventions

- `---` separates slides.
- `# Title` and `## Subtitle` create the cover slide.
- `### Heading` creates a content-slide heading.
- Lines beginning with an actual tab character are visible on the slide.
- Lines without a tab are speaker notes, except headings, which are always visible.
- A non-tabbed line separates tabbed sections into side-by-side panels.
- Images use IA Presenter's `/assets/` syntax and may be followed by `size: contain`.

See the [example deck](ia-presenter/references/Example_IA_Presenter_Deck.md) for a complete example.

## Validation

The official reference validator can be used to check the skill directory:

```bash
skills-ref validate ./ia-presenter
```

See the [Agent Skills specification](https://agentskills.io/specification) for the required directory structure and metadata rules.

## Resources

- [IA Presenter](https://ia.net/presenter)
- [IA Presenter Markdown documentation](https://ia.net/presenter/support/basics/markdown)
- [Agent Skills](https://agentskills.io/)

## Contributing

When proposing changes, keep the canonical skill in `ia-presenter/`, update the version metadata when behavior changes, and validate the directory with `skills-ref validate ./ia-presenter`.

## License

This project is licensed under the [MIT License](LICENSE).
