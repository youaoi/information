# Claude Skills

Shared source for my Claude Code skills, so they can be installed on every PC/Mac.

| Skill | Purpose |
|---|---|
| [task-orchestrator](task-orchestrator/SKILL.md) | Splits development work across Opus / Sonnet / Haiku and runs Haiku subagents in parallel |

## Install (user level, all projects)

```bash
git clone https://github.com/youaoi/information.git
mkdir -p ~/.claude/skills
cp -R information/skills/task-orchestrator ~/.claude/skills/
```

On Windows PowerShell:

```powershell
git clone https://github.com/youaoi/information.git
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse -Force information\skills\task-orchestrator "$HOME\.claude\skills\"
```

Update later with `git pull` and copy again. Restart Claude Code to pick up changes.
