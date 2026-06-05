---
name: detect-stack
description: Detect the framework and language of a project by scanning for well-known marker files, then load the matching framework skill if one exists.
---

# Stack Detection

Scan the project root (and per subdirectory for monorepos) for the marker files below. Use the first match per directory.

| Marker file                           | Framework        | Skill                                  |
| ------------------------------------- | ---------------- | -------------------------------------- |
| `Gemfile`                             | Ruby on Rails    | `skills/fig/ruby-on-rails/SKILL.md`    |
| `package.json`                        | Node / JS / TS   | —                                      |
| `go.mod`                              | Go               | —                                      |
| `pyproject.toml` / `requirements.txt` | Python           | —                                      |
| `Cargo.toml`                          | Rust             | —                                      |
| `mix.exs`                             | Elixir / Phoenix | —                                      |

**Monorepos:** run detection per subdirectory. A repo may have multiple stacks; load each matching skill.

**No match:** proceed without a framework skill. Do not guess or invent conventions.

**Loading a skill:** when a skill path is listed in the table above, read and follow that file now — its conventions inform every subsequent step.
