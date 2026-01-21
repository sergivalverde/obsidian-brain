---
name: format
description: Format notes with proper Obsidian syntax after thinking/drafting. Use when transitioning from exploration to writing, or when user says "format this" or "make this a proper note".
argument-hint: [note-path]
disable-model-invocation: false
---

# Format Note Workflow

Transform rough notes or thinking output into properly formatted Obsidian notes with rich syntax.

## When to Use

After thinking mode exploration, when the user is ready to create polished content:
- "Format this as a proper note"
- "Add proper formatting"
- "Make this look nice in Obsidian"
- Transitioning from `/thinking` to final output

## Arguments

- `$ARGUMENTS` - Optional path to existing note to format (otherwise formats current context)

## Step 1: Understand Content

If formatting existing note:
- Read the note using standard file reading
- Identify key sections, concepts, and relationships

If formatting from conversation:
- Review what was discussed in thinking mode
- Identify main ideas, questions, insights

## Step 2: Apply Obsidian Formatting

Use the `obsidian-markdown` skill to create properly formatted content with:

### Structural Elements
- **Frontmatter**: Add relevant properties (tags, status, created date, related notes)
- **Headings**: Create clear hierarchy
- **Lists**: Use proper bullet/number formatting

### Obsidian-Specific Features
- **Wikilinks**: Convert mentions to `[[note name]]` format
- **Tags**: Add inline tags like #concept or #research
- **Callouts**: Use for important notes
  - `> [!note]` for general information
  - `> [!question]` for open questions
  - `> [!insight]` for key insights
  - `> [!warning]` for important caveats

### Rich Content
- **Embeds**: Embed relevant files with `![[file]]`
- **Block references**: Use `[[file#^blockid]]` for specific sections
- **Task lists**: Use `- [ ]` for actionable items

## Step 3: Enhance with Metadata

Add frontmatter that makes the note discoverable:

```yaml
---
created: [[YYYY-MM-DD]]
tags: [topic1, topic2]
status: draft|active|complete
related: [[note1]], [[note2]]
---
```

## Step 4: Preview and Confirm

Show the formatted version and ask:
> "Here's the formatted note. Would you like me to:
> 1. Save it to a new file
> 2. Update the existing file
> 3. Make adjustments"

## Example Transformation

**Before (rough thinking output):**
```
thinking about market sizing approaches
- top down: total addressable market
- bottom up: unit economics
need to validate assumptions
see article about TAM calculation
```

**After (formatted):**
```yaml
---
created: [[2026-01-21]]
tags: [market-sizing, strategy]
status: active
related: [[Business Models]], [[Unit Economics]]
---

# Market Sizing Approaches

## Overview
Exploring two complementary approaches to market sizing.

## Approaches

### Top-Down Analysis
Start with Total Addressable Market (TAM)
- Industry reports
- Market research data
- See: [[TAM Calculation Methods]]

### Bottom-Up Analysis
Build from unit economics
- Customer segments
- Pricing models
- Conversion rates

> [!question] Key Validation Needed
> How do we validate our TAM assumptions?

## Resources
- ![[Article - TAM Calculation]]
```

## Tips for Good Formatting

- Use callouts sparingly (only for emphasis)
- Link to existing notes when relevant
- Add tags that help with future discovery
- Include created date for chronological tracking
- Use task lists for actionable follow-ups
