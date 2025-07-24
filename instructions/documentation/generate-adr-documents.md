<instruction id="generate-adr-documents">
  Generate one or more Architectural Decision Records (ADRs) based on the current project state and design history.
  If prior project analysis is available, use it to extract architectural decisions already made or implied.
  Otherwise, analyze the project's structure, documentation, and codebase directly to infer key architectural decisions.
  Output each ADR to a separate file in the `docs/adr/` directory, using the format `NNNN-<slug>.md`, where `NNNN` is a zero-padded sequential number starting from 0001, and `<slug>` is a lowercase hyphenated summary of the decision.
  You should follow the ADR recommended format from the official repository (Joel Parker Henderson): Title, Status, Context, Decision, Consequences. Reference: https://github.com/joelparkerhenderson/architecture-decision-record

  <rules>
    <rule>You MUST use the standard ADR structure: Title, Status, Context, Decision, Consequences.</rule>
    <rule>You MUST create one file per decision, even when generating multiple ADRs.</rule>
    <rule>You MUST ensure that each ADR addresses a specific architectural question or tradeoff.</rule>
    <rule>Each ADR MUST reflect real or inferable decisions relevant to the system’s current or planned architecture.</rule>
    <rule>If no clear decisions can be identified, you MUST state that explicitly in a single ADR titled "Undocumented Architecture Decisions".</rule>
  </rules>

  <directives>
    <directive>Use prior project analysis if available to guide or seed the ADR generation process.</directive>
    <directive>Name ADR files using the format `NNNN-<slug>.md` (e.g., `0001-database-choice.md`).</directive>
    <directive>Write ADRs in formal, concise English suitable for technical documentation.</directive>
    <directive>If uncertainty exists about a decision's rationale, include it in the “Context” section.</directive>
    <directive>Mark ADRs as “Proposed” if not yet agreed upon, or “Accepted” if already implemented.</directive>
  </directives>

  <examples>
    <example>
      <input>Generate ADRs for a project that moved from monolith to microservices and adopted PostgreSQL over MongoDB.</input>
      <output>
        docs/adr/

        - 0001-microservices-transition.md
          Title: Transition to Microservices
          Status: Accepted
          Context: The system was originally built as a monolith, which limited scalability and team autonomy.
          Decision: Adopt a microservices architecture, splitting the system by bounded context.
          Consequences: Increased deployment complexity, need for service orchestration and inter-service communication.

        - 0002-database-choice.md
          Title: Selection of PostgreSQL
          Status: Accepted
          Context: The team considered PostgreSQL and MongoDB for long-term data storage.
          Decision: Chose PostgreSQL due to strong relational modeling and ACID guarantees.
          Consequences: Reduced flexibility for document-based features, improved consistency and reporting capabilities.
      </output>
    </example>
  </examples>
</instruction>
