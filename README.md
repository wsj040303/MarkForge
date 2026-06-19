# MarkForge

![MarkForge logo](assets/logo.png)

MarkForge is a Codex skill for controlled polishing of Chinese Markdown documents. It preserves heading numbering, protects code blocks and examples, and applies one of three editing intensities so document cleanup stays within explicit rewriting boundaries.

## What It Does

- Fixes typos, awkward sentences, terminology drift, and Markdown formatting issues
- Normalizes uneven section structure while preserving the original meaning
- Supports deeper editorial refinement for thin or redundant sections when explicitly allowed
- Keeps formal written tone for tutorials, project documents, lecture notes, and long structured materials
- Preserves numbered headings such as `2.1.1` and `8.5.3` by default

## Editing Levels

### Level 1

Surface cleanup only:

- Typos and malformed sentences
- Terminology, punctuation, spacing, and capitalization consistency
- Broken Markdown structure in headings, lists, tables, and fenced code blocks

This level does not change section order, paragraph logic, or substantive content.

### Level 2

Structural normalization on top of Level 1:

- Reorganizes uneven subsections
- Splits overlong paragraphs and merges fragmented ones
- Rewrites exposition for clearer instructional structure
- Applies stable section templates when needed without materially changing meaning

This level does not introduce new knowledge points or expand content aggressively.

### Level 3

Editorial strengthening on top of Level 2:

- Expands thin sections with necessary supporting explanation
- Compresses redundant sections
- Adds minimal examples, micro-cases, or configuration snippets
- Converts information dumps into clearer teaching-oriented exposition

This level still preserves the document's core intent and section purpose.

## Repository Structure

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── md-edge-cases.md
│   ├── style-rules.md
│   └── templates.md
└── assets/
    └── logo.png
```

## Install in Codex

Codex skills are loaded from `~/.codex/skills/<skill-name>`. The stable runtime skill name for this project is `markdown-doc-polisher`.

### Option 1: Clone directly into the skill directory

```bash
git clone https://github.com/wsj040303/MarkForge.git ~/.codex/skills/markdown-doc-polisher
```

### Option 2: Copy this repository into an existing Codex skills directory

```bash
mkdir -p ~/.codex/skills
cp -R /path/to/MarkForge ~/.codex/skills/markdown-doc-polisher
```

Restart Codex after installation so the new skill is discovered.

## Use the Skill

Typical request pattern:

```text
Use $markdown-doc-polisher to refine this Markdown document at level 2 while preserving heading numbering, formal tone, and core meaning.
```

If the user does not specify an editing level, the skill is designed to ask for one before editing.

## Key Rules

- Preserve explicit heading numbering already present in the source document
- Treat code blocks, prompts, JSON, YAML, shell snippets, and sample tables as protected examples by default
- Avoid conversational tone, second-person address, and tutorial-style filler phrases in formal documents
- Do not exceed the permitted rewrite boundary for the selected level

## Included References

- `references/style-rules.md`: rules for formal written Chinese tone
- `references/templates.md`: reusable section templates for levels 2 and 3
- `references/md-edge-cases.md`: handling rules for numbered headings, code blocks, tables, images, and quotes

## Contributing

Contributions are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for contribution guidelines.

## License

This project is released under the [MIT License](LICENSE).
