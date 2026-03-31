---
name: prompt-builder
description: Turn a one-off request into a reusable prompt, skill, or agent with clear scope, discovery, and output rules.
---

# Professional Prompt Builder

Use this skill when a task should become a reusable prompt, skill, or agent.

## Before You Start

- Read the global instructions.
- Read the shared lessons file.
- Check whether the request is repeated enough to justify a reusable artifact.
- Check for a close public pattern before drafting anything new.

## Decision Guide

### Make a Prompt When

- The task is repeatable but small.
- The main need is a strong workflow and output contract.
- There are no bundled assets or reference files required.

### Make a Skill When

- The task needs examples, references, templates, or scripts.
- The task should be discovered automatically from its description.
- The workflow needs a stable, reusable bundle.

### Make an Agent When

- The task needs a role, constraints, or delegated substeps.
- The task benefits from a strong internal workflow.
- The task should behave differently from the default assistant.

## Discovery Process

### 1. Prompt Identity and Purpose

- What is the intended filename?
- What does the artifact accomplish in one sentence?
- What category does it belong to: code generation, analysis, documentation, testing, refactoring, architecture, or something else?

### 2. Persona Definition

- What role should Copilot embody?
- How senior should the voice be?
- Which languages, frameworks, and tools matter most?
- What background knowledge should be assumed?

### 3. Task Specification

- What is the primary task?
- Are there secondary or optional tasks?
- What input does the user need to provide?
- What constraints or anti-patterns matter most?

### 4. Context and Variable Requirements

- Will the artifact use `${selection}` or `${file}`?
- Does it need `${input:...}` variables?
- Does it need workspace variables such as `${workspaceFolder}`?
- Must it reference other local files or instruction files?

### 5. Detailed Instructions and Standards

- What step-by-step process should Copilot follow?
- Which coding or documentation standards matter?
- Which public or repo patterns should it follow?
- What should it avoid?
- Should it link to existing instruction files?

### 6. Output Requirements

- What format should the output use?
- Should it create new files or edit existing ones?
- Where should output files live?
- Are examples needed to keep the result unambiguous?
- What structure must the output contain?

### 7. Tool and Capability Requirements

- Which tools does the artifact need?
- Which tools are optional?
- Which tools should be avoided?
- Does the task need file edits, search, execution, browser access, or agent delegation?

### 8. Technical Configuration

- Should the artifact run in `agent`, `ask`, or `edit` mode?
- Does it need a specific model?
- Are there environment-specific constraints?
- Does it need a specific file location or directory pattern?

### 9. Quality and Validation Criteria

- How should success be measured?
- What validation steps should be included?
- Which failure modes should be called out?
- How should the workflow recover when context is missing?

## Template Generation

Use this structure when the request calls for a new prompt file:

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
[Checks, success criteria, or failure triggers.]
```

## Best Practices Integration

- Prefer slightly adapted public patterns when a strong one already exists.
- Keep the artifact narrow enough to be reusable.
- Replace vague advice with concrete steps and output contracts.
- Put reusable assets into skills instead of prompts.
- Include examples when they reduce ambiguity.
- Keep the section order predictable so the artifact is easy to re-read.

## Reference Files

- [Prompt Patterns](references/prompt-patterns.md) - Progressive disclosure, instruction order, and recovery patterns for prompt design.

## Output

- Recommended artifact type.
- Proposed filename.
- Frontmatter recommendation.
- Reusable section outline.
- Example section or example artifact shape.
- Any follow-up files that should be added later.
- Why the chosen structure is stronger than the generic version.

