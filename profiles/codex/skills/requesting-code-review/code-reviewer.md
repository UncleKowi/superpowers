# Focused code-review checklist

Adapted from Superpowers' reviewer template. Use in the current session, or
as a brief for an independent reviewer only when delegation is authorized.
The active `SKILL.md`, current task, and project instructions define scope.

## Inputs

Use the actual request or approved requirements, exact changed files or base
and head, relevant project constraints, and check results with their provenance.
Do not demand a written plan for a task that never needed one. If delegated,
supply this bounded context rather than an unnecessary copy of the full chat.

## Check only what matters to this change

- Does the changed behavior match the current requirements and preserve
  explicit user choices, public contracts, stored data, and unrelated work?
- Can a concrete input, error, empty state, repeated operation, cancellation,
  or concurrency condition reveal a regression? Trace the affected caller.
- Are input validation, authentication, ownership, and error handling adequate
  where this change actually touches them? Avoid an unrelated security audit.
- Do existing or added tests exercise real behavior? Are relevant regressions
  covered? Which checks were actually run on the reviewed state?
- If schemas, persisted formats, APIs, or installation paths changed, can
  existing data or consumers still work, and are migration limits clear?
- Does an observed platform, browser, native app, device, or model result
  support the claimed scope? State any consequential untested assumption.

Inspect with read-only commands. Do not move HEAD, alter the index or files,
create another reviewer, or run mutating production checks during a review-only
task. If an earlier test result covers unchanged code and the host permits
reusing it, assess that evidence rather than automatically rerunning it.

## Findings and conclusion

Lead with actionable findings in severity order using the host's required
format. Each finding needs a verified file and narrow line location, the
trigger, the observed or reasoned defect, and the practical effect. An
inference must be labeled. Suggest a focused correction when it is not obvious.

Use impact-appropriate severity: data loss, access bypass, or broken core
behavior is different from a low-impact edge case or optional polish. Do not
inflate a preference into a defect or demand features outside the task.

When no actionable issue was found, say that directly. Briefly state the
checks inspected and any material remaining uncertainty. For a self-review,
identify that limit when independence would affect the user's interpretation.
