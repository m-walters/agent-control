---
name: Keeping docs up to date
description: Notes on policy for updating docs when making implementations and changes
applyTo: '**'
paths: ["*"]
---

## Dependency

Read [writing-docs.instructions.md](./writing-docs.instructions.md) for info on Agent Docs and User Docs.

## When, and when not to, update docs

Updating docs takes a bit of nuance to keep them up to date while preventing bloat.

**Large updates**

- If you sense a large update to docs is needed, confirm this with the user with where you would like to act.

**Positive signals for doc updates**

- Whenever creating a new feature wholecloth, this usually triggers an update to Agent Docs and User Docs.
- Refactoring often triggers a doc update, both for file paths but also object/class names.

**Negative signals for doc updates**

- Minor changes, like adding a new function method, or a bug fix, rarely require doc updates.
- Functionality that is "deep under the hood" is usually irrelevant for documentation purposes.
    - Unless it effects dev operations

**Ambiguous signals**

- If you're unsure, list Agent doc files and user docs for clues on areas that may need touching up.
- If you're still unsure, simply ask the user.
