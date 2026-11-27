# Git-first Agent Assets Implementation Plan

> **For agentic workers:** Work through each checked step inline and keep the existing Compose installation intact until a native-path acceptance run passes.

**Goal:** Make reviewed Git files the sole authoring source for non-secret skills, Codex helper profiles, and MCP templates, with manual Multica refresh.

**Architecture:** An independent asset repository holds source files. Codex reads installed project/user assets; Multica imports or applies them through its native UI/CLI after a human chooses the local runtime. Secrets stay local.

**Tech Stack:** Git, Markdown skills, TOML Codex configuration, Multica v0.13.0 CLI.

---

### 1. Establish asset source

- [x] Create the independent local Git repository with existing skills and license/provenance files.
- [x] Add Codex helper profiles, non-secret MCP examples, and manual update instructions.
- [x] Create the empty public GitHub repository `0Lilhate/multica-agent-assets` and set the local `origin` URL.
- [x] Publish the existing local baseline commit to public `main` with the owner-approved visible email.
- [ ] Review and merge the candidate asset PR, then verify an unauthenticated clean clone of its merged commit.

### 2. Prove the intended native path

- [ ] On a separate B installation on the same Mac, import `multica/skills/git-first-refresh-probe/` at v1 from this repository's actual hosted URL, then review/merge v2 changes to both `SKILL.md` and `references/probe.md`; refresh and check preserved ID and agent assignment.
- [x] Scope decision: direct Codex installation into another trusted project and its separate MCP tool call are outside Multica cutover acceptance; keep the helper assets available for optional use.
- [ ] Create a Multica agent on a human-selected target runtime, apply a local MCP entry and verify a tool call without source board data.

### 3. Cut over the Compose project

- [ ] Keep the old automatic UI-to-Git BRD and acceptance report as historical evidence; update the new Git-first BRD and operator instructions for the narrower native path.
- [ ] After a private backup and native-path proof, remove config-apply/config-export and backend sync patches without deleting existing volumes.
- [ ] Update README and AGENTS.md, then run a fresh checkout validation and review the diff.
