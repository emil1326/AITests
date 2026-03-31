---
name: bugfix
description: "Reproduce, isolate, patch, and validate a bug with the smallest safe change."
argument-hint: "what is broken and any error message or file path"
---

# Bugfix Repair

Fix the reported bug with the smallest safe change that addresses the real cause.

## Mission

- Reproduce the failure, trace the code path, patch the root cause, and verify the fix.

## Inputs

- The observed failure, error message, or incorrect behavior.
- The file path or feature area that appears related.
- Any reproduction steps the user already has.

## Before You Change Code

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check the matching skills and any relevant agent lesson files.
- If the bug involves a file type with file-scoped guidance, read that instruction first.
- If the issue spans many files, split it and use the manager agent workflow.

## Working Rules

- Reproduce the problem from the repo or the evidence provided.
- Identify the root cause before patching.
- Keep the fix as small as possible.
- Do not guess when the repo, MCP tools, or the web can confirm behavior.
- If the root cause is unclear, stop at the narrowest useful blocker instead of widening the patch.

## Workflow

1. State the observed behavior.
2. State the expected behavior.
3. Trace the exact code path that causes the mismatch.
4. Patch the smallest correct fix.
5. Validate the fix and check nearby paths for regression risk.

## Output Contract

- Root cause.
- Files changed.
- Fix summary.
- Validation performed.
- Any remaining risk or follow-up.

## Validation

- The bug is reproducible before the fix.
- The patch addresses the actual cause, not just the symptom.
- The fix does not widen the scope of the original problem.
- Nearby code paths still behave as expected.

## Failure Modes

- Patching the symptom while leaving the root cause untouched.
- Adding a broader refactor when the bug needs a narrow fix.
- Claiming the bug is fixed without a real validation step.

