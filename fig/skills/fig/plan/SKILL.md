---
name: plan
description: Framework-aware feature planning that detects the stack and produces a structured implementation plan using personal conventions. Use when planning a feature, task, or architectural change, especially in multi-framework or monorepo projects.
lint-skip:
  - rule: reference.no-orphans
    reason: "Framework subfiles (rails/references/, rails/examples/) are intentionally linked from their language index file (rails.md), not directly from SKILL.md"
---

# Framework-Aware Planning

## Process

### Step 1 — Detect the stack

Scan the repo root (and subdirectories for monorepos) for framework signals:

| File | Framework |
|---|---|
| `Gemfile` | Ruby / Rails |
| `package.json` | Node / JS / TS |
| `go.mod` | Go |
| `pyproject.toml` / `requirements.txt` | Python |
| `Cargo.toml` | Rust |
| `mix.exs` | Elixir / Phoenix |

For monorepos, list all detected frameworks and note which subdirectory each lives in.

### Step 2 — Load conventions

For each detected framework, check if a matching reference file exists under `references/`. Load it if present; proceed without it if not.

### Step 3 — Search prior solutions

Before planning, search `docs/solutions/` for entries relevant to the feature or domain. Prefer decisions already made in this codebase over generic patterns.

### Step 4 — Produce the plan

Output a structured plan with:

1. **Goal** — one sentence describing what will be built
2. **Stack context** — detected framework(s) and any relevant prior solutions
3. **Approach** — implementation strategy referencing loaded conventions where applicable
4. **Steps** — ordered, concrete steps small enough to execute one at a time
5. **Tests** — what to verify and how
6. **Open questions** — decisions needed before work starts

## Conventions

- [Ruby on Rails](references/rails.md)
