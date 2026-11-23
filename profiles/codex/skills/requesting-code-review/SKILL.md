---
name: requesting-code-review
description: Use when reviewing code or starting, resuming, or handing off substantial implementation work such as a multi-file feature or a change with integration risk.
license: MIT (see LICENSE.txt)
---

# Requesting code review

Follow the user's scope, the host's delegation rules, and the applicable project instructions, including any design-review procedure. If this installation has a `references/local-project.md` file, read it for the user's project-specific guidance.

## Choose the amount of review

- For a small, clear edit, inspect the affected behavior and run the focused check. Finish in the current session without a separate plan, progress file, or reviewer.
- For substantial implementation, choose the execution mode at the start or on resumption. Work in one session by default, especially when tasks share state or cost matters. Use fresh implementers for independently testable tasks when the user or applicable higher-priority instructions explicitly request delegation and the host supports it. Read the [execution and resumption guide](references/execution.md) for the work record and review boundaries in both modes.
- For a review-only request, inspect the change and report findings. Keep files, the index, and project progress records read-only.

## Review the actual change

1. Establish the intended behavior, acceptance criteria, project constraints, and compatibility requirements. Use the current request or existing plan.
2. Identify what to review. For a PR or branch use the actual merge base and head. For local work include staged, unstaged, and relevant new files. For an installation compare the prepared and installed artifacts. Preserve the user's unrelated work.
3. Trace the change through its callers, persisted data, and relevant tests. Check the actual failure paths and integration boundaries. The [reviewer checklist](code-reviewer.md) covers evidence and findings.
4. Anchor each actionable finding to a file and line, a triggering condition, and a concrete effect. Distinguish observed issues from unresolved risks. Follow the requested review format.
5. For implementation, fix in-scope findings, re-review the affected changes, and verify the result. For a review-only task, present the findings. Identify self-review when it affects the conclusion.

Run the relevant checks before reporting delivery. State material verification limits and any outstanding findings. Commits, publication, deployment, data changes, and model changes require their own authority.
