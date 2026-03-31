---
name: feature
description: "Implement a focused feature with clear scope, acceptance criteria, and a reviewable change set."
argument-hint: "what the feature should do"
---

# Feature Implementation

Implement the requested feature as a small, complete, reviewable change.

## Mission

- Turn the feature request into working code that fits the existing Astro + PHP + MySQL/shared-hosting stack.
- Keep the change narrow enough to review without losing the end-to-end path.

## Inputs

- The feature request and any acceptance criteria the user provided.
- The current page, component, endpoint, or schema that the feature touches.
- Any matching prompt, skill, or agent file that already covers the stack.

## Before You Change Code

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check the matching skills and any relevant agent lesson files.
- If the request touches prompt files or agent files, read .github/instructions/prompt.instructions.md and .github/instructions/agents.instructions.md first.
- If the feature spans many files, split it and use the manager agent workflow.

## Working Rules

- Prefer existing project patterns over inventing new ones.
- Keep the change small, explicit, and end-to-end.
- If the feature touches PHP, Astro, MySQL, or deployment, read the matching instruction or skill first.
- When uncertain about library or hosting behavior, check the repo, MCP tools, and the web instead of guessing.
- Do not broaden the scope unless the narrower change cannot satisfy the request.

## Workflow

1. State the feature in one sentence.
2. Identify the files and entry points that matter.
3. Map the existing pattern the feature should follow.
4. Implement the smallest usable slice.
5. Add validation or tests for the risky path.
6. Update docs only when the user-facing behavior actually changed.

## Output Contract

- Short implementation plan.
- Files changed.
- Existing pattern followed.
- Validation performed.
- Remaining risks or follow-up work.

## Validation

- The feature works end to end in the current stack.
- The change stays aligned with existing project patterns.
- Any risky branch has at least one explicit check or test.
- The diff is still small enough to review without extra context.

## Failure Modes

- A feature implementation that only covers the happy path.
- A larger-than-needed change that rewrites unrelated code.
- A UI or endpoint change that is not matched by validation.
- A doc update that claims behavior the code does not yet support.
