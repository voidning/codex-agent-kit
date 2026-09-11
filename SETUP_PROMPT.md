Please install this repository's collaboration and on-demand multi-agent workflow as my personal global Codex configuration on this computer. Perform the setup and validation, rather than only providing instructions.

I authorize adopting the configuration in `config-to-merge.toml`, the workflow in `AGENTS.md`, and the four custom roles in `agents/`. Read those files first. Preserve their medium/high defaults, difficulty-based escalation policy, bounded context, and limit of three concurrent children.

1. Consult current official Codex documentation and inspect the installed version, actual configuration directory, and supported models and reasoning levels. Respect `CODEX_HOME` when set; otherwise use the normal `~/.codex` directory.
2. Back up every existing file before changing it. Merge `config-to-merge.toml` into the existing `config.toml`, preserving unrelated settings. Keep model fields at the TOML top level; merge an existing `[agents]` table without duplicating it.
3. Merge the complete collaboration, delegation, and escalation rules into the personal global `AGENTS.md`. Replace equivalent rules from earlier kit versions instead of appending the old English workflow or the six collaboration paragraphs again. Preserve unrelated compatible user instructions. Resolve conflicts with earlier kit rules in favor of this explicitly requested version and explain the changes; ask only about unresolved conflicts with other personal rules.
4. Install the four role files into the personal configuration directory's `agents/` folder. Back up existing files with matching names before updating them.
5. Preserve authentication, model providers, plugins, MCP servers, project settings, and permissions. Do not copy credentials or machine-specific paths from another computer or weaken security settings.
6. If configuration syntax has changed, use the documented current equivalent. Report unsupported models or reasoning levels; do not silently substitute another model or claim an unavailable setting was applied.
7. Validate TOML syntax, role names, models, reasoning levels, the concurrency limit, and completeness and consistency of collaboration, delegation, and escalation rules without duplicate requirements. Verify client loading when possible. Do not start paid subagent calls merely to test installation.
8. Report the settings actually written, backup locations, and whether a restart or new task is required. Distinguish files saved, rules loaded, and real model calls verified.

Escalation must respect pinned custom-role settings: use an unpinned general-purpose/default agent with explicit model and effort and a bounded or self-contained brief when supported. A prompt alone does not override a pinned role file. If unsupported, let the primary agent handle the work or report the limitation.

Proceed within this authorization, requesting filesystem permission only when required by the system.
