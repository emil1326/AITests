---
name: review-checklist
description: Review code for correctness, regressions, security issues, performance problems, and missing tests.
---

# Review Checklist Skill

Use this skill when the task is to review code, audit a diff, or check whether a change is safe.

## When to Use This Skill

- You need to review a diff before merge.
- You need to check whether a change introduces regressions or missing tests.
- You need a concrete bug-focused review rather than a style pass.
- You need to confirm that a change still matches the repo's contracts.

## Before You Start

- Read the global instructions.
- Read the shared lessons file.
- Read the relevant agent lesson file if one exists.
- Inspect the diff and nearby code before concluding.

## What This Skill Is For

- Catching concrete breakages before merge.
- Separating real defects from style opinions.
- Looking for regression risk in the changed code and adjacent code.
- Producing findings that a developer can act on immediately.

## Review Checklist

- Does the code still do what the user asked?
- Did any new path bypass existing guards?
- Did the change add a silent failure path?
- Are tests covering the risky branch?
- Could the change break existing consumers or adjacent files?

## Controlled Flow

1. Read the diff and the surrounding code path.
2. Look for behavior mismatches first.
3. Check security and data handling next.
4. Check performance and regression risk after that.
5. Note missing tests, missing validation, or mismatched docs.
6. Separate confirmed findings from questions.

## Hard Limits

- Do not waste findings on style unless style creates a bug risk.
- Do not claim a bug without evidence from the diff or surrounding code.
- Do not stop at the changed lines if nearby code controls the behavior.

## Finding Format

### Good Finding

- `High`: Missing validation on an endpoint that accepts user input.
- File and line reference.
- Why it matters.
- Suggested fix.

### Weak Finding

- `Low`: I would maybe prefer a different naming style.

Why this is weak:

- It does not describe a defect or regression.
- It is preference, not evidence.

## Output Contract

- Findings ordered by severity.
- File and line references when possible.
- A short fix recommendation for each finding.
- Separate confirmed defects from open questions.

## Reference Files

- [Finding Patterns](references/finding-patterns.md) - What counts as a good finding, severity guidance, and evidence checks.

## Validation Questions

- Does the changed code still do what the user asked?
- Did any new path bypass existing guards?
- Did the change add a silent failure path?
- Are tests covering the riskier branch?
- Could the change break existing consumers or adjacent files?
