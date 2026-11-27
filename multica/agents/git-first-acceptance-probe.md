# Git-first acceptance probe (Multica agent)

This is a disposable acceptance fixture, not a production agent or an export of an existing Multica agent. Apply it manually through the Multica UI/CLI after the target computer has an authenticated, online Codex runtime. Do not place runtime IDs, credentials, or machine paths in this file.

## Portable fields

- **Name:** `git-first-acceptance-probe`
- **Description:** Disposable agent for checking that reviewed Git assets can be applied with native Multica operations.
- **Instructions:**

  > You are a disposable acceptance agent. When given the acceptance prompt, use the assigned `codebase-design` skill to explain one small module seam, make one harmless call to the assigned `sequential-thinking` MCP tool, and report which tool was called and what it returned. If the skill or MCP tool is unavailable, report that plainly. Do not edit repository files or workspace configuration.

- **Workspace skill:** `codebase-design`, enabled; source folder `.agents/skills/codebase-design/` in this asset repository.
- **Workspace MCP:** `sequential-thinking`, enabled; configure from `multica/mcp/sequential-thinking.example.json` and assign the workspace entry to this agent.
- **Runtime provider:** Codex. A human selects the target installation's online runtime; its ID is local.
- **Access:** creator-only for the disposable check.
- **Other settings:** keep supported defaults. No custom environment or agent-level MCP configuration.

## Acceptance readback

After manual creation, compare the name, description, exact instructions, runtime provider, skill binding and MCP binding with this file. Run one safe acceptance prompt and verify the MCP tool call in the Multica run log. Confirm that no source board issues or run history appeared from the Git asset transfer. On a repeated startup of the same installation, keep the PostgreSQL volumes and the local daemon profile/identity, then confirm the agent and runtime IDs are unchanged and no new selection is needed. If that daemon profile or runtime was lost, require an explicit human rebind; never select another runtime automatically.

This fixture proves the manual native path. It does not prove transfer of a production Multica agent. Remove only the disposable fixture after recording the readback; do not remove unrelated agents or workspace data.
