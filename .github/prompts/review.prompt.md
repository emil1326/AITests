---
name: review
description: "Review a diff for bugs, regressions, security issues, performance problems, and missing tests."
argument-hint: "the files or diff to review"
---

# Review Diff

Review the change as if it were going to land in production.

## Mission

- Find concrete defects, regressions, and missing safeguards in the diff.

## Inputs

- The diff or the files to review.
- The surrounding code path and any nearby tests.
- The repo conventions that matter for the change.

## Before You Review

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check the matching agent lesson file if one exists.
- Inspect the changed files and nearby code before forming conclusions.
- If the review spans many files, use the manager-agent workflow to split the pass by concern.

## Review Passes

1. Correctness and behavior drift.
2. Security and data handling.
3. Performance or operational risk.
4. Test coverage and validation gaps.
5. Documentation or contract mismatches.

## Finding Quality

- Good findings name the concrete bug or regression, not a vague dislike.
- Good findings include file and line references when possible.
- Good findings explain why the issue matters to users or maintainers.
- Good findings suggest the smallest credible fix.
- Weak findings are style opinions without a real failure mode.

## Review Rules

- Find concrete problems first.
- Focus on correctness, regressions, security, performance, and test coverage.
- Do not guess when the repo, MCP tools, or the web can answer the question.
- If there are no findings, say so clearly and mention any residual risk or test gap.
- Treat style-only comments as out of scope unless they hide a real risk.

## Output Contract

- Findings ordered by severity.
- File and line references when possible.
- A short fix recommendation for each finding.
- Separate confirmed defects from open questions.

## Validation Questions

- Does the changed code still do what the user asked?
- Did any new path bypass existing guards?
- Did the change add a silent failure path?
- Are tests covering the riskier branch?
- Could the change break existing consumers or adjacent files?
