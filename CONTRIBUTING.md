# Contributing to MarkForge

Thank you for helping improve MarkForge.

## Scope

This repository is a Codex skill focused on controlled polishing of Chinese Markdown documents. Contributions should strengthen one or more of the following:

- Skill instructions in `SKILL.md`
- UI metadata in `agents/openai.yaml`
- Reference materials under `references/`
- Public project documentation at the repository root

## Contribution Priorities

High-value contributions usually fall into these categories:

- Sharper level boundaries between Level 1, Level 2, and Level 3
- Better protection rules for numbered headings, code blocks, tables, images, and quoted content
- Stronger formal written tone rules for Chinese technical or teaching documents
- Better section templates for concept explanation, configuration guidance, comparison, or case-based exposition
- More realistic edge cases collected from long-form Markdown materials

## Local Validation Checklist

Before opening a pull request, verify the following:

- Heading numbering examples remain intact
- Markdown code fences, lists, and tables are not broken
- Root documentation matches the current behavior of `SKILL.md`
- Examples do not contradict the declared level boundaries
- Tone guidance does not introduce conversational or second-person phrasing into formal document rules

## Pull Request Process

1. Create a branch from `main`.
2. Keep changes focused and explain the editing rationale clearly.
3. Update documentation when behavior, examples, or installation steps change.
4. Include before-and-after snippets when changing polishing rules or reference guidance.
5. Open a pull request with a concise summary of the problem and the proposed improvement.

## Issue Guidance

When reporting an issue, include:

- The document pattern that triggered the problem
- The intended polishing level
- The current output behavior
- The expected behavior

Minimal reproducible Markdown snippets are especially helpful.

## License

By contributing to this repository, contributions are submitted under the same [MIT License](LICENSE) that governs the project.
