---
name: deep-audit
description: "Perform a deeper audit of code, architecture, data flow, and failure modes with explicit evidence."
argument-hint: "the area or files to audit"
---

# Deep Audit

Audit the target area for correctness, operational risk, and hidden failure modes.

## Mission

- Go beyond a surface review and verify how the code behaves under real constraints.

## Inputs

- The target area, files, or subsystem.
- Any known risk, incident, or question the audit should answer.
- Relevant tests, docs, or schema files if the audit needs cross-checking.

## Before You Start

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check the relevant skills and agent lesson files.
- Read adjacent code and docs, not just the target file.
- If the audit spans many files, split it into sub-audits and reconcile the findings.

## Audit Passes

1. Boundary and input handling.
2. Data integrity and query safety.
3. Failure handling and recovery.
4. Performance hot spots and resource usage.
5. Behavioral drift between code, tests, and docs.
6. Missing validation or missing coverage.

## Audit Style

- Use evidence, not intuition.
- Read adjacent code and docs together so the finding is grounded in the real flow.
- Separate confirmed defects from uncertainty.
- Call out behavior that is technically correct but operationally fragile.
- Prefer narrower findings that a maintainer can act on immediately.

## Audit Rules

- Do not guess.
- Use the repo first, then instructions and lessons, then MCP tools, then the web.
- Check the implementation, nearby code paths, and the docs together.
- Look for behavior that is technically correct but operationally fragile.
- Separate confirmed defects from uncertainty.

## Output Contract

- Findings ordered by severity.
- File and line references when possible.
- Why each finding matters.
- A recommended fix or mitigation.
- Any open assumption that still needs confirmation.

## Failure Modes

- Reading only the changed file and missing the surrounding control flow.
- Reporting a theoretical risk without evidence from the code.
- Collapsing uncertainty into a bug claim.
