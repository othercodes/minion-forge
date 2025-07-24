<instruction id="analyze-project">
  Perform diagnostic analysis of the entire project codebase to understand its structure, domains, architectural boundaries, and interaction patterns. This internal understanding enables better design decisions and supports documentation, planning, and review tasks.

  <rules>
    <rule>ONLY perform read-only diagnostic analysis. NEVER generate, modify, or suggest source code.</rule>
    <rule>Build an internal understanding of the project’s architecture, domains, data flows, and inter-module relationships.</rule>
    <rule>Identify structural issues such as redundancy, coupling, missing boundaries, or conflicting patterns.</rule>
    <rule>Report findings using natural language with domain vocabulary — do NOT include pseudocode, code snippets, or implementation suggestions.</rule>
    <rule>Findings must be relevant and actionable for design, architecture, or review workflows.</rule>
  </rules>

  <directives>
    <directive>Organise insights by architectural layer, module, or domain concept when applicable.</directive>
    <directive>Explicitly surface architectural signals, hotspots, or inconsistencies that may impact current or future development.</directive>
    <directive>Ensure findings are structured and actionable so they can support future documentation or design-related decisions.</directive>
    <directive>Think sequentially and globally — you are expected to understand the entire project context unless instructed otherwise.</directive>
  </directives>

  <examples>
    <example>
      <input>Analyze the current Django project to understand where user subscription logic is implemented.</input>
      <output>
        - Subscription logic is fragmented across `users/models.py`, `payments/services.py`, and `subscriptions/tasks.py`.
        - No centralized domain boundary exists.
        - High coupling risk with the new feature. Recommend clarifying service ownership in design documentation.
      </output>
    </example>
    <example>
      <input>Analyze the Laravel app structure to check if observability concerns are already addressed.</input>
      <output>
        - Observability is inconsistent: some services use `Log::info()`, others dispatch custom events.
        - No unified tracing or log strategy present.
        - Potential risk for debugging and alerting workflows.
      </output>
    </example>
  </examples>

  <switches>
    <switch>--seq</switch>
  </switches>
</instruction>
