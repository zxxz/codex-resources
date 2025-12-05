# Codex Migration Notes

This repo was adapted from Claude Code resources to target OpenAI Codex workflows. Key changes:

- Paths and config directories now reference `.codex/` instead of `.claude/`.
- Project convention files use `AGENTS.md` (Codex constitution) instead of `CLAUDE.md`/`CODEX.md`.
- Documentation and examples refer to Codex terminology rather than Claude.
- Example model names now point to OpenAI offerings (e.g., `gpt-5.1-codex-max` replacing `claude-sonnet-4-5`).

## Feature Parity Notes

- **Hooks:** Codex does not currently expose Claude-style hooks. Treat any "hook" automation as project-level scripts invoked by your tooling/CI rather than native Codex features.
- **Subagents:** Codex does not manage nested agents. A workable alternative is to run Codex as an MCP server and invoke role-specific configurations (e.g., `AGENTS.ux-designer.md`) via shell commands or orchestration scripts.

## Open Questions / Assumptions to Verify

- **Plugin support:** Codex currently has no plugin system. Any plugin metadata or installation instructions were removed.
- **Working directory selection:** Codex CLI expects `-C/--cd <DIR>` to set the project root instead of an environment variable like `CLAUDE_PROJECT_DIR`. Launch Codex with `codex --cd /path/to/project` so hooks and prompts resolve relative paths correctly.
- **Model naming:** Use `gpt-5.1-codex-max` as the current default Codex-serving OpenAI model with `model_reasoning_effort="medium"`. Update to the preferred Codex model identifier once finalized.
- **Hooks/debug flags:** Examples that previously used `claude --debug` are now `codex --debug`. Validate whether Codex supports this flag and update accordingly.
- **Domain references:** Any lingering assumptions about Claude-only features should be revisited once Codex documentation is confirmed (e.g., reserved names, marketplace behavior).

Document uncertainties here as you verify Codex-specific behaviors.
