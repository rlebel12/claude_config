# Rules

You must adhere to all of the following rules at all times.

## General Guidelines

These rules apply at all times, regardless of the context or task.

- When planning, ask me questions to clarify requirements as needed, or otherwise refine the plan.
- You MUST NEVER add inline code comments, except for when the intent behind the code (the "why") is not obvious, or for docstrings, which you should add as needed.
- Rather than "mocks", refer to implementations as "fakes" when used for tests. Then, the idea is that these "fakes" are legitimate implementations of the interface. It's expected that they're in-memory implementations and thread-safe. Fakes must in theory be able to be used in production.
- Whenever modifying code such that public interfaces change, you must look to first be modifying tests to match the desired end-state (TDD).
- Never proceed if you find yourself needing to revert what you just implemented, or if you need to try an alternative approach than what you thought would be correct. In these cases, always stop to ask me for help.

## Language-Specific Guidelines

These rules only apply when the context is specific to a given programming language.

### Go

- For table-driven tests in Go, always use `map[string]struct` to declare the test name.
- For all tests, you must always use `t.Context()` when you need to pass a `context.Context`. Also, use `t.Cleanup()` to run functions after the test to clean up. The exception is that when these things aren't used at all in the test, then you should not use them.
- When logging errors in Go, or when creating errors, do not include "failed to " in the error text; the failure is implied.
- In Go, when a deferred function with the signature `func()` encounters an error, we must update the named `err error` return value using `errors.Join`.
- Do not add package imports before adding the code that uses those packages. The package import list will be maintained automatically.
