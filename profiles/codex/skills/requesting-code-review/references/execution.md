# Running and resuming a substantial change

## Start with one record

Use the project's existing task-specific plan, issue work file, or investigation log. A shared read-only spec can be linked from the record. If there is no writable record for this task, create `.superpowers/progress/<task-slug>.md` in the workspace with a stable, task-specific name. Follow the project's location and tracking rules. A review-only request leaves the workspace untouched.

Before implementation, record the scope, chosen mode, acceptance criteria, and next action. Keep one row per task. The coordinating session updates the file at each verified milestone, on a blocked or failed check, and before a handoff. Preserve unrelated entries. A short record is enough.

```markdown
# Import migration
Mode: single session

| Task and criterion | State | Artifact and check |
| --- | --- | --- |
| Schema reads v1 data | Verified | schema.py at revision A; targeted compatibility test, 4 passed |
| Parser accepts v1 dates | In progress | parser.py; parser dependency changed at B; rerun its date tests |
| Reader imports the fixture | Pending | Depends on parser |

Next: run the parser date tests on B, then check the reader with a v1 fixture.
```

For uncommitted work, identify the actual worktree and affected changes or artifact as well as the base revision. Record the command or observation and its result against the state it checked. Keep private data and credentials out of progress files.

## One session

Implement the next unfinished step in dependency order. Run its relevant checks and update the record. Continue directly to the next step. When all steps are ready, review the complete diff against the original criteria and test the integrated behavior. Use an independent reviewer when authorized and available. Otherwise self-review and identify it as such. This mode saves agent calls and gives one implementer continuity across coupled changes.

## Fresh implementer per task

Choose this mode for separable tasks when delegation is authorized and available. Give each fresh implementer a bounded brief with the criterion, owned files, dependencies, and expected checks. Keep checkpoint ownership with the coordinating session. Schedule overlapping changes in dependency order.

For each result, inspect the actual diff against its criterion, then review code quality, compatibility, and tests. Use an independent reviewer when authorized and available. Obtain or run checks covering the delivered state. A worker's “green” without inspectable evidence leaves the item open. Correct findings and re-review the affected area before marking the task verified. After the tasks pass, review the combined change and check the integration boundary. If a requested independent worker or reviewer is unavailable, report that limit, keep any required independent review open, and identify any self-review carried out.

## Resume from evidence

Read the record before editing. Match it to the current checkout, diff, inputs, and available test results. Keep verified work whose evidence still applies. If an input, caller, configuration, or dependency changed, reopen the affected criterion and rerun its check. Continue at the first unresolved dependency. Leave incomplete checks open with the next exact action. A progress entry never substitutes for evidence of completion.
