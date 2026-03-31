# Prompt Patterns

Use these patterns when turning a request into a reusable prompt.

## Progressive Disclosure

Start with the smallest useful prompt and add complexity only when the task needs it.

1. Direct instruction
2. Constraint added
3. Reasoning step added
4. Example added

### Example Ladder

- Level 1: "Summarize this document."
- Level 2: "Summarize this document in 3 bullets."
- Level 3: "Read this document, identify the main point, then summarize it in 3 bullets."
- Level 4: Add 2 to 3 examples when the target format is easy to misread.

## Instruction Order

Use this order when the request is ambiguous:

1. Role or mission
2. Inputs or context
3. Constraints
4. Workflow
5. Output format
6. Validation

## Recovery Patterns

- If required context is missing, ask for it and stop.
- If the result is likely to drift, add a validation step.
- If the task needs a repeatable bundle, move it to a skill instead of a prompt.

## Good Prompt Signals

- One clear job.
- One clear output shape.
- One clear owner for the output file.
- One validation step the user can check.

## Bad Prompt Signals

- Vague, all-purpose advice.
- No input boundaries.
- No output contract.
- No reason to exist as a separate artifact.
