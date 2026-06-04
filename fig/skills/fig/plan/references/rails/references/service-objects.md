---
name: rails-service-objects
description: Personal conventions for service objects in Rails — when to use them, interface, naming, and anti-patterns to avoid.
---

# Service Objects

## When to Use

- Orchestrating multiple models for a single use case
- Operations that need a transaction boundary across models
- Business logic that doesn't belong in any single model
- Operations called from more than one controller or job

## When NOT to Use

- Simple CRUD — let the controller handle it directly
- Domain logic that a single model owns — keep it in the model
- Single-model operations with no side effects

## Interface

All services are callable via `.call`:

```ruby
class ApplicationService
  extend Dry::Initializer

  def self.call(...) = new(...).call
end
```

## Naming

- Verb phrase scoped to the domain: `Users::Create`, `Orders::Publish`, `Payments::Refund`
- Avoid generic suffixes like `Manager`, `Handler`, `Processor`

## Return values

Return the primary object or raise on failure. Use result objects (dry-monads) only when callers need to branch on success/failure without exceptions.

## Anti-patterns

- **Anemic models** — don't strip domain logic into services; models should still know their own rules
- **Bag of random objects** — every service should follow the same interface and naming convention
- **Premature abstraction** — start with a plain service; extract base classes only after patterns repeat
