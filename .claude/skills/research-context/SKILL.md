---
name: research-context
description: Background knowledge about the user's Obsidian vault structure, research workflow, and organizational patterns. Auto-loads when discussing research, projects, or vault organization.
user-invocable: false
---

# Research Workflow Context

This skill provides background context about how the user organizes their Obsidian vault and conducts research.

## Vault Structure

The user's Obsidian vault is located at `/Users/tensor/Documents/SV/` and follows this organization:

- `Projects/` - Active research and work projects
- `Resources/` - Reference materials and clippings
- `Areas/` - Ongoing responsibility areas (PARA method)
- `Archives/` - Completed or paused items
- `Reviews/` - Weekly and periodic reviews

## Project Structure

Each project in `Projects/` typically has:

```
Projects/<project-name>/
├── index.md              # Main project file with frontmatter instructions
├── Chats/                # AI conversation logs
├── Research/             # Source materials and notes
└── Daily Progress/       # Daily progress notes (daily_progress_YYYY_MM_DD.md)
```

## Frontmatter Conventions

Key frontmatter fields used in the vault:

| Field | Values | Purpose |
|-------|--------|---------|
| `mode` | `thinking`, `writing`, `review` | Behavioral mode for AI interaction |
| `status` | `active`, `paused`, `complete` | Project state |
| `stage` | `exploration`, `synthesis`, `writing`, `review` | Current project phase |
| `tags` | `[tag1, tag2]` | Organization tags |
| `instructions` | Free text | Custom instructions for AI |
| `ai_instructions` | Free text | Alternative field for AI instructions |

## Thinking Mode Behavior

When files have `mode: thinking` in frontmatter:
- Claude should NOT create content
- Claude should ask questions and help explore ideas
- Focus on understanding, not producing
- Use the `/thinking` skill explicitly if needed

## Date and Link Conventions

- **Dates**: Always use ISO format (YYYY-MM-DD)
- **Date links**: Often wrapped as wiki-links `[[2024-01-15]]` for daily note linking
- **Internal links**: Prefer wiki-links `[[note name]]` over markdown links
- **Project references**: Use wiki-links in frontmatter `project: [[Project Name]]`

## File Tools Available

Claude Code provides direct file access:

### File Operations
- **Read** - Read file contents
- **Write** - Create or overwrite files
- **Edit** - Make targeted edits to existing files
- **Glob** - Find files by pattern (e.g., `vault/Projects/*/index.md`)
- **Grep** - Search content across files (supports regex, tags, etc.)
- **Bash** - Run commands for file listings, git operations, etc.

### Common Patterns

**Find recent files:**
```bash
find /Users/tensor/Documents/SV/Projects -type f -mtime -7 -name "*.md"
```

**Search for tags:**
```bash
grep -r "#tag-name" /Users/tensor/Documents/SV/Projects
```

**List project directories:**
```bash
ls -d /Users/tensor/Documents/SV/Projects/*/
```

## Working with Projects

When the user mentions a project:
1. First read the project's `index.md` to understand context
2. Check the frontmatter for mode and instructions
3. Review recent Daily Progress notes for current state
4. Look in Research/ for relevant materials
