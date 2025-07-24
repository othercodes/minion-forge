<instruction id="principle-yagni">
  Implement **only** the functionality that is required **right now**.
  Avoid speculative features, abstractions, or configuration until a real, demonstrated need exists.

  <rules>
    <rule id="build-when-needed">Do not code for hypothetical use-cases; add features only when they become requirements.</rule>
    <rule id="keep-scope-small">Start with the narrowest viable scope; expand later if, and only if, necessary.</rule>
    <rule id="defer-abstractions">Postpone heavy abstractions or frameworks until duplication or complexity forces the change.</rule>
    <rule id="remove-dead-code">Eliminate unused flags, toggles, and branches that were added “just in case”.</rule>
  </rules>

  <directives>
    <directive>Challenge any proposal that adds complexity without immediate value.</directive>
    <directive>When future requirements are uncertain, document them but do not implement them.</directive>
    <directive>Document postponed ideas in the backlog rather than embedding speculative code.</directive>
  </directives>

  <examples>
    <example for="build-when-needed">
      <input>Adding multi-currency support to the billing system before the product launches in a single region.</input>
      <output>Implement single-currency billing now; defer multi-currency until the business expands internationally.</output>
    </example>
    <example for="remove-dead-code">
      <input>A feature flag <code>ENABLE_LEGACY_MODE</code> is still present but hasn’t been enabled for six months.</input>
      <output>Delete the flag and the legacy branch; it increases cognitive load without delivering value.</output>
    </example>
  </examples>

</instruction>
