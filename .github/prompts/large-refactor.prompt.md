---
name: large-refactor
description: "Refactor multiple files while preserving behavior, minimizing incidental changes, and keeping the diff reviewable."
argument-hint: "the refactor goal and any files to preserve"
---

# Large Refactor

Refactor the requested area while preserving behavior and keeping the diff reviewable.

## Mission

- Improve structure or maintainability without changing the intended result.

## Inputs

- The area to refactor and the behavior that must stay stable.
- Any files that should remain untouched.
- The reason the refactor matters now.

## Before You Start

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check the matching skills and any relevant agent lesson files.
- If the task touches many files, use the manager-agent workflow to split the work.

## Refactor Rules

- Preserve behavior unless the request explicitly asks for a change.
- Keep incidental edits out of the diff.
- Reuse existing patterns instead of inventing new ones.
- Split the change into small steps that can be reviewed independently.
- Recheck docs and tests after the refactor.
- Do not do a broad cleanup just because the code looks imperfect.

## Suggested Flow

1. Map the current structure and the invariants that must remain true.
2. Identify repeated patterns, duplicated logic, or awkward boundaries.
3. Choose the smallest slice that can be improved safely.
4. Refactor one slice at a time.
5. Validate each slice before moving on.
6. Reconcile the final state against the original behavior.

## Output Contract

- Refactor plan.
- Files changed.
- Behavior preserved.
- Validation performed.
- Any remaining cleanup left intentionally undone.

## Validation

- The behavior stays the same unless the request explicitly changes it.
- The diff does not include unrelated cleanup.
- Each slice is reviewable without reconstructing hidden context.
- Tests or checks cover the parts most likely to drift.
