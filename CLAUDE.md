# Rules

You must adhere to all of the following rules at all times.

## General Guidelines

These rules apply at all times, regardless of the context or task.

- If you are unsure of something, you must stop and ask me for clarification.
- Use the research subagent when you need to explore code to find a given target/subject.
- You must follow/extend existing coding patterns present in a project/codebase.

## Implementation Approach

You (primary Claude instance) implement code directly while invoking specialized reviewers for quality assurance. Follow this iterative workflow:

1. **Implement**: Focus on functional correctness first
2. **Auto-review**: Immediately invoke appropriate language reviewer after implementation
3. **Refine**: Apply critical and important refinements from reviewer feedback
4. **Continue**: Proceed to next implementation step

### Automatic Review Rules

After implementing code in any language, automatically invoke the appropriate reviewer:

- **Go code** → Use `go-code-reviewer` agent
- **Python code** → Use `python-code-reviewer` agent
- **SvelteKit code** → Use `sveltekit-code-reviewer` agent

Apply reviewer feedback selectively:

- **Critical issues**: Always fix (security, performance, correctness)
- **Important issues**: Usually fix (significant maintainability improvements)
- **Optional issues**: Consider based on context and time constraints

## Language Guidelines

Keep these essential patterns in mind during implementation:

### Go Essentials

- Use `errors.Is/As` not `==` for error comparisons
- Use `slog` for logging with context parameters
- Table-driven tests with `map[string]struct{}` for test cases
- Avoid "failed to" prefixes in error messages
- Handle deferred function errors with `errors.Join` on named returns
- Define interfaces where consumed, not where implemented
- Use new types for entity IDs (implement `String()` method)

### Python Essentials

- Use `pathlib` not `os.path` for file operations
- Use `dataclasses` over plain dicts for structured data
- Modern type hints: `list[str]` not `List[str]`
- Use `async/await` for I/O bound operations
- Context managers (`with` statements) for resource management
- f-strings for string formatting

### SvelteKit Essentials

- Svelte 5 mechanisms, runes, etc.
- `load` functions in `+page.ts/+layout.ts` for data fetching
- Component prop destructuring with defaults
