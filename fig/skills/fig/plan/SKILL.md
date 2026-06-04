---
name: plan
description: Framework-aware feature planning that detects the stack and produces a structured implementation plan using personal conventions. Use when planning a feature, task, or architectural change, especially in multi-framework or monorepo projects.
lint-skip:
  - rule: reference.no-orphans
    reason: "Framework subfiles (rails/references/, rails/examples/) are intentionally linked from their language index file (rails.md), not directly from SKILL.md"
---

# Framework-Aware Planning

## Stack signals

| File                                  | Framework        |
| ------------------------------------- | ---------------- |
| `Gemfile`                             | Ruby / Rails     |
| `package.json`                        | Node / JS / TS   |
| `go.mod`                              | Go               |
| `pyproject.toml` / `requirements.txt` | Python           |
| `Cargo.toml`                          | Rust             |
| `mix.exs`                             | Elixir / Phoenix |

For monorepos, detect per subdirectory. Load the matching reference from `references/` if one exists; proceed without it if not.

## Workflows

- [Planning flow](workflows/planning-flow.md) — full session: grill → detect → PRD → plan → backlog

## Conventions

- [Ruby on Rails](references/rails.md)
