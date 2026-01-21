# Obsidian Brain

Claude Code skills that turn Claude into a thinking partner for your Obsidian vault.

**Core philosophy**: Help me think, don't think for me.

## Skills

### Thinking Workflows
| Command | Description |
|---------|-------------|
| `/thinking` | Activate thinking partner mode - questions over answers |
| `/catchup [project] [days]` | Summarize recent activity in a project |
| `/newproject [name]` | Create a new research project with structure |
| `/progress [project]` | Create or update daily progress note |
| `/weekly-review` | Conduct weekly review of all projects |

### Content Creation
| Command | Description |
|---------|-------------|
| `/format [note]` | Format notes with proper Obsidian syntax (callouts, wikilinks, frontmatter) |
| `/visualize [what]` | Create canvas visualizations - mind maps, project dashboards, research networks |

### File Format Skills (from [obsidian-skills](https://github.com/kepano/obsidian-skills))
| Skill | What It Does |
|-------|--------------|
| `obsidian-markdown` | Create properly formatted Obsidian notes with all syntax features |
| `obsidian-bases` | Create database views with filters, formulas, and aggregations |
| `json-canvas` | Create visual canvas files for mind mapping and spatial organization |

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

Creates a dated note for learnings, insights, next steps. Offers formatting enhancement.

### Weekly Review

```
/weekly-review
```

Reviews all projects: progress, stalled items, next week priorities. Offers visual dashboard creation.

### Format Notes

```
/format "My Rough Note"
```

Transforms rough notes into properly formatted Obsidian notes with callouts, wikilinks, tags, and rich frontmatter. Perfect after thinking mode when you're ready to create polished content.

### Visualize Research

```
/visualize "Market Analysis"
```

Creates canvas visualizations:
- Mind maps after brainstorming
- Project dashboards from `/weekly-review`
- Research networks showing connections

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
│   ├── CLAUDE.md                      # Thinking partner persona
│   └── skills/
│       ├── Thinking workflows:
│       │   ├── catchup/SKILL.md
│       │   ├── thinking/SKILL.md
│       │   ├── newproject/SKILL.md
│       │   ├── progress/SKILL.md
│       │   ├── weekly-review/SKILL.md
│       │   └── research-context/SKILL.md
│       ├── Content creation:
│       │   ├── format/SKILL.md
│       │   └── visualize/SKILL.md
│       └── File formats (from obsidian-skills):
│           ├── obsidian-markdown/SKILL.md
│           ├── obsidian-bases/SKILL.md
│           └── json-canvas/SKILL.md
├── Projects/                          # Your research projects
├── Research/                          # Reference materials
└── ... your other vault files
```

## How It Works Together

**Thinking → Creating Pipeline:**

1. `/thinking` - Explore ideas without jumping to solutions
2. Work through questions, gather materials, organize thoughts
3. `/format` - Transform exploration into polished Obsidian notes
4. `/visualize` - Create visual maps of connections and themes

**Project Management Flow:**

1. `/newproject` - Set up research project structure
2. Daily work sessions with thinking mode
3. `/progress` - Document daily learnings (with formatting)
4. `/weekly-review` - Synthesize across projects (with visualization)
5. `/catchup` - Resume work by reviewing recent changes

## Credits

- Thinking partner workflow inspired by [Noah Brier](https://www.aisupremacy.com/p/my-obsidian-ai-thinking-partner)
- File format skills from [Kepano's obsidian-skills](https://github.com/kepano/obsidian-skills)

## License

MIT
