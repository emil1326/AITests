---
description: 'Guidelines for creating high-quality prompt files for GitHub Copilot'
applyTo: '**/*.prompt.md'
---

# Copilot Prompt Files Guidelines

Use these rules when creating or editing reusable prompt files.

## Purpose

- Make each prompt do one concrete job well.
- Prefer prompts that produce one specific artifact or decision.
- If the task needs bundled templates, scripts, or reference data, use a skill instead.

## Frontmatter

- Use `name` when the prompt should appear as a slash command.
- Use `description` as a one-line outcome, not a slogan.
- Use `agent` to select the right execution mode when the prompt depends on it.
- Add `argument-hint` when the prompt expects short user input.
- Only add `model` or `tools` when the prompt truly needs them.
- Keep one field per line for readability and maintenance.

## Body Structure

- Start with a direct title and a one-line mission.
- Prefer this flow when it fits the task:
  - Mission
  - Inputs / Preconditions
  - Scope
  - Workflow
  - Output
  - Validation
  - Failure modes
- Keep steps concrete and ordered.
- Say what not to do when the boundary matters.
- Make the output contract explicit: file path, format, required sections, and success criteria.

## Context Handling

- Use `${selection}`, `${file}`, `${workspaceFolder}`, or `${input:...}` only when they are essential.
- Explain what Copilot should do if required input is missing.
- If a required path is missing, stop and ask rather than guessing.
- Reference related prompt or instruction files with relative links when that reduces ambiguity.

## Tool Guidance

- Use the smallest tool set that works.
- List tools in the order they should be used when order matters.
- Warn before destructive actions.
- Prefer prompts that can run without extra clarification.

## Quality Rules

- Use imperative verbs.
- Replace implied context with explicit context.
- Include validation steps the user can actually run or inspect.
- Name the stack, files, and constraints when the prompt targets a known workflow.
- Add failure triggers so the agent knows when to halt or retry.

## Example Outline

```md
---
description: 'Create an implementation plan from a feature request'
agent: 'ask'
argument-hint: 'feature or refactor target'
---

# Create Implementation Plan

## Mission
[One sentence describing the task and desired outcome.]

## Inputs
[Variables, file paths, selection context, or user-provided details.]

## Workflow
1. [Step one]
2. [Step two]
3. [Step three]

## Output
[File paths, formats, and required sections.]

## Validation
[Checks, success criteria, and failure triggers.]
```

## Maintenance

- Update the prompt when dependencies or repository conventions change.
- Re-read `AGENTS.md` and the relevant lessons before editing a prompt.
- If a prompt keeps being reused, move reusable logic into a skill.
