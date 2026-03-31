---
name: release
description: "Prepare release notes, risk notes, and rollout guidance for a completed change."
argument-hint: "the changes to summarize for release"
---

# Release Notes

Prepare a concise release summary for the completed change.

## Mission

- Tell a human reader what changed, why it matters, and what to watch after release.

## Inputs

- The completed change or final diff.
- Any validation results, migrations, or docs that matter to release readers.
- The deployment or hosting model if it changes rollout risk.

## Before You Start

- Read AGENTS.md, the relevant instructions, and the shared lessons file.
- Review the final diff or the set of completed files.
- Check whether docs, migrations, or workflow files should be mentioned in the release notes.

## Release Rules

- Summarize what changed, not the whole implementation history.
- Call out user-visible behavior changes.
- Mention validation that was actually performed.
- Note risks, compatibility concerns, and rollback considerations.
- Keep the summary concise and useful for a human reader.
- If the change affects shared hosting or deployment, say so plainly.

## Release Shape

- Summary of changes.
- User-visible impact.
- Validation performed.
- Risks or follow-up items.
- Rollback notes if relevant.

## Validation

- The release note reflects what was actually delivered.
- User-facing changes are called out clearly.
- Operational risk is stated without exaggeration.
- Any rollout concerns are easy to spot.
