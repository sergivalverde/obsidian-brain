# Obsidian Brain

Claude Code skills that turn Claude into a thinking partner for your Obsidian vault.

**Core philosophy**: Help me think, don't think for me.

## Skills

| Command | Description |
|---------|-------------|
| `/catchup [project] [days]` | Summarize recent activity |
| `/thinking` | Activate thinking partner mode |
| `/newproject [name]` | Create a research project |
| `/progress [project]` | Create daily progress note |
| `/weekly-review` | Weekly review of all projects |

## Quick Start

### 1. Install MCP Server

You need the [mcp-obsidian-thinking](https://github.com/username/mcp-obsidian-thinking) MCP server for Obsidian connectivity.

```bash
git clone https://github.com/username/mcp-obsidian-thinking.git
cd mcp-obsidian-thinking
python3 -m venv .venv
.venv/bin/pip install -e .
```

### 2. Configure Obsidian

Install and enable the [Local REST API plugin](https://github.com/coddingtonbear/obsidian-local-rest-api).

### 3. Configure Claude Code

Add to `~/.claude/settings.json`:

```json
{
  "mcpServers": {
    "mcp-obsidian-thinking": {
      "command": "/path/to/mcp-obsidian-thinking/.venv/bin/python",
      "args": ["-m", "mcp_obsidian"],
      "env": {
        "OBSIDIAN_MODE": "api",
        "OBSIDIAN_API_KEY": "your-api-key",
        "OBSIDIAN_HOST": "127.0.0.1",
        "OBSIDIAN_PORT": "27124"
      }
    }
  }
}
```

### 4. Install Skills

Copy the `.claude/` folder to your project or `~/.claude/skills/` for global use:

```bash
# Project-level
cp -r .claude/ /path/to/your/project/

# Global
cp -r .claude/skills/* ~/.claude/skills/
```

## Usage

### Catch Up

```
/catchup "My Research" 3
```

Shows what changed in the last 3 days: files modified, themes, open questions.

### Thinking Mode

```
/thinking
```

Claude becomes a thinking partner:
- Asks clarifying questions
- Challenges assumptions
- Organizes your thoughts
- Does NOT write content unless asked

### New Project

```
/newproject "Market Analysis"
```

Creates:
```
Projects/Market Analysis/
├── index.md          # Thinking mode enabled
├── Chats/            # AI conversations
├── Research/         # Source materials
└── Daily Progress/   # Daily notes
```

### Daily Progress

```
/progress "Market Analysis"
```

Creates a dated note for learnings, insights, next steps.

### Weekly Review

```
/weekly-review
```

Reviews all projects: progress, stalled items, next week priorities.

## Thinking Mode

Control Claude's behavior with frontmatter:

```yaml
---
mode: thinking
---
```

When Claude reads a file with `mode: thinking`, it asks questions instead of generating content.

## Structure

```
.claude/
├── CLAUDE.md                    # Persona
└── skills/
    ├── catchup/SKILL.md
    ├── thinking/SKILL.md
    ├── newproject/SKILL.md
    ├── progress/SKILL.md
    ├── weekly-review/SKILL.md
    └── research-context/SKILL.md  # Auto-loads for context
```

## Credits

Inspired by Noah Brier's thinking partner workflow.

## License

MIT
