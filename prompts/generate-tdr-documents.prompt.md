---
mode: 'agent'
tools: ['codebase', 'markdownlint']
description: 'Generate Technical Debt Records based on the current project.'
---

Generate TDRs based on the current state of the project.

- For each debt item, create a Markdown file in `docs/tdr/` using the format `NNNN-<slug>.md`.
- Use this structure: Title, Type, Affected Area, Description, Risk Level, Cause (blank), Potential Mitigation.
- If prior analysis is available, use it. Otherwise analyze code and documentation directly.
