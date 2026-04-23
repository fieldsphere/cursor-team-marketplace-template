---
name: update-readme
description: Generate or update a repository README with startup instructions and a Mermaid architecture diagram. Use when creating a README, updating project documentation, onboarding new contributors, or when the user mentions README, startup guide, or architecture overview.
---

# Update README

Generate or update a comprehensive README by analyzing the repository's code, config files, and directory structure.

## Workflow

```
Task Progress:
- [ ] Step 1: Analyze repository
- [ ] Step 2: Draft startup instructions
- [ ] Step 3: Generate architecture diagram
- [ ] Step 4: Assemble and write README
- [ ] Step 5: Verify
```

### Step 1: Analyze Repository

Scan the repo to gather context. Check for:

| Signal | Files to Check |
|--------|---------------|
| Language/runtime | `package.json`, `pyproject.toml`, `go.mod`, `Cargo.toml`, `Gemfile`, `*.csproj` |
| Package manager | `package-lock.json`, `yarn.lock`, `pnpm-lock.yaml`, `poetry.lock`, `uv.lock` |
| Containerization | `Dockerfile`, `docker-compose.yml`, `.devcontainer/` |
| CI/CD | `.github/workflows/`, `.gitlab-ci.yml`, `Jenkinsfile` |
| Environment | `.env.example`, `.env.template`, `.envrc` |
| Existing docs | `README.md`, `docs/`, `CONTRIBUTING.md` |
| Entry points | `main.ts`, `index.ts`, `app.py`, `main.go`, `src/` |
| Config | `tsconfig.json`, `vite.config.*`, `next.config.*`, `webpack.config.*` |

If a README already exists, preserve any sections the user has manually written (badges, license, contributing guidelines) and only update the startup and architecture sections.
