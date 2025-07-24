<instruction id="generate-development-checklist">
  Generate a structured, atomic task list that maps directly to the sections and actions defined in the Feature Design Document (FDD). This checklist must be used for implementation tracking, ensuring that each step can be verified and marked individually during development.

  <rules>
    <rule>The checklist MUST be appended to the end of the current FDD file as a new section titled `## Implementation Checklist`.</rule>
    <rule>The checklist MUST reflect all concrete implementation actions described in the FDD.</rule>
    <rule>Each task MUST be self-contained, verifiable, and suitable for completion tracking.</rule>
    <rule>Group tasks according to FDD sections: `Data Model`, `API`, `Business Logic`, `Security`, `Testing`, etc.</rule>
    <rule>Use task dependencies (via →) to indicate execution order when necessary.</rule>
    <rule>NEVER infer or suggest new tasks beyond what is explicitly defined in the FDD.</rule>
  </rules>

  <directives>
    <directive>Insert the checklist at the bottom of the current FDD using a second-level markdown heading (`##`).</directive>
    <directive>Use `[ ]` (Markdown syntax) for all checklist items.</directive>
    <directive>Follow the order of appearance and structure of the FDD to maintain alignment.</directive>
    <directive>Use absolute and implementation-ready task phrasing (e.g., “Define model X with constraints”).</directive>
    <directive>Include all relevant tasks, even if simple or repetitive, to support fine-grained progress tracking.</directive>
  </directives>

  <examples>
    <example>[ ] Define `Subscription` model with `status` as StrEnum</example>
    <example>[ ] Create migration for new `subscriptions` table → before implementing services</example>
    <example>[ ] Implement `RenewSubscriptionService` with retry logic</example>
    <example>[ ] Add `renew/` API endpoint with DRF ViewSet</example>
    <example>[ ] Write unit tests for service layer methods</example>
    <example>[ ] Write integration tests for full subscription renewal flow</example>
  </examples>

  <notes>
    This checklist is intended for use by development teams during feature implementation.
    It must be generated after the FDD is finalized and should strictly follow its structure and scope.
    It is the canonical source of implementation progress tracking and must not include speculative or inferred tasks.
  </notes>

</instruction>
