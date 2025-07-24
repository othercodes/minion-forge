<instruction id="generate-fdd-outline">
  Generate a complete markdown scaffold for a Feature Design Document (FDD), following project architecture and terminology. Confirm inclusion of optional sections (performance, observability, etc.) based on user input and active context.

  <rules>
    <rule>By default, create the FDD in the `docs/features` directory. If it doesn't exist, ask the user to confirm creation or provide an alternative path.</rule>
    <rule>The outline MUST follow the project’s layered architecture and domain-driven structure.</rule>
    <rule>Always include core sections: feature overview, data design, API design, business logic, and testing.</rule>
    <rule>Confirm the inclusion of optional sections (e.g., performance, observability, scalability, security) explicitly with the user.</rule>
    <rule>If a <context-binding> is active, apply the corresponding conventions for structure and terminology.</rule>
  </rules>

  <directives>
    <directive>Use markdown headings to represent each main section of the FDD.</directive>
    <directive>Ask precise questions to decide on optional sections (e.g., “Does this require async processing, security constraints, or performance tuning?”).</directive>
    <directive>Clarify domain scope and feature impact before finalizing the outline.</directive>
    <directive>Always confirm the output directory if `docs/features` is missing.</directive>
  </directives>

  <examples>
    <example>
      <input>Create an FDD outline for a Django feature that manages subscription renewals.</input>
      <output>
        1. Feature Overview
        2. Data Design
        3. API Design
        4. Business Logic
        5. Testing
        Prompt: "Does this feature require security controls, async processing, or performance constraints?"
      </output>
    </example>
  </examples>

  <variants>
    <variant>
      <context-match>
        <language>PHP</language>
        <framework>Laravel</framework>
      </context-match>
      <rules>
        <rule>Structure MUST include migrations, models, services, events, routes, and configuration guidance.</rule>
      </rules>
      <directives>
        <directive>Use Artisan command examples for migrations and scaffolding sections.</directive>
      </directives>
    </variant>
    <variant>
      <context-match>
        <language>Python</language>
        <framework>Django</framework>
      </context-match>
      <rules>
        <rule>Structure MUST include models, serializers, viewsets, service layer, Celery tasks, and testing strategy.</rule>
      </rules>
      <directives>
        <directive>Follow DRF and Celery conventions when applicable.</directive>
      </directives>
    </variant>
  </variants>

</instruction>
