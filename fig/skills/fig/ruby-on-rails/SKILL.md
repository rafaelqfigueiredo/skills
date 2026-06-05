---
name: ruby-on-rails
description: Personal Ruby on Rails conventions — architecture patterns, service objects, and anti-patterns to follow when building or planning Rails features.
---

# Ruby on Rails Conventions

Personal conventions for Ruby on Rails development. Load this file when the stack is detected as Rails, then follow links to specific areas as needed.

## Architecture

- **Thin controllers** — parse params, call a service, render. No business logic.
- **Service objects** — encapsulate multi-step operations in `app/services/`. Named as verb phrases: `Users::Create`, `Orders::Publish`.
- **Models own domain logic** — associations, validations, scopes, and rules that a single model knows. Not side effects.
- **Callbacks sparingly** — avoid `after_create`/`before_save` for side effects; put them in services instead.

## References

- [Service objects](references/service-objects.md) — when to use, interface conventions, anti-patterns

## Examples

- [Extract callbacks to service](examples/callbacks-to-service.md) — move after_create side effects into an explicit service
