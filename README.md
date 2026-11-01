# agent-control

Resources to make your agent less stupid.

Although I try in some places to guide on usage with Claude, I'm building this with
VSCode's default GitHub Copilot.

### Forcing Load

If you would like any of the instructions provided here to be loaded on any agent operation,
set `applyTo: **` within the frontmatter of them.

From what I understand, this is not literally on every request, but would be pulled in when
it wants to edit a file.

For global always-on instructions, see "Always-on Instructions" below.

Also, you can add [instructions/copilot-instructions.md](./instructions/copilot-instructions.md) to your global instructions file.

## Creating Instructions

In VSCode, run **Chat: Open Customizations** from the Command Palette to check whether your instructions or skills are discovered.
To test use, start a fresh chat with a matching task and check the response's **References** for instructions, or invoke a skill from the `/` menu.

### Filename

Name Copilot's modular files `*.instructions.md`. Claude rules can use ordinary
`*.md` filenames.

### Frontmatter

For Copilot, you can optionally supply frontmatter:

```yaml
---
name: ...
description: ...
applyTo: "**/*.py"
---
```

`applyTo` automatically attaches instructions when matching files are changed.
`description` helps the agent discover instructions relevant to a task. If you
omit both, attach the file manually.

For Claude rules, use `paths` instead of `applyTo`:

```yaml
---
paths:
  - "**/*.py"
---
```

### Locations

These locations hold modular instructions for GitHub's Copilot or Claude.

A Workspace scope applies to the project you're working on, and is thus relative to the project's root.

Use the User scope to apply controls to all your projects using that harness.

| Session and scope | Default file location |
|-------------------|-----------------------|
| Copilot workspace | `.github/instructions/` |
| Claude workspace | `.claude/rules/` |
| Copilot user | `~/.copilot/instructions/` |
| Claude user | `~/.claude/rules/` |

#### Always-on Instructions

Use these files for guidance that applies throughout a session, rather than
instructions selected by file patterns or task relevance.

See the [VS Code custom instructions documentation](https://code.visualstudio.com/docs/agent-customization/custom-instructions)
and [Claude Code instructions documentation](https://code.claude.com/docs/en/memory).

| Description | File location |
|-------------|---------------|
| Copilot user-level instructions that apply across repositories. | `~/.copilot/copilot-instructions.md` |
| Copilot repository-wide instructions. | `.github/copilot-instructions.md` |
| Claude user-level instructions that apply across repositories. | `~/.claude/CLAUDE.md` |
| Claude repository-wide instructions. | `CLAUDE.md` or `.claude/CLAUDE.md` |

## Creating Skills

Skills describe task-specific workflows that the agent can load when relevant.
Unlike instructions, a skill can also include scripts, examples, and other
supporting files.

### Filename

Give each skill its own directory containing a file named `SKILL.md`. For
example, `.github/skills/test-changes/SKILL.md`:

```markdown
---
name: test-changes
description: Run relevant project tests when validating a code change and report the results.
---

# Test changes

1. Find the tests relevant to the change.
2. Run them using the project's documented test commands.
3. Report what passed, failed, or could not be run.
```

In VS Code, `name` and `description` are required. The name must match the
directory name and use only lowercase letters, numbers, and hyphens. The
description should say both what the skill does and when to use it.

### Locations

As with instructions, workspace skills belong to a project, while user skills
are available across projects.

| Session and scope | Default file location |
|-------------------|-----------------------|
| Copilot workspace | `.github/skills/<skill-name>/SKILL.md` |
| Claude workspace | `.claude/skills/<skill-name>/SKILL.md` |
| Copilot user | `~/.copilot/skills/<skill-name>/SKILL.md` |
| Claude user | `~/.claude/skills/<skill-name>/SKILL.md` |

VS Code's Local sessions also search `.claude/skills/` and `.agents/skills/`
in the workspace, and `~/.claude/skills/` and `~/.agents/skills/` for user
skills. Supported locations can differ between harnesses.

### Using skills

By default, Copilot may select a discovered skill based on its description, or
you can invoke it directly in chat, for example with `/test-changes`. Discovery
does not guarantee automatic selection. Start a fresh chat to test both direct
invocation and whether the skill is selected for a relevant request.

Claude Code can use the directory name when `name` is omitted, but include it
for VS Code compatibility. Claude Code also supports older command files in
`.claude/commands/`; new skills should use the skill directories above.

See the [VS Code agent skills documentation](https://code.visualstudio.com/docs/agent-customization/agent-skills)
and [Claude Code skills documentation](https://code.claude.com/docs/en/skills).
