---
name: review-checklist
description: Tactical review checklist that applies code-review-generic.instructions.md to diffs and nearby code.
---

# Review Checklist Skill

Use this skill when you need a fast, bug-focused pass over a diff.

## Before You Start

- Read the global instructions.
- Read [code-review-generic.instructions.md](../../instructions/code-review-generic.instructions.md).
- Read the shared lessons file.
- Inspect the diff and nearby code before concluding.

## What This Skill Is For

- Fast defect detection on a concrete diff.
- Turning the generic review policy into an actionable pass.
- Capturing regression risk without re-teaching review theory.

## Tactical Flow

1. Check behavior and contracts first.
2. Check security and data handling next.
3. Check performance and test coverage after that.
4. Separate confirmed defects from open questions.

## Review Checklist

- Does the code still do what the user asked?
- Did any new path bypass existing guards?
- Did the change add a silent failure path?
- Are tests covering the risky branch?
- Could the change break existing consumers or adjacent files?

## Hard Limits

- Do not waste findings on style unless style creates a bug risk.
- Do not claim a bug without evidence from the diff or surrounding code.
- Do not stop at the changed lines if nearby code controls the behavior.

## Finding Format

- High-priority findings need a file/line reference, impact, and smallest fix.
- Low-priority preferences without a failure mode do not count as findings.

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
