---
name: documentation
description: "Update docs after code changes so the repository stays in sync with the implementation."
argument-hint: "the code change or docs that need updating"
---

# Documentation Update

Update the documentation so it matches the implementation and the repo workflow.

## Mission

- Keep the docs true to the code, not the other way around.

## Inputs

- The code change or implementation area that needs documentation.
- The user-facing doc, workflow doc, or bootstrap doc that is now stale.
- Any related prompt, skill, or agent file if the workflow changed.

## Before You Start

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check the code change and any docs it already affects.
- If the docs refer to a file type, read the matching file instructions first.
- If the docs are part of a broader workflow change, check the related prompt or agent file too.

## Documentation Rules

- Keep docs accurate and current.
- Prefer small doc edits that match the actual implementation.
- Do not document behavior that the code does not support.
- When a code change alters usage, update the user-facing docs and any workflow docs that explain it.
- If the docs are stale, fix them in the same change rather than leaving a note for later.
- Include the operational detail a future maintainer would actually need.

## Workflow

1. Identify which docs are now affected.
2. Read the code path so the doc reflects real behavior.
3. Update the smallest doc surface that keeps the repo accurate.
4. Keep examples, file references, and instructions consistent with the code.
5. Check that the doc does not overstate behavior.

## Output Contract

- Docs updated.
- Code behavior documented.
- Any unresolved doc gap.
- Files and line references when possible.

## Validation

- The docs match the implementation.
- The user-facing usage path is still accurate.
- No doc claims behavior that the code does not provide.
