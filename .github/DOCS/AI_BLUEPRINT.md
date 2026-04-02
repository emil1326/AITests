# AI Workflow Blueprint

## Goal

Keep the AI workflow centered on GitHub Copilot and build a small set of reusable instructions around it.

The rule is simple:

- Copilot is the default.
- Prompts are for repeatable tasks.
- Skills are for repeatable workflows that benefit from structure, references, or checklists.
- MCP adds tools only where they help.
- Large refactors use a special prompt for that task.
- A manager agent coordinates large tasks and can hand work out to specialist agents.
- Lessons capture small details, mistakes, wishes, and resolutions so the workflow gets better over time.

## Workflow Layers

### 1. Copilot as the default

Use Copilot for daily editing, short refactors, explanations, and test generation.

### 2. Repo-local instructions

Keep the rules in git so the project carries its own workflow.

Suggested files:

- `AGENTS.md`
- `.github/copilot-instructions.md`
- `.github/instructions/*.instructions.md`
- `.github/prompts/*.prompt.md`
- `.github/skills/<name>/SKILL.md`
- `.github/agents/*.agent.md`
- `.github/lessons/shared.lessons.md`
- `.github/lessons/*.lessons.md`
- `docs/ai-workflow.md`

Use both global and file-specific instruction files:

- Global instructions set the default behavior for the whole repo.
- File instructions with `applyTo` should override or add context for specific file types, such as `**/*.php` or `**/*.astro`.
- When the AI edits a file, it should read the global instruction file first and then the matching file-scoped instruction file.

Use lessons as a lightweight memory layer:

- Each agent gets its own lesson file.
- All agents also share a common lesson file.
- Important details, repeated mistakes, user wishes, and fixed errors should be written into lessons when they matter.
- If a lesson file gets too long, condense it and remove low-value detail so the important parts stay easy to read.
- Before responding, the agent should re-read the relevant instructions and lessons so the current response reflects the latest learned context.

### 3. MCP for safe tool access

Keep the MCP set small and practical.

Good core choices:

- Filesystem access
- Git history and diffs
- GitHub issues and pull requests
- Fetch for docs and pages
- Context7 for up-to-date library docs
- Memory for decisions and notes like Mem0
- Database tools for safe MySQL inspection

## Prompt Set

Keep prompts short and repeatable.

Recommended prompt types:

- Feature prompt
- Bugfix prompt
- Code review / audit prompt
- Deep-audit prompt
- Large refactor prompt
- Documentation prompt
- SQL prompt
- Release prompt
- Prompt-builder prompt

When a public prompt already exists and is close to what we need, prefer a slightly modified version of that prompt instead of inventing a fresh one.

Prompt quality rule:

- Use a clear section order such as Goal, Inputs, Rules, Steps, and Output.
- Use delimiters or file references when the task has multiple inputs.
- Specify the output format explicitly.
- Add examples only when they improve reliability or reduce ambiguity.

## What Each Prompt Should Do

- Feature: define scope, acceptance criteria, and test expectations.
- Bugfix: reproduce, isolate, patch, and validate.
- Code review / audit: check the diff for bugs, regressions, security issues, performance problems, and missing tests.
- Deep-audit: require severity ranking, line references, and a fix strategy.
- Large refactor: handle multi-file changes while preserving behavior and keeping the diff reviewable.
- Documentation: update docs after code changes.
- SQL: generate safe queries, schema changes, indexes, seed data, and validation steps.
- Release: summarize changes, risks, and rollback notes.
- Prompt-builder: turn a one-off task into a reusable prompt or skill with clear scope and output rules.

## What A SQL Prompt Is

A SQL prompt is the task prompt you use when the work touches the database.

Use it for things like:

- table design
- migrations
- indexes
- joins and query cleanup
- seed data
- safety checks before running SQL
- validation steps after schema changes

## Skills

Skills are for tasks that repeat often enough to deserve structure.

Good skills for this project:

| Skill | What it covers | Why it helps |
|---|---|---|
| `ui-styling` | Layout, spacing, typography, colors, responsiveness, accessibility | Keeps the Astro frontend visually consistent and intentional |
| `astro-site` | Astro pages, components, content patterns, static build rules | Keeps the frontend aligned with Astro-specific conventions |
| `php-endpoints` | PHP endpoint patterns, validation, forms, sessions, file uploads | Keeps the backend simple and shared-hosting friendly |
| `mysql-schema` | Schema design, migrations, indexes, query safety | Helps database changes stay correct and small |
| `deploy-shared-hosting` | Upload flow, cPanel/File Manager, build output, env/config notes | Makes deployment repeatable on cheap hosting |
| `review-checklist` | Code review and audit checklist for correctness, security, and regressions | Replaces separate review and audit prompt clutter |
| `prompt-builder` | Convert a task into a good prompt or new skill file | Helps create prompts without guessing the format |

