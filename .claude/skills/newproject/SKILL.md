---
name: newproject
description: Create a new research project in Obsidian with standard structure. Use when user wants to start a new project, research topic, or organized workspace.
argument-hint: [project-name]
disable-model-invocation: true
---

# Create New Project Workflow

Help the user create a new research project with proper structure in their Obsidian vault.

## Arguments

- `$ARGUMENTS` - Project name (optional, will prompt if not provided)

## Step 1: Get Project Details

If `$ARGUMENTS` is empty, ask:
- "What would you like to name this project?"
- "Can you give me a brief description of what you're exploring?"

If project name provided, confirm and ask for description:
- "Creating project: **<name>**. What's the main goal or question you're exploring?"

## Step 2: Create Project Structure

Use the MCP `obsidian_create_project` tool:

```json
{
  "base_path": "<project-name>",
  "template": "research_project"
}
```

This creates:
- `Projects/<name>/index.md` - Main file with thinking mode frontmatter
- `Projects/<name>/Chats/` - For AI conversation logs
- `Projects/<name>/Research/` - For source materials
- `Projects/<name>/Daily Progress/` - For daily notes

## Step 3: Customize the Index

After creation, read the index.md and offer to customize:

1. **Key Questions**: "What are the main questions you want to explore?"
2. **Tags**: "What tags should we use for organization? (e.g., #research, #work, #personal)"
3. **Success Criteria**: "How will you know when this project is complete?"

Update the frontmatter with any additions using `obsidian_frontmatter`:
```json
{
  "filepath": "Projects/<name>/index.md",
  "operation": "update",
  "frontmatter": {
    "tags": ["tag1", "tag2"],
    "key_questions": ["Question 1?", "Question 2?"]
  }
}
```

## Step 4: Confirm and Suggest Next Steps

Summarize what was created:

> **Project Created: [[<project-name>]]**
>
> Structure:
> - `index.md` - Your main project file (thinking mode enabled)
> - `Chats/` - Save our conversations here
> - `Research/` - Store articles and source materials
> - `Daily Progress/` - Track daily learnings
>
> **Next Steps:**
> 1. Add your initial thoughts to the index
> 2. Start collecting relevant materials in Research/
> 3. When you're ready to work on this, just open the project and I'll be in thinking mode

## Template: index.md Content

The created index.md should have this structure:

```markdown
---
mode: thinking
status: active
stage: exploration
created: <today's date>
tags: []
---

# <Project Name>

## Overview
<Brief description from user>

## Key Questions
-

## Current Thinking


## Resources
-

## Open Threads

```
