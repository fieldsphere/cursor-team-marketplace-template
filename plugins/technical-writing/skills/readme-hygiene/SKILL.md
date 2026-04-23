---
name: readme-hygiene
description: Check whether README documentation should be updated when code changes affect setup, usage, commands, configuration, environment variables, workflows, or user-visible behavior. Use when making changes that may invalidate existing README content or require new documentation.
---

# README hygiene

## Goal

Prompt the agent to notice when code changes should also trigger a README update.

## When to apply

- Setup or installation steps changed
- Commands, scripts, or developer workflows changed
- Environment variables or configuration changed
- Public behavior or user-facing usage changed
- A new package, service, or entry point was added

## Check

Ask:

1. Does this change make any existing README content inaccurate?
2. Does this introduce new setup, usage, or troubleshooting information?
3. Should the root `README.md` or a closer package README be updated?

## Default behavior

- If the answer is likely yes, explicitly suggest a README update
- If planning work, include README updates in the plan when relevant
- If implementing the change, check for an existing README before creating new docs
- Prefer updating the nearest relevant README over adding a new markdown file

## What to update

- Setup and installation
- Run and build commands
- Required environment variables
- Local development workflow
- Feature usage or integration steps
- Troubleshooting notes for common failure modes

## What to avoid

- Suggesting README edits for purely internal refactors with no doc impact
- Creating new markdown files when an existing README is the right home
- Repeating implementation details that belong in code or deeper docs
