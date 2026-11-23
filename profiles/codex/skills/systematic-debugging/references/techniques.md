# Focused debugging techniques

Adapted from Superpowers' root-cause tracing, condition-based waiting, and
defense-in-depth references. These are optional techniques, selected for the
observed failure. The active `../SKILL.md` and existing project rules govern.

## Trace a bad value backward

Start at the failing operation and inspect its inputs. Follow each caller until
you find where the invalid value, missing state, or unintended default first
appears. Compare with the nearest working path. If necessary, add temporary,
redacted diagnostics around the suspected boundary and remove them once their
purpose is served. Prefer an existing logger that is actually visible in the
test environment; do not dump environment variables or private data.

An empty working directory can resolve to the current source directory. Validate
the real target at the boundary that owns that contract, and test the caller
that supplied the empty value. Do not add identical checks to every layer by
default or claim a bug is impossible because several guards were added.

## Wait for the observed condition

For readiness, file creation, async completion, or UI updates, prefer the
project's event, locator, or bounded wait primitive to a guessed sleep. Include
a deadline, useful failure details, and cleanup for listeners or processes the
check owns. Choose polling intervals appropriate to the operation; a local
predicate and a remote service do not need the same interval. Read fresh state
on each attempt. Keep waits within the host's interaction and update limits.

Use a fixed elapsed interval only when time itself is the behavior under test,
such as debounce or throttling, and tie it to the documented timing contract.
Condition-based waiting does not authorize repeated side-effecting requests.

## Find test-order or state pollution

Compare a failing test alone with the same test after its suspected predecessor.
Narrow the preceding set using the project's actual runner, retaining exit
codes and relevant output. Use an isolated temporary workspace and synthetic
data. Restore only fixtures and processes owned by the check. Run the project's
test runner directly so failures and inconclusive probes remain visible.

## Add a guard where it protects a real boundary

After identifying the source, add validation or an environment guard where it
prevents a concrete recurrence. Test a relevant bypass path when one exists.
Resolve and validate complete paths rather than relying on a string prefix,
especially on Windows. Keep changes proportional to the bug and the contract.
