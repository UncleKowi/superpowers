---
name: verification-before-completion
description: Use before claiming code, a fix, installation, build, or deployment is complete, or when reconciling recorded results after a handoff or a dependency change.
license: MIT (see LICENSE.txt)
---

# Verification before completion

Follow current user and project requirements, including required design checks. If this installation has a `references/local-project.md` file, read it for project-specific guidance. Work within the existing authorization for checks, data access, publication, and resource use.

1. **Match the claim to a check.** For a bug, exercise the original trigger. For an installation, verify the destination, discovery metadata, and required files. For a deployment, inspect the actual target and final operation status. For a small reversible edit, a focused test or direct observation can suffice.
2. **Run checks on the delivered state.** Read the exit status and relevant output. Treat skipped, failed, unavailable, and unfinished checks as open. Inspect a worker's evidence against the actual change and run missing checks. A passing build demonstrates compilation or packaging. A behavioral claim needs a behavioral check.
3. **Reconcile existing results.** When resuming substantial work, open the task's progress file. Compare the tested revision or working-tree change, inputs, dependencies, and configuration with the current state. Keep results that still cover it and rerun the affected checks after a material change. A checked box alone cannot establish that a test passed.
4. **Check the combined result.** For a multi-step change, exercise the acceptance criteria across the touched boundaries after integration. In delegated work each task needs its review and evidence before closure. In single-session implementation use step checks and one final review of the whole change.
5. **Report the evidence.** For a tracked task, record the command or observation, outcome, tested state, and any remaining blocker or next action in the existing work file before handoff. Report what actually passed and which requested behavior remains unverified. A review-only task reports this in the response and leaves files untouched.

Keep verification proportional. Distinguish installed skill files from recognition in a running chat, a simulated UI from physical-device behavior, and benchmark throughput from model quality. Use synthetic fixtures and existing project checks where appropriate.
