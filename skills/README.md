# Claude Skills

Shared source for my Claude Code skills, so they can be installed on every PC/Mac.

| Skill | Purpose |
|---|---|
| [task-orchestrator](task-orchestrator/SKILL.md) | Splits development work across Opus / Sonnet / Haiku and runs Haiku subagents in parallel |
| [dig](dig/SKILL.md) | Interviews me one question at a time about a plan or design until we share an understanding (based on [ryonakae/dotfiles](https://github.com/ryonakae/dotfiles/tree/master/config/.agents/skills/dig), with extra trigger phrases) |
| [grill-me](grill-me/SKILL.md) | Alias of `dig`; also triggered by phrases like "ask me if anything is unclear" |

## Install (user level, all projects)

```bash
git clone https://github.com/youaoi/information.git
mkdir -p ~/.claude/skills
cp -R information/skills/task-orchestrator information/skills/dig information/skills/grill-me ~/.claude/skills/
```

On Windows PowerShell:

```powershell
git clone https://github.com/youaoi/information.git
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
foreach ($s in "task-orchestrator","dig","grill-me") { Copy-Item -Recurse -Force "information\skills\$s" "$HOME\.claude\skills\" }
```

Update later with `git pull` and copy again. Restart Claude Code to pick up changes.