## Skill File Shape

Use a simple skill format inspired by the reference repo, but keep it compact.

Each skill should usually have:

- a short frontmatter block with name and description
- when to use it
- the workflow it should follow
- a small checklist
- references or examples if needed

The actual skill files should live at `.github/skills/<name>/SKILL.md`.

Do not make every skill huge. The point is to make the workflow obvious, not to copy a giant handbook into every file.

## Custom Agents

Use agents for isolated workflows or when a task should follow a tighter process than a normal prompt.

Good agents for this project:

| Agent | What it does | Why it helps |
|---|---|---|
| `ui-review.agent.md` | Reviews Astro and UI changes for layout, accessibility, and polish | Useful when visual quality matters and the task is not just code correctness |
| `php-api.agent.md` | Checks PHP endpoint changes, validation, and request flow | Keeps backend changes small and safe |
| `mysql-audit.agent.md` | Reviews schema, migrations, indexes, and query safety | Helps catch data-model mistakes early |
| `prompt-builder.agent.md` | Turns a one-off request into a reusable prompt or skill | Makes prompt creation more systematic |
| `manager.agent.md` | Breaks a large task into parts, assigns work to specialist agents, and reconciles the results | Enables parallel work across many files without losing structure |

Agents should be used when the task benefits from a tighter scope, a specific checklist, or different tool limits than the default Copilot flow.

## Lessons and Consolidation

The workflow should remember small but useful details without turning memory into clutter.

Lesson files should capture:

- repeated mistakes
- user preferences
- successful fixes
- recurring constraints
- things the agent should not repeat

When a lesson file gets noisy, consolidate it:

- keep the important outcomes
- remove stale or low-value details
- preserve clear reminders about what to do differently next time
- keep the file short enough that the agent can actually re-read it before responding

The manager agent should prefer to update shared lessons when a lesson is useful across agents, and per-agent lessons when the lesson only applies to one workflow.

## Agent Hierarchy

For large work, the workflow should be hierarchical instead of flat.

Recommended order:

1. Manager agent reads the task, the repo, and the instructions.
2. Manager agent splits the work into smaller units.
3. Manager agent delegates to specialist agents in parallel where possible.
4. Specialist agents return findings or edits for their slice of work.
5. Manager agent reconciles the results, checks for conflicts, and produces the final answer or patch plan.

Use this model for bulk work such as:

- reviewing many files
- applying the same change across many files
- fan-out edits across dozens of files, including roughly 50-file tasks
- auditing a large diff
- refactoring a repeated pattern across the repo

The manager should not guess when the task is unclear.

When uncertain, it should check:

- the repo first
- the matching instruction or skill files next
- MCP tools next
- the web last for current docs, repos, and examples

If the work spans many files, the manager should prefer fan-out over manual serial review, but keep the final reconciliation step central so the result stays consistent.

## AI File Strategy

Do not add files just because they sound useful. Add them only when they solve a repeated task.

Start with:

- one instruction file
- one or two file-scoped instructions for the most common file types
- one prompt per repeated task
- a small set of skills for the workflows you will actually repeat
- a few agents for higher-value review or builder flows
- shared lessons plus per-agent lesson files

Add more only when the workflow proves it needs them.

## Research Behavior

When the AI is uncertain, it should not guess.

It should check, in order of usefulness:

- the repo files
- the matching instructions or skill files
- MCP tools
- the web for current docs, repos, and examples

Prefer web-backed answers over memory when the topic depends on up-to-date library behavior, current hosting support, or current public patterns.

Prefer slightly modified public prompts, skills, or agent patterns over inventing a fresh custom version each time.

## Good Defaults

- Prefer repo-local prompts over copying instructions into chat every time.
- Prefer adapting good public patterns instead of inventing new ones.
- Prefer small, reviewable changes over broad automation.
- Prefer docs and tests over guesswork.
- Prefer web-backed patterns that are close to the task, then adapt them slightly instead of starting from zero.

## What Not To Do

- Do not replace Copilot with a second paid AI product.
- Do not add a large MCP catalog on day one.
- Do not create prompt files that never get reused.
- Do not make the AI workflow more complex than the app stack.