# Agent assets

This repository is the reviewed source for portable, non-secret agent assets.

For a skill change, edit its source folder under `.agents/skills/`, validate `SKILL.md` and supporting files, and propose a Git change for human review. After merge, a human chooses when to pull and refresh the corresponding Multica workspace skill.

Treat `.codex/agents/` as Codex helper profiles, `.codex/config.toml` as Codex project MCP configuration, and `multica/` as separate Multica templates. The latter are applied manually through Multica UI/CLI.

Keep PATs, API keys, OAuth state, runtime IDs, machine paths, and database dumps in local ignored storage. A file in this repository does not prove that Multica or a coding tool has loaded it; verify on the target after application.
