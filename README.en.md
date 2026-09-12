# Codex Agent Kit

[简体中文](README.md) | English

Portable Codex collaboration and multi-agent configuration with natural requests, goal-matched validation, on-demand delegation, and difficulty-based escalation.

A personal configuration starter kit: the primary agent coordinates useful independent work, collects evidence, and verifies the final result. Simple or tightly sequential tasks stay with the primary agent. Roles are started only when needed.

## Problems this workflow addresses

These are the problems the rules target, not a claim that every issue has been resolved in practice. See [AGENTS.md](AGENTS.md), the Chinese canonical workflow, for exact triggers and authorization boundaries.

| Problem | Approach |
| --- | --- |
| Drifting from references | Extract required features, compare rendered samples, and obtain approval at explicitly required checkpoints before expanding. |
| Piling on patches | Revise existing clauses, merge duplicates, and resolve conflicts instead of continually appending rules. |
| Repeated questions | Use available context first; ask only about consequential choices, without requiring a template. |
| Excessive approval requests | Handle routine details within authorization and do not request existing authorization again. |
| Forgetting earlier decisions | Update only the parts affected by new feedback and preserve confirmed decisions. |
| Over-delegation | Do simple tasks directly; delegate only useful work that can proceed independently. |
| Repeating research | Hand off necessary context and verify key evidence instead of repeating the entire investigation. |
| Blind trial and error | Diagnose failed fixes before trying again rather than repeating speculative changes. |
| Superficial validation | Inspect actual renders, follow normal interaction paths, and validate functions and visuals separately. |
| Endless scope growth | Deliver when the goal is met instead of automatically adding optimization or reviews. |
| Unnecessary model escalation | Escalate with task difficulty; do not default to the highest tier or claim unperformed model switches. |

These principles apply to single-agent and multi-agent work without requiring interviews, samples, or reviews for every task. Asset, technical, or cost constraints do not justify silently changing an agreed direction. Temporary interfaces do not establish visual acceptance, and self-checks do not establish user approval.

## Upgrading an existing installation

The September 12, 2026 revision refines the collaboration principles while preserving roles, models, concurrency limits, and escalation settings.

Merge the complete repository `AGENTS.md` into the personal global file. Replace equivalent rules from earlier kit versions instead of appending the old English workflow or the six collaboration paragraphs again. Preserve unrelated compatible personal rules and report unresolved semantic conflicts. Do not overwrite the entire personal configuration file.

A rule merge and static checks do not prove better real-world outcomes. Evaluate correction rounds, completion time, acceptance results, and available usage data on real tasks before tuning further; do not claim a measured speed or cost improvement without evidence.

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
| `AGENTS.md` | Merge the complete collaboration and delegation rules into `$CODEX_HOME/AGENTS.md` |
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

Model settings reflect a personal configuration exported on September 10, 2026; collaboration principles were revised on September 12, 2026. Model access, reasoning levels, and configuration support depend on the destination account and Codex version. Verify them during installation and report unavailable settings explicitly.

Multiple agents can consume more tokens than a comparable single-agent run. These defaults aim to avoid unnecessary delegation; they do not guarantee lower total cost.

No account credentials, API keys, provider endpoints, or machine-specific project paths are included. This is an independent configuration kit, not an official OpenAI preset.

Reference: [Official Codex subagent documentation](https://developers.openai.com/codex/multi-agent).
