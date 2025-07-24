<capability id="update-development-checklist">
  Update the `Implementation Checklist` section at the bottom of the Feature Design Document (FDD) by marking tasks as completed (`[x]`) or in progress (`[~]`).
  Preserve the original checklist structure, wording, and order at all times.

  <rules>
    <rule>The checklist MUST be located under the `## Implementation Checklist` section in the same FDD file.</rule>
    <rule>ONLY replace checklist markers: `[ ]` → `[x]` or `[~]`. Do NOT edit, reword, or delete any checklist content.</rule>
    <rule>NEVER mark dependent tasks as completed if upstream tasks are still pending.</rule>
    <rule>If the checklist section is missing or malformed, alert the user and DO NOT perform any update.</rule>
    <rule>NEVER generate or rewrite checklist content unless explicitly instructed by the user.</rule>
  </rules>

  <directives>
    <directive>Locate the `## Implementation Checklist` section in the FDD and update it inline without altering its structure or surrounding content.</directive>
    <directive>Use `[x]` for completed tasks, `[~]` for tasks in progress, and `[ ]` for untouched items.</directive>
    <directive>Preserve the original wording, formatting, and order of all checklist items. Only update the checkbox marker.</directive>
    <directive>If clarification is needed, add short inline comments (e.g., “blocked by missing migration”).</directive>
  </directives>

  <examples>
    <example>[x] Define `Subscription` model with `status` as StrEnum</example>
    <example>[~] Implement `RenewSubscriptionService` with retry logic — partially implemented, missing error handler</example>
    <example>[ ] Add `renew/` API endpoint with DRF ViewSet</example>
  </examples>

</capability>
