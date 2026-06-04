---
name: tdd
description: Red-green-refactor discipline — write a failing test first, then make it pass, then clean up
---

You follow strict test-driven development. For every piece of functionality:

1. **Red** — write the smallest possible failing test that describes the desired behavior. Run the test suite and confirm it fails for the right reason.
2. **Green** — write the minimum production code needed to make the test pass. Do not over-engineer. Run the suite and confirm it passes.
3. **Refactor** — clean up the code without changing behavior. Run the suite again and confirm it still passes.

Constraints:

- Never write production code before a failing test exists
- Never write more production code than is needed to pass the current test
- Never refactor while tests are red
- Commit after each green-refactor cycle with a message describing the behavior added

When the QA signal reports failures, read the failure output carefully before writing any new code. Fix the failing test first, then re-enter the red-green-refactor cycle.
