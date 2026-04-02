# Project Instructions

- Keep the stack simple: Astro static frontend, plain PHP backend, MySQL or MariaDB, shared hosting.
- Prefer repo-local prompts, skills, and file-scoped instruction files over inventing new workflow files.
- When uncertain, check the repo, the relevant instruction files, the MCP tools, and then the web.
- Prefer slightly adapted public prompts over writing a fresh custom prompt every time.
- For large tasks, use a manager-style agent to split work, fan out to specialist agents, and reconcile the results.
- Do not guess when the repo, MCP tools, or the web can answer the question.
- Do not guess about hosting, APIs, or library behavior if the current docs can be checked.
- Re-read the global instructions, the matching file instructions, and the relevant lesson files before responding.
- When editing prompt files or agent files, also read .github/instructions/prompt.instructions.md and .github/instructions/agents.instructions.md.
- Record useful lessons, mistakes, user wishes, and resolutions in the shared lessons file and the relevant agent lesson file.

## Canonical Agent Set

Keep the visible agent set small. The repo should revolve around these 10 agents:

1. `gem-orchestrator` - phase detection, routing, retries, and synthesis.
2. `Planner` - DAG planning, decomposition, and assumption locking.
3. `Researcher` - codebase discovery and structured evidence gathering.
4. `Implementer` - TDD implementation and minimal safe changes.
5. `Reviewer` - security, secrets, PRD compliance, and correctness review.
6. `Architecture Reviewer` - architecture, tradeoffs, and adversarial challenge.
7. `Browser Tester` - browser verification, E2E, accessibility, and visual checks.
8. `Documentation Writer` - docs parity, walkthroughs, and diagrams.
9. `UX Designer` - JTBD, journey mapping, and UX research artifacts.
10. `Context7` - external library and framework documentation verification.

## Retired Agent Families

- Keep specialized one-off roles in skills when they are situational.
- Do not reintroduce duplicate agents for tasks already covered by the canonical set.
- If a new agent overlaps with one of the 10 above, merge the concept into the canonical owner instead of adding another file.
