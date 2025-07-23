# MinionForge

MinionForge is a modular instruction system for AI models. It is designed to work with Claude Sonnet 4, GPT-based models, or any language model that supports XML-style prompts inside Markdown files.

The goal is to define precise, reusable, and role-based behaviors through structured prompt modules. This helps AI follow clear rules and adapt better to real-world project workflows.

## Motivation

Most prompts are just plain text, hard to maintain, hard to scale, and not always reliable.

MinionForge solves this by breaking down instructions into atomic units called **capabilities**, and loading only what each role needs. This brings consistency, context-awareness, and full control over how AI behaves across tasks like feature design, architecture, or implementation.

## Project Status

MinionForge is currently in active development and considered experimental. The format, tags, and conventions may change as we refine the design based on real-world usage with different models.

## References

- [Anthropic Claude Prompt Engineering Guide](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview)

## Components

MinionForge uses custom XML tags embedded in `.md` files. These tags define structure and intent, while keeping the text readable and easy to maintain.

| Tag             | Purpose                                                           |
|------------------|--------------------------------------------------------------------|
| `<role>`         | Declares the identity and purpose of the AI agent.                |
| `<responsibility>` | Lists what this role is expected to deliver.                    |
| `<default-behavior-rules>` | Declares global rules shared by all roles and capabilities. Only allowed in the base instruction file. |
| `<rules>` / `<rule>` | Mandatory behaviors and constraints for the role or capability. |
| `<directives>` / `<directive>` | Recommended strategies or behavioral suggestions.      |
| `<capabilities>` / `<capability>` | Declares capability instructions: either as inline blocks or external references. |
| `<examples>` / `<example>` | Optional usage samples for clarity or guidance.          |
| `<switches>` / `<switch>` | Runtime options or behavior flags (e.g. `--seq`).         |
| `<context-binding>` | Sets the default language, architecture, or project context.   |
| `<communication-rules>` | Defines how the AI should interact with users (tone, clarity, intent). |
| `<tone-rules>`          | Enforces voice, confidence, and level of formality.                  |
| `<visual-style-rules>`  | Controls formatting, spacing, line length, and visual hierarchy.     |
| `<symbol-rules>`        | Specifies allowed symbols and their meanings.                        |
| `<symbol>`              | Declares individual symbols and their interpretation.                |
| `<message-structure>`   | Defines the required structure of output (summary first, bullets, etc). |

## Format and Structure

All files are plain `.md` files using XML-style tags. Each `<capability>` is structured using a consistent set of components described below.

### `<capabilities>` / `<capability>`

The `<capabilities>` tag is used to load capability instructions.

You can define them in two ways:

1. **External reference** (recommended for modular design):

```xml
<capabilities>
  - [analyze-project](../capabilities/analyze-project.md)
  - [generate-development-checklist](../capabilities/generate-development-checklist.md)
</capabilities>
```

Each item links to a separate .md file containing a <capability> block, like:

```xml
<!-- File: capabilities/generate-development-checklist.md -->
<capability id="generate-development-checklist">
  Generate a detailed checklist from the FDD, with verifiable implementation steps grouped by section.
</capability>
```

2. **Inline declaration** (for context-specific or temporary instructions):

```xml
<capabilities>
  <capability id="generate-development-checklist">
    Generate a detailed checklist from the FDD, with verifiable implementation steps grouped by section.
  </capability>
</capabilities>
```

You may mix both forms if needed, but external files are preferred for reuse and clarity.

### `<rules>`

Defines strict behaviors or constraints the model must follow.  
Each `<rule>` is atomic and imperative. Use them to enforce logic, compliance, or limitations.

You can add a `for="..."` attribute to scope the rule (e.g., `tooling`, `architecture`, etc.).

```xml
<rules>
  <rule>NEVER write business logic inside views or serializers.</rule>
  <rule>ALWAYS validate user input before processing.</rule>
  <rule for="tooling">ONLY use markdown for documentation tasks.</rule>
</rules>
```

### `<directives>`

Provides softer behavioral instructions — best practices, style guides, or process recommendations.  
Use `<directive>` for suggestions that improve clarity, safety, or quality.

```xml
<directives>
  <directive>Use second-level markdown headings (`##`) for main sections.</directive>
  <directive>Organize tasks in the same order as the FDD sections.</directive>
  <directive>Ask questions before adding optional sections like security or performance.</directive>
</directives>
```

### `<examples>`

Optional but useful. Provide sample inputs and expected outputs using `<example>` to guide the model.  
Use only when the behavior is non-obvious or benefits from demonstration.

```xml
<examples>
  <example>
    <input>Design an endpoint to deactivate a user.</input>
    <output>POST /users/{id}/deactivate → triggers UserDeactivationService</output>
  </example>
</examples>
```

### `<switches>`

Declare runtime flags that affect reasoning. For example: `--seq` for sequential thinking.  
Each `<switch>` represents a modifier that the model should activate when the capability is loaded.

```xml
<switches>
  <switch>--seq</switch>
  <switch>--context7</switch>
</switches>
```

### `<variants>`

Used to specialize a capability for specific environments (like Django, Laravel, etc.).

Each `<variant>` must include a `<context-match>` section that defines when it applies.  
Variants may override or add `<rules>`, `<directives>`, or `<examples>` inside the capability.

```xml
<variant>
  <context-match>
    <language>Python</language>
    <framework>Django</framework>
  </context-match>
  <rules>
    <rule>Use DRF ViewSets and Celery tasks when applicable.</rule>
  </rules>
</variant>
```

Variants are optional. The base capability applies globally by default.

### `<context-binding>`

Declares the default working context — such as language, framework, architecture, constraints, or any other environment-specific assumption the AI should consider when reasoning.

Use this block in role or system instruction files to define expectations like:

```xml
<context-binding>
  <language>Python</language>
  <framework>Django</framework>
  <quality>modular, testable</quality>
  <principles>design-first</principles>
</context-binding>
```

### Example Project Structure

```text
.github/
  ├── copilot-instructions.md
  ├── capabilities/
  │   ├── analyze-project.md
  │   ├── generate-fdd-outline.md
  │   ├── generate-development-checklist.md
  │   ├── generate-architecture-diagram.md
  │   └── ...
  └── chatmodes/
      ├── feature-designer.chatmode.md
      └── software-engineer.chatmode.md

```

- `capabilities/` contains atomic instruction modules (reusable).
- `chatmodes/` defines the roles, responsibilities, and capability loading logic.
