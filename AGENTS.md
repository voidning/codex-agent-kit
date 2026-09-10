# On-demand, cost-conscious agent workflow

The user requests subagent delegation by default when useful independent parallel work exists. Follow this policy for applicable tasks.

- The primary agent plans, coordinates, integrates results, and verifies the final outcome. Prefer gpt-6-astra with medium reasoning unless the user selects another model.
- Delegate only concrete, bounded subtasks that can run independently alongside useful primary-agent work. Complete simple or tightly sequential tasks directly. Do not routinely spawn every role.
- Explorer: gpt-5.6-luna / medium, for bounded read-heavy investigation.
- Worker: gpt-5.6-sol / high, for implementation and appropriate tests.
- Researcher: gpt-5.6-luna / medium, for focused documentation or factual lookup.
- Reviewer: gpt-6-astra / high, only when material risk, complex changes, or unresolved correctness questions justify independent review and useful independent primary-agent work remains.
- Use matching custom agents when the tool supports selecting them. Otherwise explicitly supply the model and reasoning effort above and include the role's instructions in the delegated prompt. Use a bounded history fork or a self-contained prompt without history when needed for model overrides.
- Keep at most three child agents active. Child agents should not delegate further unless explicitly requested.
- Provide objectives, relevant context, constraints, file ownership, and expected output. Avoid overlapping edits, duplicated research, and unnecessary repeated review.
- Collect required results, inspect evidence, integrate changes, and perform appropriate final validation before reporting completion.
- If a requested model or reasoning level is unavailable, report the limitation; never claim an unavailable configuration or an unperformed check ran.

## Difficulty-based escalation and context budget

- Start explorer and researcher at medium; keep worker at high and optional reviewer at high. Do not automatically escalate every task.
- If evidence remains insufficient after one focused investigation or validation attempt, sources conflict, or the task involves difficult cross-module reasoning, report the evidence and uncertainty to the primary agent instead of repeating the same approach. The primary decides whether to clarify scope, take over, or escalate.
- For harder exploration/research, first consider gpt-5.6-luna / high; if capability is insufficient, the primary can take over or explicitly assign gpt-5.6-sol / high. Use gpt-6-astra / xhigh review only for difficult security, concurrency, data-consistency, or similarly material correctness issues that justify independent review.
- Custom agent files pin their model and effort and can override explicit spawn settings. For escalation, use a general-purpose/default agent that does not pin these settings, explicitly passing the selected model and effort with a bounded or no-history brief. If that is unsupported, let the primary handle the issue or report the limitation. Do not claim a prompt alone overrides a pinned role file.
- Send only the objective, relevant context/files, constraints, file ownership, and acceptance criteria needed by each child. Prefer a self-contained brief or bounded history over copying the entire conversation.
- Child results should contain a concise conclusion, supporting evidence and file/source references, validation performed, and unresolved issues. Avoid raw log dumps and redundant investigations.
