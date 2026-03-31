---
name: prompt-builder
description: "Turn a one-off request into a reusable prompt, skill, or agent with clear scope, discovery, and output rules."
argument-hint: "the workflow or task you want to turn into a reusable artifact"
---

# Prompt Builder

Turn the request into the smallest reusable artifact that will still work in another repo.

## Mission

- Decide whether the task belongs in a prompt, skill, or agent file.
- Reuse a strong public pattern when one already fits.
- Keep the artifact narrow, explicit, and easy to reuse.

## Before You Start

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Check whether the request is repeated often enough to deserve reuse.
- Look for a close public pattern before inventing a custom one.
- If the artifact is a prompt or agent, also read the local prompt and agent instruction files.

## Discovery Process

### 1. Identity and Purpose

- Identify the intended filename.
- Define the artifact in one sentence.
- Classify it as a prompt, skill, or agent.

### 2. Persona Definition

- Decide what role and expertise the artifact should project.
- Keep the persona specific enough to reduce guesswork.

### 3. Task Specification

- Define the primary task.
- List secondary tasks only if they are truly needed.
- Name the required user input and constraints.

### 4. Context and Variables

- Decide whether the artifact needs `${selection}`, `${file}`, or `${input:...}` variables.
- Decide whether it depends on other local files or instruction files.

### 5. Detailed Instructions and Standards

- Write the workflow in short, direct steps.
- Include the hard limits that matter.
- Add examples when they materially reduce ambiguity.

### 6. Output Requirements

- Specify the file path, format, and required sections.
- State what counts as a valid result.
- Make validation steps explicit.

### 7. Tool and Capability Requirements

- List only the tools the artifact truly needs.
- Keep permissions tight.
- Add agent delegation only when it improves the workflow.

### 8. Technical Configuration

- Decide whether the artifact should run in `agent`, `ask`, or `edit` mode.
- Add a specific model only when the role benefits from it.

### 9. Quality and Validation Criteria

- Define how success will be judged.
- Call out failure modes and recovery steps.
- Keep the output contract measurable.

## Builder Rules

- Decide whether the best fit is a prompt, a skill, or an agent.
- Keep the scope narrow.
- Use clear sections and concrete output rules.
- Prefer a lightly adapted public pattern over a fresh prompt from scratch.
- If the task needs repeated steps or reference assets, consider a skill.
- If the task needs isolation or a strict workflow, consider an agent.

## Template Generation

Use this structure when the request should become a prompt:

```md
---
description: "[Clear, concise outcome statement]"
agent: "[agent|ask|edit or a custom agent name]"
tools: ["[tools only when needed]"]
model: "[only if a specific model is required]"
argument-hint: "[short input hint if needed]"
---

# [Prompt Title]

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

## Output

- Recommended file type
- Proposed filename
- Frontmatter recommendation
- Reusable section outline
- Example section or example artifact shape
- Any follow-up files that should exist
- Why the chosen structure is stronger than the generic version
