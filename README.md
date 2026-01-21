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

## Installation

Copy the `.claude/` folder to your Obsidian vault:

```bash
cd /path/to/your/obsidian-vault
git clone https://github.com/YOUR_USERNAME/obsidian-brain.git .obsidian-brain
cp -r .obsidian-brain/.claude .
rm -rf .obsidian-brain
```

Or manually:
1. Download this repo
2. Copy the `.claude/` folder to the root of your Obsidian vault
3. Open your vault in Claude Code

That's it! The skills will be available in any Claude Code session in that vault.

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
your-obsidian-vault/
├── .claude/
│   ├── CLAUDE.md                    # Thinking partner persona
│   └── skills/
│       ├── catchup/SKILL.md
│       ├── thinking/SKILL.md
│       ├── newproject/SKILL.md
│       ├── progress/SKILL.md
│       ├── weekly-review/SKILL.md
│       └── research-context/SKILL.md
├── Projects/                        # Your research projects
├── Research/                        # Reference materials
└── ... your other vault files
```

## Credits

Inspired by Noah Brier's thinking partner workflow.

## License

MIT
