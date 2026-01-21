---
name: weekly-review
description: Conduct a weekly review of all active projects. Use at end of week to summarize progress and plan next week.
disable-model-invocation: true
---

# Weekly Review Workflow

Conduct a comprehensive weekly review of all active projects.

## Step 1: Gather All Recent Activity

Use Bash to find recently modified files in the vault's Projects folder:

```bash
find /Users/tensor/Documents/SV/Projects -type f -mtime -7 -name "*.md" -exec stat -f "%m %N" {} \; | sort -rn
```

This gives an overview of activity without loading full content yet.

## Step 2: Identify Active Projects

From the results, identify:
- Projects with activity this week
- Projects with no activity (may need attention or archiving)

## Step 3: Review Each Active Project

For each project with activity:

1. **Read the index.md** to understand current state
   ```
   Use Read tool: /Users/tensor/Documents/SV/Projects/<name>/index.md
   ```

2. **Read recent Daily Progress notes** to see trajectory
   ```
   Use Glob: /Users/tensor/Documents/SV/Projects/<name>/Daily Progress/*.md
   Then Read the most recent files from the past 7 days
   ```

3. **Summarize for this project**:
   - Files created/modified
   - Key learnings from progress notes
   - Questions that remain open
   - Current stage and momentum

## Step 4: Identify Cross-Project Patterns

Look across all projects for:
- **Common themes** emerging across projects
- **Connections** between different research threads
- **Projects needing attention** (stalled, blocked, or forgotten)
- **Projects ready to archive** (complete or abandoned)

## Step 5: Generate Review Summary

Present the review in this format:

---

## Weekly Review: [[YYYY-MM-DD]]

### Project Status

#### [[Project A]] - *Stage: exploration*
- **Activity**: 5 files modified, 2 created
- **Progress**: <summary of key progress>
- **Open questions**: <remaining questions>
- **Next actions**: <suggested next steps>

#### [[Project B]] - *Stage: synthesis*
- **Activity**: 2 files modified
- **Progress**: <summary>
- **Open questions**: <questions>
- **Next actions**: <actions>

### Inactive Projects
- [[Project C]] - No activity for 2 weeks. Archive or resume?
- [[Project D]] - Last active 10 days ago

### Wins This Week
- <accomplishments across all projects>

### Challenges
- <blockers or difficulties>

### Cross-Project Insights
- <patterns or connections noticed>

### Focus for Next Week
1. <priority 1>
2. <priority 2>
3. <priority 3>

---

## Step 6: Offer to Save

Ask the user:
> "Would you like me to save this as a weekly review note?
> It would go to: `Reviews/weekly_review_YYYY_MM_DD.md`"

If yes, use Write tool to create the review note at `/Users/tensor/Documents/SV/Reviews/weekly_review_YYYY_MM_DD.md`.

## Step 7: Offer Visualization

After presenting the text review, offer to create visual overview:

> "Would you like me to create a visual dashboard of your projects?
> I can use `/visualize` to create a canvas showing:
> - Projects arranged by status
> - Connections between related work
> - Visual overview of your research landscape"

If user agrees, invoke the visualize skill with "all projects" context.

## Step 8: Follow-up Questions

After presenting the review (and optional visualization), offer:
- "Would you like to dive deeper into any project?"
- "Should we archive any of the inactive projects?"
- "Want to set specific goals for next week?"
