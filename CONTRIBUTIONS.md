# Contributions Guide — Ournetwork Engineering Standards

This document defines how to contribute to the Launchpad service under Ournetwork engineering standards. It is the authoritative guide for workflow, conventions, and quality gates.

## Fork-Based Workflow (Mandatory)
- You ALWAYS begin by forking the repository: https://github.com/ouronetwork/Launchpad
- Clone your fork locally (`git clone git@github.com:<your-user>/Launchpad.git`).
- Create a NEW branch in your fork for every change.
- ALL commits must be made to your fork only.
- NEVER push or commit directly to the organization repository.
- Open a Pull Request from your fork’s branch → into: `ouronetwork/Launchpad` → `main` branch.

Quick start:
```bash
# 1) Fork on GitHub, then clone your fork
git clone git@github.com:<your-user>/Launchpad.git
cd Launchpad

# 2) Add upstream to keep your fork in sync
git remote add upstream git@github.com:ouronetwork/Launchpad.git

# 3) Create a branch in YOUR fork (use a Jira key)
git checkout -b feature/DEM-123-short-description

# 4) Commit to your fork; push to origin (your fork)
git add -A
git commit -m "[DEM-123] Implement feature X"
git push -u origin feature/DEM-123-short-description

# 5) Open PR: origin/feature → ouronetwork/Launchpad:main
```

## Mandatory Jira Integration
- Always start from a Jira ticket (DEM-###) and include the key in branch names, commits, and PRs.
- Link the PR to the Jira issue using the GitHub–Jira integration to sync status.
- Governance tickets for broader changes:
  - DEM-1 — SDLC end-to-end framework (processes, CI/CD, release, governance)
  - DEM-2 — Documentation standards (README, CONTRIBUTIONS, docs updates)
  - DEM-3 — Migration/standardization initiative (repository structure, cleanup)

## Branch Naming Conventions
- `feature/DEM-###-short-description`
- `bugfix/DEM-###-short-description`
- `hotfix/DEM-###-short-description`

Examples:
- `feature/DEM-217-service-scaffold`
- `bugfix/DEM-308-fix-auth-timeout`
- `hotfix/DEM-401-revert-bad-release`

## Commit Conventions
- Format: `[DEM-###] short descriptive commit message`
- The body should explain:
  - what changed
  - why it changed
  - tests performed
  - any documentation updates

Example:
```
[DEM-217] Add FastAPI health endpoint

- Create /health route returning version and uptime
- Adds unit tests (pytest) for 200 OK response
- Updates README with local run instructions
```

## Pull Request Requirements
- Target repository/branch: `ouronetwork/Launchpad` → `main`.
- Link the Jira ticket (DEM-###) in the PR title or description.
- Follow the PR template (include summary, screenshots/logs, testing notes, risks, rollout plan).
- All CI/CD checks must pass (build, tests, linting, type checks).
- At least one reviewer approval required.
- Keep PRs focused and small; prefer incremental changes over large batches.
- Keep your PR up to date with `main` (rebase or merge as appropriate).

### Code Review and Approvals
- Reviewers assess correctness, tests, security, performance, readability, standards compliance, and Jira linkage.
- At least one reviewer required; consider two for security/compliance/production-critical areas.
- Authors must address feedback or provide rationale for trade-offs.

## Testing Requirements
- Unit tests are required for new features and bug fixes.
- All tests must pass locally and in CI before creating a PR.
- Linting must pass:
  - Frontend: `eslint`
  - Backend: `flake8` (and optional `black --check`, `mypy`)
- Where practical, add UI/interaction tests for user-facing changes.
- Suggested coverage goals: aim for 80%+ on critical paths.

### CI, Quality Gates, and Security
- CI must run tests, lint, and type checks (where applicable); failing checks block merges.
- Include security/static analysis if configured; do not bypass security gates.

## Documentation Requirements
- Update `README.md` and/or `CONTRIBUTIONS.md` when behavior, setup, or standards change.
- Source code must include meaningful comments where non-obvious.
- Update diagrams or docs if architecture, endpoints, or interfaces change.

### Code Structure and Consistency
- Follow existing project structure and patterns; prefer consistency over novelty.
- Clean up related code where safe (naming, dead code) as part of changes.
- Prefer incremental refactors to large, mixed changes. Propose broader refactors with a dedicated Jira ticket.

## Definition of Done
- Code complete and compiles/lints without errors.
- Tests created/updated and passing locally and in CI.
- Linting passes (`eslint` and `flake8`, plus optional format/type checks).
- Documentation updated (README/CONTRIBUTIONS and any diagrams).
- PR reviewed, approved, and merged into `main`.

## PR Checklist (copy into your PR description)
- [ ] Linked to Jira ticket (e.g., DEM-###)
- [ ] Small, focused scope with clear description
- [ ] Unit tests added/updated and passing
- [ ] Docs/comments updated (README/CONTRIBUTIONS, inline as needed)
- [ ] Linting and CI checks pass

## Jira Integration in Development
1) Start from a Jira issue (e.g., DEM-###).
2) Create your feature branch using the Jira key (`feature/DEM-###-...`).
3) Include the Jira key in all commit messages: `[DEM-###] ...`.
4) Open the PR and link the Jira ticket; ensure status transitions as per team workflow.

## Local Development Expectations
- Frontend (React + Vite): `npm ci` then `npm run dev`; `npm test`; `npm run lint`.
- Backend (FastAPI): `pip install -r requirements.txt`; `pytest`; `flake8`; run with `uvicorn`.
- Docker Compose: prefer `docker compose up -d --build` for full-stack validation.

## Prohibited Actions
- Do not push directly to `ouronetwork/Launchpad`.
- Do not merge without at least one approval.
- Do not bypass CI/CD checks.

## Keeping Your Fork in Sync
```bash
# Fetch upstream changes and rebase your branch
git fetch upstream
git checkout main
git rebase upstream/main
git push origin main

# Update your feature branch
git checkout feature/DEM-123-short-description
git rebase main
git push -f origin feature/DEM-123-short-description
```

---

By contributing, you agree to follow these standards. PRs not adhering to the fork-based workflow and quality requirements will be rejected.