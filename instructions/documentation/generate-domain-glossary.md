<instruction id="generate-domain-glossary">
  Generate or update the project's domain-specific glossary using the Ubiquitous Language found in the system.
  If prior project analysis is available, use it to extract relevant domain terms and definitions.
  Otherwise, analyze the project structure, code, and documentation directly to infer the domain vocabulary.
  If a glossary already exists in `docs/glossary.md`, update it by appending new terms or refining existing entries while preserving formatting, order, and structure.
  If no glossary is present, create it from scratch.

  <rules>
    <rule>You MUST include only domain-relevant terms, not technical or implementation-specific details.</rule>
    <rule>Each glossary entry MUST contain: Term, Definition, and optionally Bounded Context.</rule>
    <rule>Glossary MUST be written in clear, formal, and unambiguous language.</rule>
    <rule>You MUST preserve and update existing entries when refining the glossary, avoiding duplication.</rule>
    <rule>When updating, you MUST maintain consistent formatting and structural integrity.</rule>
  </rules>

  <directives>
    <directive>Use prior project analysis as input when available, but never require it.</directive>
    <directive>Sort glossary terms alphabetically unless instructed otherwise.</directive>
    <directive>Use second-level Markdown headings (##) for each term.</directive>
    <directive>If the Bounded Context is unknown, omit that field rather than guessing.</directive>
    <directive>Prefer nouns and stable domain concepts over actions or UI labels.</directive>
  </directives>

  <examples>
    <example>
      <input>Generate or update the domain glossary for a project that manages visa applications for Australia.</input>
      <output>
        ## Applicant
        A person who submits a visa request to the Australian immigration system.
        **Bounded Context**: Visa Processing

        ## Bridging Visa
        A temporary visa granted while a substantive visa is being processed.
        **Bounded Context**: Legal Status

        ## Regional Work Requirement
        A condition tied to certain visa subclasses, requiring applicants to work in specified areas.
        **Bounded Context**: Compliance
      </output>
    </example>
  </examples>

</instruction>
