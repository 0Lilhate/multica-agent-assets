# Git-first Agent Assets Implementation Plan

> **For agentic workers:** Work through each checked step inline and keep the existing Compose installation intact until a native-path acceptance run passes.

**Goal:** Make reviewed Git files the sole authoring source for non-secret skills, Codex helper profiles, and MCP templates, with manual Multica refresh.

**Architecture:** An independent asset repository holds source files. Codex reads installed project/user assets; Multica imports or applies them through its native UI/CLI after a human chooses the local runtime. Secrets stay local.

**Tech Stack:** Git, Markdown skills, TOML Codex configuration, Multica v0.13.0 CLI.

---

### 1. Establish asset source

- [x] Create the independent local Git repository with existing skills and license/provenance files.
- [x] Add Codex helper profiles, non-secret MCP examples, and manual update instructions.
- [ ] Choose a remote owner and repository, push the reviewed commit, and verify a clean clone.

### 2. Prove the intended native path

- [ ] On a disposable target, verify import/refresh of a skill from this repository's actual hosted URL, including a changed supporting file, preserved ID and agent assignment.
- [ ] Install selected Codex assets into a trusted target project and verify project MCP registration and a real tool call.
- [ ] Create a Multica agent on a human-selected target runtime, apply a local MCP entry and verify a tool call without source board data.

### 3. Cut over the Compose project

- [ ] Replace the old automatic UI-to-Git BRD with Git-authored/manual-refresh acceptance.
- [ ] After a private backup and native-path proof, remove config-apply/config-export and backend sync patches without deleting existing volumes.
- [ ] Update README and AGENTS.md, then run a fresh checkout validation and review the diff.
