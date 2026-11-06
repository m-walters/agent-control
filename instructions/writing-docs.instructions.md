---
name: "Writing Docs"
description: "Instructions and practices for how you should be writing docs"
applyTo: '**'
paths: ["*"]
---

## Two Archetypes

Within a project, in general there are two archetypes of docs you will create:

1. **Agent Instructive Docs**: Documentation that are as verbose as needed to provide the agent with the context it needs
2. **User/Dev Docs**: Documentation intended for human consumption. Shorter, *significantly less verbose*.

These docs have different rules for where they should be placed.

### Doc Locations

Use this standard when deciding where to write docs

| Location | Description | Example |
|---|---|---|
| `docs/` (User default) | General place for docs. May contain `agent/` subdir though. | `docs/module1.md` |
| `.agent/docs/` (Agent default) | Default location for docs on project topics | `.agent/docs/running-tests.md` |
| `docs/agent/` | Alternative to `.agent/docs/`. Up to user preference. | `docs/agent/running-tests.md` |
| `src/module/docs/` | Special, helpful information pertaining to a scoped area. Should be human-friendly. | `src/api/docs/usage.md` |
| `src/module/docs/agent/` | If an exception is deserved, you can write a nested Agent Doc within. | `src/api/docs/agent/writing-views.md` |

As stated, `.agent/docs/` or `docs/agent/` are the go-to places for agent docs, but short scoped docs may be placed deeper in code, at your discretion. However, such nested docs should be human-friendly.

*First check if `.agent/docs` or `docs/agent/` exists, and then stick to that one.*

### Agent Instructive Docs

Agent docs are allowed to be as verbose as necessary for the agent to better understand ins and outs of the repository

### User/Dev Docs**:

Agent docs are often way too verbose and laborious for human consumption.

## Deciding which to write

### Ask the user first

If it seems like documentation would be desirable, be transparent with the user:

- Tell the user "I would like to write some \[Agent|User\] documentation for this"
- Include in your request the proposed file paths: `docs/<some_user_doc>.doc` and/or `.agent/docs/<agent_doc>.md`. 

### Writing both Agent and User docs at once

In your flow, it is often desirable---though certainly not mandatory---to write both an Agent and a User doc for something.

- First, notify the user of your intention, with proposed file paths.
- Write the agent doc first, and then generate a succinct, user-friendly version in the approriate locations.

Consider when a 1-to-1 is not desirable:

#### Agent doc sans User doc

Often it's helpful for the agent to remember/track information that is inappropriate or too in-the-weeds for human consumption. This is perfectly fine, but notify the user.

#### User doc sans Agent doc

This may typically arise in two situations:

1. The user has requested you write some docs.
2. A doc is straightforward enough that there needn't be also an agent version.

If the user has requested docs, consider if a complimentary Agent doc would make sense, and notify the user of your intention with the file path.

### Deeper, nested src docs

For nested src docs, *these should most often be considered like human-friendly User docs*.
Keep them succinct.

If you feel like an Agent Doc is application, nest it directly as `docs/agent/` subdir.

- Example: `src/api/docs/agent/writing-views.md`
