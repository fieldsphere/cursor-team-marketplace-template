# Cursor Fundamentals

Team Marketplace **Cursor Fundamentals** (`cursor-fundamentals`): five focused plugins for Cursor.

## Included plugins

- **cursor-starter-pack**: Code quality, system design, onboarding, commits, git hygiene, planning output, markdown and agent naming, and review-focused agents
- **product-management**: Jira-oriented ticket writing, board summaries, devil's advocate critique, Atlassian MCP
- **design**: Wireframes, mockups, component design, UI engineer agent, Figma MCP
- **technical-writing**: README updates, weekly reviews, README hygiene, docs writer, optional Notion MCP
- **testing**: Test engineer and test runner agents; empty `mcp.json` ready for your CI or tooling

## Repository structure

- `.cursor-plugin/marketplace.json`: marketplace manifest and plugin registry
- `plugins/<plugin-name>/.cursor-plugin/plugin.json`: per-plugin metadata
- `plugins/<plugin-name>/rules`: rule files (`.mdc`)
- `plugins/<plugin-name>/skills`: skill folders with `SKILL.md`
- `plugins/<plugin-name>/agents`: subagent definitions
- `plugins/<plugin-name>/mcp.json`: MCP server configuration for each plugin

## Validate changes

Run:

```bash
node scripts/validate-template.mjs
```

This checks marketplace paths, plugin manifests, and required frontmatter in rule/skill/agent/command files.

## Submission checklist

- Each plugin has a valid `.cursor-plugin/plugin.json`
- Plugin names are unique, lowercase, and kebab-case
- `.cursor-plugin/marketplace.json` entries map to real plugin folders
- Required frontmatter metadata exists in plugin content files
- Logo paths resolve correctly from each plugin manifest (if present)
- `node scripts/validate-template.mjs` passes
