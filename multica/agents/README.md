# Multica agent templates

No production Multica agent definition existed in the source repository at this migration point. Codex TOML profiles under `.codex/agents/` are different objects.

[`git-first-acceptance-probe.md`](git-first-acceptance-probe.md) is a non-production fixture for checking the manual Git → Multica path on a disposable installation. Its Git fields are applied through the Multica UI/CLI after a human selects a local runtime; it is not an automatic import format.

For a new production Multica agent, review its name, instructions, intended skills, access, and runtime provider here. On each installation, authenticate with the pinned CLI or UI, select that machine's registered runtime, create or update the agent, and assign workspace skills and MCP entries. Keep runtime IDs and custom environment values local.
