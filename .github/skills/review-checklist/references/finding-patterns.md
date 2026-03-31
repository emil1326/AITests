# Finding Patterns

Use these patterns when reviewing a diff for concrete problems.

## What Counts as a Good Finding

- The issue is a real defect, regression, or missing safeguard.
- The file and line can be pointed to directly.
- The explanation says why the issue matters.
- The fix is narrow and credible.

## What Does Not Count

- Style preferences.
- Pure naming opinions.
- Speculation without code evidence.
- Complaints that do not change behavior.

## Severity Guide

### High

- Breaks user-visible behavior.
- Introduces a security or data-integrity risk.
- Creates a silent failure path.

### Medium

- Weakens validation.
- Creates a likely regression path.
- Leaves a risky path untested.

### Low

- Small correctness concern.
- Minor maintainability issue with a clear behavioral link.

## Evidence Checklist

Before writing a finding, confirm:

1. The code path exists in the diff or nearby code.
2. The risk is not already handled elsewhere.
3. The behavior change can be explained plainly.
4. The fix does not require inventing a new problem.
