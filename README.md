# Cursor Fundamentals

**Cursor Fundamentals** (`cursor-fundamentals`) is a Cursor Team Marketplace built around one idea: give every function a small, focused plugin that encodes how the team actually works. Each plugin contributes the minimum set of rules, skills, agents, and MCP servers needed to raise quality in that function without overlapping with the others.

## Plugins

### Cursor Starter Pack

Engineering baseline that every contributor gets by default. It ships the non-negotiables: code quality and system design rules, a repo-onboarding skill, commit and git hygiene, planning output, and the naming conventions that make markdown files and Cursor agents consistent across the org. The `code-skeptic` and `code-oracle` agents handle critical review and deeper architectural reasoning when a change needs a second set of eyes. Start here; most other plugins assume this one is installed.

### Product Management

Owns everything between "we should build this" and "engineering can execute on it." Use it to draft implementation-ready Jira tickets, summarize a board or sprint for a stakeholder update, and stress-test a plan with the `devils-advocate` agent before any code is written. The included Atlassian MCP wires the plugin into Jira and Confluence so ticket reading and writing stay in the loop.

### Design

Covers UX definition and the handoff into code. The `wireframes` and `mockup` skills help teams reason about backend-aware UI states and high-fidelity layouts, the `component-designer` agent focuses on component-level decisions, and the `ui-engineer` agent implements the result in a way that respects the design intent. The Figma MCP keeps Figma files and code aligned without context switching.

### Technical Writing

The single home for developer-facing prose. It generates and updates READMEs, produces weekly review summaries, and flags when a code change should trigger a README update (`readme-hygiene`). The `docs-writer` agent handles longer-form documentation such as API references and guides. An optional Notion MCP is included for teams that publish there. Markdown file-naming conventions intentionally live in **Cursor Starter Pack** so naming stays universal rather than docs-specific.

### Testing

Focused specifically on automated tests. The `test-engineer` agent adds and extends unit and E2E tests that match the project's frameworks and conventions, and the `test-runner` agent runs and interprets the relevant test commands. `mcp.json` is intentionally empty so each team can add CI or vendor MCP servers that fit their stack.

## Repository structure

- `.cursor-plugin/marketplace.json`: marketplace manifest and plugin registry
- `plugins/<plugin-name>/.cursor-plugin/plugin.json`: per-plugin metadata
- `plugins/<plugin-name>/rules`: rule files (`.mdc`)
- `plugins/<plugin-name>/skills`: skill folders with `SKILL.md`
- `plugins/<plugin-name>/agents`: subagent definitions
- `plugins/<plugin-name>/mcp.json`: MCP server configuration for each plugin

## Use this marketplace on your team

Cursor imports a team marketplace by reading `.cursor-plugin/marketplace.json` from a GitHub repository. There are two realistic ways to consume Cursor Fundamentals: **point at this public repo directly**, or **fork it** and tailor the plugins to your team. Pick based on how much you want to customize and how much upstream change you're willing to inherit.

### Option A: Point at the public repo directly (no fork)

Fastest path. Import this repo's GitHub URL as your team marketplace. Your team automatically tracks every commit upstream makes to the default branch.

1. In Cursor, go to **Dashboard → Settings → Plugins → Import**.
2. Paste this repo's GitHub URL.
3. Pick access groups and mark each plugin **Required** (auto-installed) or **Optional** (developer choice).
4. Save.

**Benefits**

- Zero maintenance. No fork, no merges, no CI.
- New plugins and fixes show up automatically as upstream ships them.
- Simple story for small teams that don't need org-specific tweaks yet.

**Risks**

- You inherit **every** upstream change on the default branch, including breaking ones. Upstream decisions about plugin scope, agents, or MCP servers become your decisions by default.
- You cannot add org-specific rules, agents, or MCP credentials to the marketplace itself. You can still configure MCP env vars locally, but plugin content stays whatever upstream ships.
- On the **Teams** plan you only get 1 team marketplace, so "pointing at upstream" uses up that slot and blocks you from publishing your own.
- You are trusting the upstream maintainer. If you don't control this repo, treat this option like installing any third-party extension and review the contents first.

**Best for:** teams evaluating Cursor team marketplaces, small teams happy with the defaults, or orgs that explicitly want to track an official/maintained baseline.

### Option B: Fork and publish your own (recommended for most teams)

Fork this repo into your GitHub org, edit it to match your stack and conventions, and register the fork as your team marketplace. You own what ships, and you can still pull upstream updates as PRs when you want them.

1. Fork this repository to your team's GitHub organization (for example, `your-org/cursor-fundamentals`).
2. Clone the fork locally and edit plugin contents (`rules/`, `skills/`, `agents/`, `mcp.json`) to reflect your stack, conventions, and tooling. Remove plugins you don't want.
3. If you rename the marketplace, update both `name` (lowercase kebab-case) and `displayName` in [.cursor-plugin/marketplace.json](.cursor-plugin/marketplace.json).
4. Run `node scripts/validate-template.mjs` to catch manifest, frontmatter, and path issues before publishing.
5. Commit and push. If the repo is private, grant the Cursor GitHub app read access when prompted.
6. In Cursor, go to **Dashboard → Settings → Plugins → Import**, paste your fork's URL, pick access groups, and mark each plugin **Required** or **Optional**.

**Benefits**

- Full control over plugin content, scope, and MCP wiring.
- Org-specific rules and agents live in one place, versioned in git alongside your other internal tools.
- Updates ship when *you* push to the default branch, on your review cadence.

**Risks**

- You own maintenance: merging upstream updates, validating manifests, and keeping plugin docs aligned with reality.
- Public forks are public on GitHub; if your plugins reference internal systems, use a private fork (or "Use this template") and grant the Cursor GitHub app access.

**Best for:** any team that wants to encode its own conventions, credentials, or tool choices — which is most teams once they move past evaluation.

### Plan limits and access

- **Teams** plan: up to 1 team marketplace per team. **Enterprise** plan: unlimited team marketplaces.
- Cursor syncs new commits from the default branch, so pushing to the repo you imported is how you ship updates.
- Members of the selected access groups see the plugins in **Settings → Plugins** inside Cursor.

## Further reading

- [Cursor Plugins documentation](https://cursor.com/docs/plugins) — plugin anatomy (rules, skills, agents, commands, MCP, hooks) and team-marketplace setup.
- [Cursor Marketplace](https://www.cursor.com/marketplace) — officially reviewed plugins you can use as references.
- [cursor/plugin-template](https://github.com/cursor/plugin-template) — minimal starter for building a single plugin or multi-plugin marketplace.
- [Team dashboard](https://cursor.com/docs/account/teams/dashboard) — where team marketplaces are imported and managed.
