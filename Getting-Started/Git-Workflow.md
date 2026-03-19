# Git Workflow

This document defines the official Git workflow for all Lightning Robotics software projects.

Our goals:

- Prevent broken robot code
- Make collaboration safe and organized
- Teach professional software engineering practices
- Ensure changes are reviewable and reversible

All programmers are expected to follow this workflow.

---

# 🌳 Branch Strategy

We use a simplified GitHub Flow model.

## Main Branches

- `main` → Always competition-ready code
- `dev` (optional) → Active integration branch

No one pushes directly to `main`.

---

# 🛠 Development Process

## 1️⃣ Create a Feature Branch

Branch from `main` (or `dev` if used).

Branch naming format:

feature/<subsystem>-<short-description>

Examples:

- feature/intake-soft-limits
- feature/shooter-feedforward
- feature/auto-two-piece
- fix/drivetrain-inversion
- refactor/constants-cleanup

---

## 2️⃣ Make Small, Focused Changes

Each branch should:

- Solve one problem
- Add one feature
- Fix one bug

Avoid mixing unrelated changes.

---

## 3️⃣ Commit Standards

Commits should be:

- Clear
- Specific
- Professional

### Good Commit Messages

- Add intake pivot soft limits
- Fix shooter motor inversion
- Refactor constants into subsystem classes

### Bad Commit Messages

- stuff
- update
- fixed things
- testing

---

# 🔁 Pull Requests (PRs)

All changes must be merged via Pull Request.

Never push directly to `main`.

---

## PR Requirements

A PR must include:

- Clear description of what changed
- Why the change was needed
- Testing performed
- Screenshots if dashboard changes

Example PR description:

> Adds PID control to intake pivot.
> Tested on practice robot.
> Verified soft limits prevent over-rotation.

---

## Review Process

Before merging:

- At least one other programmer reviews
- Code compiles successfully
- Robot deploys successfully
- No broken features

Mentor approval required for:

- Architecture changes
- Major subsystem rewrites
- Autonomous logic changes before competition

---

# 🚦 Merging Rules

Only merge if:

- Build passes
- Code has been tested on robot or simulator
- No merge conflicts
- Documentation updated if necessary

Delete feature branch after merge.

---

# 🧠 Constants Rule

If a change modifies:

- CAN IDs
- Motor directions
- PID values
- Subsystem architecture

You must update:

- Constants.java
- Engineering documentation if applicable

---

# 🚨 Emergency Competition Fixes

If urgent fix is needed:

1. Create branch: `hotfix/<issue>`
2. Make minimal fix
3. Test immediately
4. Merge into main
5. Tag release (see below)

No direct pushes, even under pressure.

---

# 🏷 Version Tagging (Important Before Competition)

Before each competition:

- Ensure `main` is stable
- Create GitHub Release
- Tag version:

Example:
2026-week1-ready
2026-district-event1
2026-provincials

This allows rollback if needed.

---

# 🔄 Syncing Your Local Repo

Before starting work each day:

```bash
git checkout main
git pull origin main
Then create your feature branch.

Never branch from outdated code.
```
