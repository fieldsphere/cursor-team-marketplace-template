---
name: summarize-board
description: Summarize Jira board status for stakeholders with risks, blockers, and delivery confidence. Use for weekly PM updates and planning checkpoints.
---

# Summarize Jira Board

Produce a concise board summary that is useful for engineering, product, and leadership updates.

## Input Expectations

- Active sprint or board filter
- Issue list with status, assignee, priority, and due date when available
- Optional labels/components for grouping

## Output Sections

1. Snapshot
   - Total issues by status
   - Work started vs not started
   - Items at risk

2. Progress Highlights
   - 3-5 bullets on meaningful movement this period
   - Call out completed high-impact items

3. Risks and Blockers
   - Blocked issues with cause, owner, and recommended unblock action
   - Dependencies likely to impact delivery

4. Delivery Confidence
   - Confidence rating: High, Medium, or Low
   - Short rationale with leading indicators

5. Recommended Actions
   - Priority actions for PM/EM in the next 1-3 days

## Writing Rules

- Keep tone objective and concise.
- No emojis in summaries intended for Jira comments or ticket updates.
- Prefer concrete counts and dates over vague statements.
