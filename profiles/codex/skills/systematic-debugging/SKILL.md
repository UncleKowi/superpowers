---
name: systematic-debugging
description: Use when diagnosing a bug, failing test or build, performance regression, or unexpected behavior across components, including resuming a previous investigation.
license: MIT (see LICENSE.txt)
---

# Systematic debugging

Follow the user's scope, applicable project instructions, and any required design review. If this installation has a `references/local-project.md` file, read it for project-specific guidance. Continue authorized, reversible investigation in the current session. Ask for input when a necessary decision, permission, or change of scope is missing.

## Locate the first failure

1. Read the actual error and capture a minimal reproduction. Identify the trigger, environment, expected behavior, and observation. If the failure is intermittent, preserve the conditions and uncertainty.
2. Inspect the affected code, recent changes, callers, and one working comparison. Trace a bad value or missing state back to the first boundary where it diverges. Use synthetic inputs and redact diagnostic output. Consult the [debugging techniques](references/techniques.md) for timing, state pollution, or a deeper trace.
3. State a hypothesis and run a probe that distinguishes it from a plausible alternative. Change one variable at a time. After repeated failed hypotheses, revisit the reproducer and the first unobserved boundary.
4. Make the smallest fix supported by the evidence. Preserve public contracts and saved data. For a behavioral bug, use a meaningful regression check where feasible. An existing test or disposable reproducer can be sufficient.
5. Re-run the original trigger and the affected regression checks. Report the evidenced cause, the fix or mitigation, and any conditions still unverified.

## Investigations that span steps or sessions

Use a single session by default for a causal chain. At the outset, open the existing investigation or plan. If there is none, create a task-specific `.superpowers/progress/<task-slug>.md` in the workspace, subject to project conventions. Record the reproduction, current code or artifact, probes and results, ruled-out hypotheses, and next distinguishing probe. Update it after a decisive result and before stopping. On resumption, compare the record with the current code and dependencies. Revisit a ruled-out cause only when its evidence has gone stale.

For an authorized split into independent fixes, use the [execution guide](../requesting-code-review/references/execution.md) and keep one shared investigation record. An obvious isolated correction needs only a focused check. Preserve the project's existing test workflow, approval rules, and agent settings.
