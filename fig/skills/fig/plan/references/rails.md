---
name: rails-index
description: Personal Rails conventions index — entry point for Rails-specific planning guidance covering architecture, patterns, and examples.
lint-skip:
  - rule: reference.one-level-deep
    reason: "Intentional index file — links down to rails/ subfiles which are deeper in the same references/ tree"
---

# Ruby on Rails Conventions

Personal conventions for Ruby on Rails development. The planner loads this file first and follows links to specific areas as needed.

## Architecture

- **Thin controllers** — parse params, call a service, render. No business logic.
- **Service objects** — encapsulate multi-step operations in `app/services/`. Named as verb phrases: `Users::Create`, `Orders::Publish`.
- **Models own domain logic** — associations, validations, scopes, and rules that a single model knows. Not side effects.
- **Callbacks sparingly** — avoid `after_create`/`before_save` for side effects; put them in services instead.

## References

- [Service objects](rails/references/service-objects.md) — when to use, interface conventions, anti-patterns

## Examples

- [Extract callbacks to service](rails/examples/callbacks-to-service.md) — move after_create side effects into an explicit service
