# Astro Page Patterns

Use these patterns as the default reference when editing Astro pages in this repository.

## 1. Static Landing Page

Use this for pages whose primary job is to inform, persuade, or route the user elsewhere.

```astro
---
const highlights = [
  'Fast static output',
  'Simple shared-hosting deployment',
  'Easy maintenance',
];
---

<main class="page-shell">
  <section class="hero">
    <p class="eyebrow">Astro static site</p>
    <h1>Make the page obvious in one glance.</h1>
    <p>Static content should communicate the purpose before the user scrolls.</p>
  </section>

  <section aria-label="Highlights">
    <ul>
      {highlights.map((item) => <li>{item}</li>)}
    </ul>
  </section>
</main>
```

Use this when:

- The page is mostly content.
- The page has no real client-side state.
- The build should remain predictable and simple.

## 2. Content Page With Metadata

Use this for documentation, long-form content, changelogs, or detail pages.

```astro
---
const meta = {
  title: 'Project overview',
  updated: '2026-03-27',
  category: 'Blueprint',
};
---

<article class="content-page">
  <header>
    <p>{meta.category}</p>
    <h1>{meta.title}</h1>
    <p>Last updated {meta.updated}</p>
  </header>

  <slot />
</article>
```

Use this when:

- The page is mostly prose.
- The page needs a few stable metadata fields.
- Slots can carry the actual body content.

## 3. Static Shell Plus Island

Use this when one part of the page genuinely needs browser behavior.

```astro
---
import SearchPanel from '../components/SearchPanel.tsx';
---

<main>
  <header>
    <h1>Browse entries</h1>
    <p>Keep the shell static and isolate the only interactive part.</p>
  </header>

  <SearchPanel client:visible />
</main>
```

Use this when:

- The page needs filtering, toggles, or live input.
- The page still makes sense without JS.
- The interactive feature is small enough to isolate cleanly.

## 4. Good vs Bad Boundaries

### Good

- Static header and content.
- One focused client island.
- Clear reason for interaction.

### Bad

- Page-wide client state for a simple content page.
- Hidden interactivity that makes the page harder to deploy.
- Rewriting the layout when a slot or component change would do.

## 5. What To Check Before Editing

- Is the page truly interactive, or just content with a nice presentation?
- Can the problem be solved by markup and data instead of state?
- Is there already an existing page pattern to follow?
- Does the change affect routing, metadata, or the shell structure?
- Will the page still be simple to host after the change?

## 6. Validation Checklist

- Page builds successfully.
- Layout remains responsive.
- Accessibility still makes sense in the DOM structure.
- No new client code was added without a clear reason.
- The final file still matches the repo's existing page language.
