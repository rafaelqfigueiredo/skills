## master

## 0.3.0 (2026-06-05)

- Moved planning workflow into `fig/commands/plan.md`; `fig-planner` agent now delegates to the command and triggers proactively on natural-language planning requests.
- Added `fig/skills/fig/detect-stack` skill — stack detection extracted from the old `plan` skill into its own reusable skill.
- Added `fig/skills/fig/ruby-on-rails` skill — Rails conventions promoted to a top-level skill with references and examples migrated from the old `plan/references/rails/` tree.
- Removed `fig/skills/fig/plan` — replaced by the command, `detect-stack`, and framework-specific skills.

## 0.2.0 (2026-06-05)

- Added `/fig:plan` command and `fig-planner` agent for framework-aware feature planning with grill-me, PRD, implementation plan, and backlog decomposition stored in `.plans/`.

## 0.1.0 (2026-06-04)

- Added `/fig:handoff` command to compact the current conversation into a handoff document for a fresh agent.
- Added `/fig:grill-me` command to run the interview engine on a proposed change.
- Added `/fig:tdd` command to enter red-green-refactor discipline mode.
- Added `/fig:to-backlog` command to break a plan or PRD into issue tracker tickets.
- Added `/fig:to-prd` command to synthesize a grilling session into a structured PRD.
- Added `/fig:write-a-skill` command to scaffold new skills following repo conventions.
