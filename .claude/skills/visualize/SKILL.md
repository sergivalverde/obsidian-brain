---
name: visualize
description: Create visual canvas maps of research, projects, or ideas. Use when user wants to see connections, create mind maps, or visualize project structure. Great after /catchup or /weekly-review.
argument-hint: [what-to-visualize]
disable-model-invocation: false
---

# Visualize Research Workflow

Create visual canvas maps to see connections, themes, and project structures spatially.

## When to Use

- After `/catchup` - "Show me connections in this project"
- After `/weekly-review` - "Visualize my project landscape"
- When exploring relationships - "Map out these ideas"
- For project overviews - "Create a research map"
- Mind mapping sessions

## Arguments

- `$ARGUMENTS` - What to visualize (project name, topic, or "all projects")

## Step 1: Gather Information

Based on what user wants to visualize:

### For a Single Project
- Read project index.md
- Get recent files from Research/ and Daily Progress/
- Identify key themes, questions, resources

### For All Projects
- Use folder scanning to list all projects
- Read each project's index.md
- Identify status, stage, relationships

### For a Topic/Concept
- Search vault for the topic
- Find related notes and backlinks
- Identify clusters and connections

## Step 2: Design Canvas Layout

Use the `json-canvas` skill to create structured layout:

### Layout Strategies

**Mind Map (Radial)**
- Central concept in the middle
- Main themes radiating out
- Sub-topics branching from themes

**Project Dashboard (Grid)**
- Projects arranged by status (active, paused, complete)
- Color-coded by stage
- Connections show dependencies

**Research Map (Organic)**
- Related concepts clustered together
- Open questions in one area
- Resources in another
- Insights connecting across

**Timeline (Linear)**
- Chronological flow left to right
- Daily progress notes in sequence
- Key milestones marked

## Step 3: Create Canvas Elements

### Node Types

**Text Nodes** - For concepts, questions, insights
```
Color: Use to show meaning
- Red: Open questions, blockers
- Yellow: In progress
- Green: Completed, validated
- Blue: Key insights
- Purple: Resources to review
```

**File Nodes** - Link to actual notes
- Project index files
- Research materials
- Daily progress notes

**Group Nodes** - Organize related items
- Group by theme
- Group by project
- Group by time period

**Edges** - Show relationships
- Labeled edges explain connections
- Use for dependencies, references, relates-to

## Step 4: Generate Canvas File

Create `.canvas` file using `json-canvas` skill with:
- Clear positioning (avoid overlaps)
- Logical grouping
- Meaningful colors
- Descriptive labels

Save to appropriate location:
- Project canvases: `Projects/<name>/map.canvas`
- Topic maps: `Research/<topic>-map.canvas`
- Overview dashboards: `dashboards/projects-overview.canvas`

## Step 5: Explain and Offer Next Steps

After creating canvas:
> "I've created a canvas visualization showing:
> - [describe key elements]
> - [explain layout logic]
> - [highlight insights visible in the map]
>
> Open `<path>` in Obsidian to explore interactively.
>
> Would you like me to:
> - Add more details
> - Focus on a specific area
> - Create a different view"

## Example: Project Research Map

For a project on "Market Analysis":

```
Center: "Market Analysis" (project index)
  ├─ Left: Research Phase
  │   ├─ File: [[Competitor Analysis]]
  │   ├─ File: [[Customer Interviews]]
  │   └─ Group: "Data Sources"
  │
  ├─ Right: Key Questions (text nodes in yellow)
  │   ├─ "How big is the TAM?"
  │   ├─ "What's our pricing power?"
  │   └─ "Who are we really competing with?"
  │
  ├─ Bottom: Daily Progress (timeline)
  │   ├─ 2026-01-15 → 2026-01-18 → 2026-01-21
  │
  └─ Top: Insights (green text nodes)
      ├─ "Bottom-up beats top-down"
      └─ "Need better competitive data"
```

## Example: All Projects Dashboard

```
Grid Layout by Status:

┌─ Active ─────────────┐  ┌─ Paused ──────┐
│ • Market Analysis    │  │ • Old Project │
│ • Product Research   │  └───────────────┘
│ • Customer Strategy  │
└──────────────────────┘  ┌─ Complete ────┐
                           │ • Launch Plan │
                           └───────────────┘

Colors: Active=Yellow, Paused=Gray, Complete=Green
```

## Tips for Effective Visualizations

- **Keep it simple**: Don't try to show everything
- **Use color meaningfully**: Consistent color = consistent meaning
- **Group related items**: Make patterns visible
- **Label edges**: Explain relationships
- **Leave space**: Don't crowd the canvas
- **Test the view**: Make sure it tells a story

## Common Patterns

| Pattern | Best For | Layout |
|---------|----------|--------|
| Mind Map | Exploring a concept | Radial from center |
| Timeline | Project progress | Left-to-right chronological |
| Dashboard | Project overview | Grid by status/stage |
| Network | Idea connections | Organic clusters |
| Hierarchy | Structured breakdown | Top-down tree |
