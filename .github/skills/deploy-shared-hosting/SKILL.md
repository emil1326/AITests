---
name: deploy-shared-hosting
description: Deploy Astro and PHP projects to shared hosting with a simple build-and-upload flow.
---

# Shared Hosting Deployment Skill

Use this skill when the task involves building or deploying the site to shared hosting.

## When to Use This Skill

- The frontend is Astro static output.
- The backend includes plain PHP endpoints.
- The host is shared hosting rather than a VPS or container platform.
- You need a simple build, upload, and verify flow that does not assume server-side control.

## Before You Start

- Read the global instructions.
- Read the shared lessons file.
- Check the chosen hosting plan.
- Confirm whether the site is static only or includes PHP files.

## What This Skill Is For

- Shipping static Astro output to shared hosting.
- Uploading PHP endpoints alongside a static frontend.
- Verifying which files belong in the public web root.
- Catching path, rewrite, and host-assumption mistakes before deployment.

## Deployment Map

- Static build output goes to the public web root or the configured subdirectory.
- PHP endpoints go in the same public location as the frontend if the frontend calls them directly.
- Source-only files, notes, and internal tooling stay off the public host.
- Any path that is not part of runtime delivery stays local.

## Controlled Flow

1. Identify the host document root and the public URL path.
2. Split the site into static assets, PHP files, and private files.
3. Build the frontend locally.
4. Upload only the files that belong in the public web root.
5. Verify PHP endpoints with a direct request, not just by assuming the upload worked.
6. Confirm the built site still resolves its internal links and assets.

## Hard Limits

- Do not assume a Node runtime on shared hosting unless the plan explicitly supports it.
- Do not upload source-only files that are not meant to be publicly served.
- Do not rely on local dev-only paths or absolute filesystem paths.
- Do not treat the host as if it were a full VPS.

## Common Hosting Shapes

### Static Astro Site

- Build locally.
- Upload only the generated static output.
- Confirm the host serves the landing page and all linked routes.
- Check that asset paths still resolve after deployment.

### Astro Plus PHP Endpoint

- Keep the frontend static.
- Upload the PHP endpoint into the correct public location.
- Confirm the frontend calls the endpoint with the expected relative URL.
- Test the endpoint with a real request and confirm the response shape.

### Site in a Subdirectory

- Confirm the base path before upload.
- Check that links, scripts, and assets respect the subdirectory.
- Verify that the build output does not hardcode the root domain.

## Validation

- The built site opens from the deployed URL.
- Static assets load without 404s.
- PHP endpoints return the expected status and body.
- The public path matches the host configuration.
- No hidden runtime dependency remains in the deployment plan.

## Common Failure Modes

- Uploading the source tree instead of the build output.
- Forgetting that PHP files need to sit in the public web root.
- Hardcoding local development URLs in production files.
- Assuming server behavior that the shared host does not support.
- Missing rewrite or routing expectations for the deployed path.

## Output Contract

- Deployment map: what goes to the web root, what stays local, what must not be uploaded.
- Step-by-step deployment order.
- Validation performed.
- Host limitations to watch for.
- File and line references when possible.
