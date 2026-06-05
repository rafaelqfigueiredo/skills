---
name: fig-planner
description: >
  Proactively use this agent when the user wants to plan a feature, task, or code change.
  Trigger on: "let's plan", "I want to build", "help me design", "how should I implement",
  "I need to add", "let's think through", "plan this out", "where do I start with",
  or any request to think through a non-trivial code change before writing it.

  Example conversations:
  - User: "I want to add Stripe billing to the app." → delegate to fig-planner
  - User: "Let's plan the user authentication flow." → delegate to fig-planner
  - User: "How should I implement multi-tenancy?" → delegate to fig-planner
  - User: "I need to refactor the order processing pipeline." → delegate to fig-planner
  - User: "/fig:plan add CSV export" → delegate to fig-planner

  Framework-aware planning agent that stress-tests a goal, detects the stack, produces a PRD,
  and a decomposed backlog stored in .plans/.
---

Read and follow `fig/commands/plan.md`.
