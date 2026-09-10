# Codex Agent Kit

English | [简体中文](README.zh-CN.md)

Portable Codex multi-agent configuration with on-demand delegation, cost-conscious defaults, and difficulty-based escalation.

A personal configuration starter kit: the primary agent coordinates useful independent work, collects evidence, and verifies the final result. Simple or tightly sequential tasks stay with the primary agent. Roles are started only when needed.

## Default roles

| Role | Model | Reasoning | Responsibility |
| --- | --- | --- | --- |
| Primary | `gpt-6-astra` | `medium` | Plan, coordinate, integrate, and verify |
| Explorer | `gpt-5.6-luna` | `medium` | Bounded, read-heavy investigation |
| Worker | `gpt-5.6-sol` | `high` | Implementation and appropriate tests |
| Researcher | `gpt-5.6-luna` | `medium` | Focused documentation and factual lookup |
| Reviewer | `gpt-6-astra` | `high` | Optional independent review of material risks |

At most **three child agents** run concurrently. Children do not delegate further unless explicitly requested.

## Quick start

1. Install Codex and sign in on the destination computer.
2. Clone or download this repository.
3. Give Codex access to the repository directory.
4. Send the contents of [SETUP_PROMPT.md](SETUP_PROMPT.md), or use the [Chinese setup prompt](SETUP_PROMPT.zh-CN.txt).
5. Let Codex verify the installed version and available models, back up existing files, merge settings, and report whether a restart or new task is needed.

The setup prompt authorizes installation; downloading or opening this repository alone does not install anything.

## Files and destinations

| File | Purpose / destination |
| --- | --- |
| `config-to-merge.toml` | Merge into `$CODEX_HOME/config.toml` |
| `AGENTS.md` | Merge workflow rules into `$CODEX_HOME/AGENTS.md` |
| `agents/*.toml` | Install four custom roles under `$CODEX_HOME/agents/` |
| `SETUP_PROMPT.md` | English installation prompt |
| `SETUP_PROMPT.zh-CN.txt` | Chinese installation prompt |
| `GUIDE.zh-CN.txt` | Chinese migration guide |

When `CODEX_HOME` is not set, the usual directory is `~/.codex`. The configuration file is a **merge fragment**, not a complete replacement: preserve existing authentication, providers, plugins, MCP servers, projects, and permissions. Keep `model` and `model_reasoning_effort` at the TOML top level and merge into an existing `[agents]` table instead of duplicating it.

## Escalation and context

Start exploration and research at medium reasoning. After one focused attempt, report insufficient evidence, conflicting sources, or difficult cross-module reasoning to the primary agent. The primary can clarify the scope, take over, or escalate to Luna / high, then Sol / high when appropriate. Reserve Astra / xhigh independent review for difficult security, concurrency, data-consistency, or similarly material correctness issues.

Custom role files pin model and reasoning settings. Escalation must use an unpinned general-purpose/default agent with explicit model and effort settings, if supported; a prompt alone does not override a pinned role file.

Provide each child only the objective, relevant context, constraints, file ownership, and acceptance criteria. Collect concise conclusions, supporting references, validation results, and unresolved issues.

## Compatibility and cost

This kit reflects a personal configuration exported on September 10, 2026. Model access, reasoning levels, and configuration support depend on the destination account and Codex version. Verify them during installation and report unavailable settings explicitly.

Multiple agents can consume more tokens than a comparable single-agent run. These defaults aim to avoid unnecessary delegation; they do not guarantee lower total cost.

No account credentials, API keys, provider endpoints, or machine-specific project paths are included. This is an independent configuration kit, not an official OpenAI preset.

Reference: [Official Codex subagent documentation](https://developers.openai.com/codex/multi-agent).
