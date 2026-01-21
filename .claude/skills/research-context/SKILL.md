---
name: research-context
description: Background knowledge about the user's Obsidian vault structure, research workflow, and organizational patterns. Auto-loads when discussing research, projects, or vault organization.
user-invocable: false
---

# Research Workflow Context

This skill provides background context about how the user organizes their Obsidian vault and conducts research.

## Vault Structure

The user's Obsidian vault follows this organization:

- `Projects/` - Active research and work projects
- `Resources/` - Reference materials and clippings
- `Areas/` - Ongoing responsibility areas (PARA method)
- `Archives/` - Completed or paused items

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
- The MCP server injects a warning banner
- Claude should NOT create content
- Claude should ask questions and help explore ideas
- Focus on understanding, not producing

## Date and Link Conventions

- **Dates**: Always use ISO format (YYYY-MM-DD)
- **Date links**: Often wrapped as wiki-links `[[2024-01-15]]` for daily note linking
- **Internal links**: Prefer wiki-links `[[note name]]` over markdown links
- **Project references**: Use wiki-links in frontmatter `project: [[Project Name]]`

## MCP Tools Available

The `mcp-obsidian-thinking` server provides these tools:

### File Operations
- `obsidian_list_files_in_vault` - List root directory
- `obsidian_list_files_in_dir` - List specific directory
- `obsidian_get_file_contents` - Read file (includes frontmatter instruction injection)
- `obsidian_batch_get_file_contents` - Read multiple files
- `obsidian_simple_search` - Text search
- `obsidian_complex_search` - Advanced search with filters
- `obsidian_put_content` - Write/overwrite file
- `obsidian_append_content` - Append to file
- `obsidian_patch_content` - Insert at position
- `obsidian_delete_file` - Delete file

### Metadata Operations
- `obsidian_frontmatter` - Read/update/delete frontmatter
- `obsidian_tags` - Query tags, find files by tag
- `obsidian_links` - Extract links from file
- `obsidian_attachments` - Get attachment info

### Progress Tracking
- `obsidian_get_recent_changes` - Recently modified files
- `obsidian_files_by_date` - Files from specific date range
- `obsidian_folder_progress` - Activity summary for folder
- `obsidian_get_periodic_note` - Get daily/weekly/monthly note
- `obsidian_get_recent_periodic_notes` - Recent periodic notes

### Project Management
- `obsidian_create_project` - Create project with template structure
- `obsidian_create_daily_progress` - Create daily progress note

## Working with Projects

When the user mentions a project:
1. First read the project's `index.md` to understand context
2. Check the frontmatter for mode and instructions
3. Review recent Daily Progress notes for current state
4. Look in Research/ for relevant materials
