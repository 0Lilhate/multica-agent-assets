# Multica agent assets

Reviewed public Git source for non-secret Multica workspace skills and agent/MCP examples. This is a **separate repository** from the Compose installation. The Compose installation switched to the native Git-first path on 27 November 2026: its official backend runs without the former UI exporter and startup apply services. Humans review and merge asset changes, then pull and manually import or refresh the selected workspace skills. Agent and MCP examples are applied separately through Multica UI/CLI.

## Contents

- `.agents/skills/`: copied project skills from `multica-docker-compose` commit `7e73b40`; licenses and upstream revisions remain in `.agents/skills/SOURCES.md`.
- `.codex/agents/`: Codex helper profiles for maintaining and reviewing these assets. They are not Multica agents.
- `.codex/config.toml`: non-secret Codex project settings and MCP definitions. Codex reads project config only for a trusted checkout; a sibling checkout does not configure unrelated projects.
- `multica/mcp/`: non-secret workspace MCP examples; the Multica CLI consumes a separate JSON server entry.
- `multica/skills/`: disposable hosted-refresh acceptance fixture, separate from copied project skills.
- `multica/agents/`: a disposable acceptance template and instructions for manually creating Multica agents after local runtime registration. No production agent definition or runtime ID is exported here.

## Transfer boundary

A fresh Multica installation imports selected workspace skills from the public GitHub URL and manually applies only the disposable agent and workspace MCP examples needed for acceptance. This repository does not restore the source installation's workspace context/settings, production agents, Plugin packages/hooks, Autopilots/triggers, or board data. Existing installation data is held in PostgreSQL/uploads; its preservation must be checked during the separate Compose cutover drill. No unused object needs to be recreated on the fresh target for this acceptance. The accepted B target is a separate checkout/Compose project/database/volume set/CLI profile on the same Mac; this does not establish behavior on a second physical computer.

## Update path

1. A person or local coding agent may edit this repository on a branch and propose a reviewed change. Git is the authoring source. UI edits to an imported Multica skill are temporary; anyone who wants to retain one must separately submit and merge a Git change before refresh. How the Git change is authored is outside Multica cutover acceptance; this repository need not be linked as a Multica repo resource for skill import or refresh.
2. After merge, pull on the destination computer. Direct Codex use of the helper profiles, project skills, and `.codex/config.toml` is optional and outside Multica cutover acceptance; those files do not create Multica workspace objects.
3. Import a workspace skill into Multica from a public hosted GitHub URL once. If first import gets GitHub HTTP 403 with `x-ratelimit-remaining: 0`, wait until `x-ratelimit-reset` and retry the same URL; the skill remains absent until hosted import succeeds. Later, an owner/admin **manually** chooses Update from source or `multica skill refresh <id>`. If GitHub is temporarily unavailable, keep an existing workspace skill and retry later; do not archive-overwrite a hosted skill, because that removes its refreshable source. Refresh keeps the skill ID and agent assignments but replaces UI-only edits without a required pre-refresh diff.
4. Create/update Multica agents through its UI/CLI after selecting a registered runtime on that installation. Configure Multica workspace MCP separately with `multica workspace mcp add/update --server-config-file` and bind it to the agent. Put any credential-bearing JSON in a local private file, never in this repository.
5. Verify the target UI, assigned skill content and supporting files, runtime choice, and a real MCP tool call. Git pull alone does not perform steps 3–5. The Codex runtime used by this Multica agent still needs its local installation and login.

The Compose repository's automatic UI → Git → UI BRD and acceptance report are historical evidence for the previous implementation. Its Git-first BRD defines the narrower native workflow. The cutover was rehearsed on a restored copy and applied to the working installation with existing PostgreSQL/uploads volumes preserved; a second physical computer has not been tested.
