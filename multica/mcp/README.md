# Workspace MCP templates

`sequential-thinking.example.json` is a non-secret example that passed a disposable Multica v0.13.0 agent tool call on this Mac. The example now pins npm package `@modelcontextprotocol/server-sequential-thinking@2.2.0`; this release requires Node.js 24 or newer and `npx` on the target. Multica workspace MCP is separate from Codex `[mcp_servers]` and is not created by copying `.codex/config.toml`.

Use the pinned Multica CLI `workspace mcp add <name> --server-config-file <local-file>`, then `agent mcp add <agent-id> <server-id>`. A real server's URL, executable path and credentials must be checked on the destination. The Multica list response hides the stored configuration; verify a tool call, not merely the list entry.
