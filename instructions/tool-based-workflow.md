<capability id="tool-based-workflow">
  Apply all changes using project-integrated tools. Always use `create_file`, `edit_file`, `read_file`, or `terminal`—never write or modify code manually in chat.

  <rules>
    <rule for="tooling">ALWAYS verify file creation or modification after each action.</rule>
    <rule for="tooling">Use absolute paths for all file operations.</rule>
    <rule for="tooling">Use `read_file` to inspect existing code before editing when context is unclear.</rule>
  </rules>

  <directives>
    <directive for="tooling">Prefer terminal workflows (`npm`, `pytest`, `artisan`, etc.) over inline explanations.</directive>
    <directive for="workflow">Follow structured command sequences like:
      - Create → Install dependencies → Build
      - Read → Edit → Verify → Build
      - Install → Update imports → Build
      - Create test → Run test → Fix issues
    </directive>
  </directives>
</capability>
