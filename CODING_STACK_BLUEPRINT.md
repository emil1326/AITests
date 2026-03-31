# Coding Stack Blueprint

## Goal

Keep the site cheap, simple, and compatible with shared hosting.

The chosen stack is:

- Frontend: Astro static site
- Backend: plain PHP endpoints
- Database: MySQL or MariaDB
- Hosting: shared hosting

That gives you a clean split:

- Astro handles the UI and static pages
- The browser calls PHP endpoints with `fetch` or forms
- PHP talks to MySQL if the site needs storage
- No JVM or VPS is required for the first version

## Why this stack fits

- It matches the hosting plan you are actually considering.
- It avoids depending on Node or JVM support on the server.
- It keeps the frontend and backend responsibilities separate.
- It leaves room to add persistence only when you need it.

## Project Layout

This is the layout to use later if we build the project in this direction:

- `src/` for Astro pages and components
- `public/` for static assets
- `api/` or `backend/` for PHP endpoints
- `db/` for schema and seed SQL
- `scripts/` for deployment helpers or small utilities

## Deployment Model

1. Build the Astro site locally.
2. Upload the generated static output.
3. Upload the PHP backend files.
4. Point the frontend at the PHP endpoints.
5. Add MySQL only when the site actually needs stored data.

## Notes For Shared Hosting

- PHP and MySQL are the safe default for shared hosting.
- Static frontend files are a good fit.
- Node.js support is not required for this stack.
- JVM hosting is not part of this plan.

## What To Avoid For Now

- Do not add Laravel unless the project becomes clearly PHP-framework-heavy.
- Do not add JVM hosting unless you have a host that explicitly supports it.
- Do not add a database unless you already know what data needs to persist.