# Multica agent assets

Candidate Git source of truth for reviewed, non-secret skills and agent configuration. This is a **separate repository** from the Compose installation. The current Compose repository remains active until the native path is accepted; do not run its old exporter and this Git-first workflow as two authors of the same setting.

## Contents

- `.agents/skills/`: copied project skills from `multica-docker-compose` commit `7e73b40`; licenses and upstream revisions remain in `.agents/skills/SOURCES.md`.
- `.codex/agents/`: Codex helper profiles for maintaining and reviewing these assets. They are not Multica agents.
- `.codex/config.toml`: non-secret Codex project settings and MCP definitions. Codex reads project config only for a trusted checkout; a sibling checkout does not configure unrelated projects.
- `multica/mcp/`: non-secret workspace MCP examples; the Multica CLI consumes a separate JSON server entry.
- `multica/agents/`: instructions for manually creating Multica agents after local runtime registration. No live agents or runtime IDs are exported here.

## Update path

1. An agent edits this repository on a branch and proposes a reviewed change. Keep Git as the authoring source; reconcile useful UI experiments back into Git before refreshing.
2. After merge, pull on the destination computer. For Codex, install selected skills and profiles into the applicable project or user locations, and place the MCP definitions into that trusted project's `.codex/config.toml` or a local user config. Check actual discovery and tool calls.
3. Import a workspace skill into Multica from a hosted GitHub URL once. Later, an owner/admin **manually** chooses Update from source or `multica skill refresh <id>`. A local archive has no hosted refresh source; re-import it with explicit conflict handling. Refresh keeps the skill ID and agent assignments but replaces UI edits to its content.
4. Create/update Multica agents through its UI/CLI after selecting a registered runtime on that installation. Configure Multica workspace MCP separately with `multica workspace mcp add/update --server-config-file` and bind it to the agent. Put any credential-bearing JSON in a local private file, never in this repository.
5. Verify the target UI, assigned skill content and supporting files, runtime choice, and a real MCP tool call. Git pull alone does not perform steps 2–5.

The current Compose repository's automatic UI → Git → UI BRD is a different contract. Revise that BRD and test this native workflow on a fresh installation before removing its sync services, backend patches, or preserving volumes differently.
