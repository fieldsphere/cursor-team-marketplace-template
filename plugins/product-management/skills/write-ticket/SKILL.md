---
name: write-ticket
description: Write high-quality Jira tickets from product requests, incidents, or discovery notes. Use when drafting or refining implementation-ready Jira issues.
---

# Write Jira Ticket

Create clear, implementation-ready Jira tickets that engineers can execute without follow-up clarification.

## Required Output Structure

1. Title
   - Concise and action-oriented.
   - Include key domain/context.

2. Problem
   - What user or business issue is being solved.
   - Why now and expected impact.

3. Scope
   - In scope and out of scope bullets.

4. Requirements
   - Functional requirements as testable bullets.
   - Non-functional constraints (performance, reliability, security) when relevant.

5. Acceptance Criteria
   - Use `Given/When/Then` or explicit checklist.
   - Include error and edge-case behavior.

6. Technical Notes
   - Relevant systems/services, API endpoints, dependencies, risks.

7. QA Notes
   - Concrete validation steps and sample data.

## Quality Rules

- No emojis in ticket title or body.
- Avoid ambiguous language (for example, "improve", "optimize") without measurable definition.
- Make each requirement independently verifiable.
- Include assumptions explicitly when requirements are incomplete.
