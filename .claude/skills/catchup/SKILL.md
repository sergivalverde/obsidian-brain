---
name: catchup
description: Summarize recent changes to a project or folder. Use when user asks "what changed", "catch me up", "what's new", "recent activity", or "what did I work on".
argument-hint: [project-name] [days-back]
---

# Catch Up Workflow

Help the user get caught up on recent activity in their Obsidian vault.

## Arguments

- `$ARGUMENTS[0]` - Project or folder name (optional)
- `$ARGUMENTS[1]` - Number of days to look back (optional, default: 3)

## Step 1: Determine Scope

If no project specified in arguments:
- Ask: "Which project or folder would you like to catch up on? Or should I show activity across the whole vault?"

If project specified:
- Use `Projects/<project-name>` as the folder path

## Step 2: Gather Recent Changes

Use Bash to find recently modified files:

```bash
# For a specific project
find /Users/tensor/Documents/SV/Projects/<project-name> -type f -mtime -<days> -name "*.md"

# For the whole vault
find /Users/tensor/Documents/SV -type f -mtime -<days> -name "*.md"
```

Then use Read tool to read the content of changed files.

## Step 3: Analyze Changes

For each changed file:
1. Identify the type of change (new note, daily progress, chat log, research)
2. Extract key themes or insights
3. Note any questions or open items mentioned
4. Track the progression of ideas across days

## Step 4: Present Summary

Structure your response as:

### Overview
One sentence on activity level (e.g., "Moderate activity over the past 3 days with focus on X")

### Key Changes
- Bullet points of significant updates
- Link to relevant files using `[[filename]]` format

### Themes Emerging
- Patterns you notice across the files
- Connections between ideas

### Open Questions
- Items marked as questions or needing follow-up
- Unresolved threads

### Suggested Next Steps
- Based on the trajectory of work
- What seems like the natural next action

## Example Output

> **Overview**: Active research over the past 3 days, primarily exploring market sizing approaches.
>
> **Key Changes**:
> - Created [[Market Analysis Framework]] with initial structure
> - Added 5 research notes to Research/ folder
> - Daily progress notes show iteration on key questions
>
> **Themes Emerging**:
> - Tension between top-down and bottom-up approaches
> - Need for better competitive data
>
> **Open Questions**:
> - "How do we validate the TAM assumption?" (from daily progress 01-18)
> - Market segmentation criteria still undefined
>
> **Suggested Next Steps**:
> - Address the TAM validation question
> - Consider creating a dedicated note for competitive analysis
