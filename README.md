# agent-control

Resources to make your agent less stupid.


## Instruction locations based on harness

Some locations to note whether you are using GitHub's Copilot (the VSCode default) or Claude.

A Workspace scope applies to the project your working on, and is thus relative to the project's root.

Use the User scope to apply controls to all your projects using that harness

| Session and scope | Default file location |
|-------------------|-----------------------|
| Copilot workspace | `.github/instructions` |
| Claude workspace | `.claude/rules` |
| Copilot user | `~/.copilot/instructions` |
| Claude user | `~/.claude/rules` |
