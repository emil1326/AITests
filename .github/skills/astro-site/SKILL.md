---
name: astro-site
description: Work on Astro pages, components, and static-site patterns with strict static-first rules, explicit validation, and minimal client JavaScript.
---

# Astro Site Skill

Use this skill when the task touches Astro pages, components, layouts, routing, or site structure.

## Before You Start

- Read the global instructions.
- Read the shared lessons file.
- Read the Astro file instructions.
- Inspect the existing page, layout, and component pattern before changing anything.
- Check whether the page can stay static-first without weakening the request.
- Read [references/page-patterns.md](references/page-patterns.md) before making a design or structure decision.

## Controlled Flow

1. Identify the exact page, component, or layout being changed.
2. Read the nearest existing Astro patterns and reuse them if they already solve the problem.
3. Decide whether the page can remain fully static.
4. Add client-side JavaScript only if the request explicitly needs interaction, state, or browser-only APIs.
5. Keep the change narrow enough that the build output stays predictable on shared hosting.
6. Verify the page still matches the site’s visual language and routing structure.

## What This Skill Is Actually For

- Building static pages that load fast and stay easy to deploy.
- Updating Astro content without pulling in unnecessary client-side complexity.
- Preserving the site's existing component and layout language.
- Adding the smallest possible interactive island only when the request truly needs it.

## Common Page Patterns

- Landing page: hero, proof points, CTA, and a small supporting section.
- Content page: frontmatter-driven content, a compact sidebar or metadata block, and readable prose.
- Feature page: one main claim, a short feature grid, and one direct next step.
- Interactive page: static shell first, then one isolated island for the actual interaction.

## Reference-Backed Rules

- Prefer Astro's static-first shape for informational pages.
- Keep browser-only logic isolated to the smallest visible surface.
- Do not turn a content page into a framework app.
- Treat layout consistency as a real requirement, not a style preference.
- If a page can be built from data and slots, do that before inventing state.

## Examples

### Good Example: Static Content Page

```astro
---
const sections = [
	{ title: 'Fast to load', body: 'Static content keeps hosting simple.' },
	{ title: 'Easy to maintain', body: 'Content lives in one place.' },
	{ title: 'Predictable output', body: 'The build always produces the same page shape.' },
];
---

<main class="page-shell">
	<header class="hero">
		<p class="eyebrow">Astro static site</p>
		<h1>Build pages that stay simple to deploy.</h1>
		<p>Use Astro markup first, then add interactivity only when the request truly needs it.</p>
	</header>

	<section class="feature-grid" aria-label="Benefits">
		{sections.map((section) => (
			<article class="feature-card">
				<h2>{section.title}</h2>
				<p>{section.body}</p>
			</article>
		))}
	</section>
</main>
```

Why this is good:

- The page is static and predictable.
- The content is obvious from the markup.
- The structure is easy to reuse elsewhere.
- No client JavaScript is needed to deliver the page.

### Good Example: Small Interactive Island

```astro
---
import SearchFilters from '../components/SearchFilters.tsx';
---

<main>
	<section>
		<h1>Browse resources</h1>
		<p>Use a static page shell, then isolate the filter controls.</p>
	</section>

	<SearchFilters client:visible />
</main>
```

Why this is good:

- The interactive part is isolated.
- The rest of the page remains static.
- The `client:visible` boundary is explicit and minimal.

### Bad Example: Unnecessary Client Complexity

```astro
---
import { useState } from 'react';
---

<script>
	// unnecessary page-wide scripting for content that could be static
</script>

<main>
	<!-- page shell, but the whole thing now depends on client behavior -->
</main>
```

Why this is bad:

- It adds client behavior without proving the need.
- It makes the page harder to host and reason about.
- It hides what is actually static versus interactive.

## Hard Limits

- Do not add client islands by default.
- Do not introduce framework-specific complexity that a static page does not need.
- Do not change the deployment assumptions unless the user explicitly asks for that.
- Do not invent new layout systems if an existing one already fits.
- Do not hide structural changes behind stylistic edits.

## Decision Gates

- If the page is informational, keep it static.
- If the page needs interaction, isolate the smallest interactive part.
- If the request can be solved with markup and existing components, stop there.
- If the request needs dynamic data, confirm the data source and the delivery path before adding code.
- If you cannot justify the client boundary in one sentence, the page is probably overbuilt.

## Validation

- The page builds with the rest of the site.
- The output remains compatible with the chosen hosting target.
- The markup stays accessible and responsive.
- Any added JavaScript is justified and scoped to the smallest possible surface.
- The rendered page still matches the existing visual system.
- Any dynamic boundary is explicit in the file, not implied by imports.

## Output

- Relevant Astro changes
- Files changed
- Static-vs-dynamic decision
- Validation performed
- Hosting or build implications, if any
