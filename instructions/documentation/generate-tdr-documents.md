<instruction id="generate-tdr-documents">
  Generate one or more Technical Debt Records (TDRs) based on the current state of the project.
  If prior project analysis is available, use it to identify areas of known or suspected technical debt.
  Otherwise, inspect the system structure, codebase, and documentation directly to detect likely sources of technical debt.
  Output each TDR to a separate file in the `docs/tdr/` directory, using the format `tdr-<slug>.md` or `NNNN-<slug>.md`.

  <rules>
    <rule>You MUST use the following TDR structure: Title, Type, Affected Area, Description, Risk Level, Cause (leave blank), Potential Mitigation, Location (optional), Status (optional), Date Identified (optional).</rule>
    <rule>You MUST generate one TDR per identifiable item of technical debt.</rule>
    <rule>Each TDR MUST describe a real or strongly inferable problem that affects maintainability, quality, or future scalability.</rule>
    <rule>You MUST leave the "Cause" field blank, as the origin of the debt is not always knowable.</rule>
    <rule>You MUST avoid vague or speculative entries that cannot be linked to concrete artifacts in the system.</rule>
    <rule>If no technical debt is detectable, you MUST output a single TDR stating "No known technical debt at this time".</rule>
  </rules>

  <directives>
    <directive>Set the Type field to one of: Architecture, Technological Gap, Infrastructure, Code.</directive>
    <directive>Name TDR files using lowercase slugs with hyphens (e.g., `tdr-missing-tests.md`) or use `NNNN-<slug>.md` if using sequential IDs.</directive>
    <directive>Write TDRs in clear, objective language, avoiding speculation or blame.</directive>
    <directive>Always include the impacted module, layer, or feature in the Affected Area.</directive>
    <directive>Use relative risk classification: Low, Medium, or High.</directive>
    <directive>Include Location and Status only if clearly known. Leave Cause blank.</directive>
  </directives>

  <examples>
    <example>
      <input>Generate TDRs for a project missing unit tests and using an outdated encryption library.</input>
      <output>
        docs/tdr/

        - 0001-missing-unit-tests.md
          Title: Lack of Unit Test Coverage
          Type: Code
          Affected Area: Service Layer
          Description: Core business methods have no associated unit tests.
          Risk Level: High
          Cause:
          Potential Mitigation: Add tests and enforce minimum coverage.
          Location: services/user_service.py
          Status: Open
          Date Identified: 2025-07-24

        - 0002-outdated-encryption-library.md
          Title: Outdated Encryption Library
          Type: Technological Gap
          Affected Area: Security Module
          Description: The system uses a version with known vulnerabilities.
          Risk Level: High
          Cause:
          Potential Mitigation: Upgrade to a secure, maintained version.
          Location: requirements.txt
          Status: Open
          Date Identified: 2025-07-24
      </output>
    </example>
  </examples>
</instruction>
