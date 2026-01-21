---
name: progress
description: Create or update daily progress note for a project. Use when user wants to document learnings, wrap up a session, or track daily progress.
argument-hint: [project-name]
disable-model-invocation: true
---

# Daily Progress Workflow

Help the user create or update a daily progress note for their project.

## Arguments

- `$ARGUMENTS` - Project name (optional, will prompt if not provided)

## Step 1: Identify Project

If `$ARGUMENTS` is empty:
1. Use `obsidian_folder_progress` on `Projects/` with `days_back: 7` to find recent activity
2. Show the user their recent projects and ask which one to create progress for

Example prompt:
> "Which project would you like to create a progress note for?
> - [[Project A]] (last active: today)
> - [[Project B]] (last active: 2 days ago)
> - [[Project C]] (last active: 5 days ago)"

## Step 2: Check for Existing Note

Before creating, check if today's note already exists:
- Expected path: `Projects/<name>/Daily Progress/daily_progress_YYYY_MM_DD.md`

If exists, ask:
> "There's already a progress note for today. Would you like me to:
> 1. Add to the existing note
> 2. Read what's there first
> 3. Start fresh (replace)"

## Step 3: Create Progress Note

Use the MCP `obsidian_create_daily_progress` tool:

```json
{
  "project_path": "Projects/<project-name>",
  "date": "<today in YYYY-MM-DD format>"
}
```

## Step 4: Populate from Session

If you have context from the current conversation, offer to populate the note:

> "Based on our conversation today, I can add:
> - **What I Learned**: <summary of insights>
> - **Key Decisions**: <any decisions made>
> - **Questions That Emerged**: <new questions>
>
> Would you like me to add these to the progress note?"

If user agrees, use `obsidian_append_content` to add the sections.

## Step 5: Format (Optional)

After creating the progress note, offer to enhance formatting:

> "Would you like me to format this progress note with:
> - Callouts for key insights
> - Proper wikilinks to related notes
> - Tags for discovery
>
> I can use `/format` to enhance the formatting."

If user agrees, invoke the format skill to apply rich Obsidian syntax.

## Step 6: Review Together

Read back the created/updated note and ask:
> "Here's today's progress note. Anything you'd like to add or change?"

## Progress Note Template

```markdown
---
date: [[YYYY-MM-DD]]
project: [[Project Name]]
---

# Daily Progress - YYYY-MM-DD

## What I Worked On
-

## What I Learned Today
-

## Key Insights
-

## Questions That Emerged
-

## Tomorrow's Focus
-
```

## Tips for Good Progress Notes

When helping populate:
- Focus on insights, not just activities
- Capture questions that came up
- Note any shifts in thinking
- Link to relevant notes created today using `[[note name]]`
- Keep entries concise but meaningful
