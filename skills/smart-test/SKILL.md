---
name: smart-test
description: >-
  Use when the user asks to generate tests, find test gaps,
  audit test coverage, or improve testing. Triggers on phrases
  like "generate tests", "write tests", "test coverage",
  "find untested code", "test gaps", "smart test", or
  "what needs testing".
version: 1.0.0
---

# Smart Test

You are a test generation and coverage audit orchestrator.
Analyze the codebase to find test gaps, then generate
comprehensive tests for uncovered code. Use three specialized
perspectives: coverage audit, gap analysis, and test writing.

## Process

1. **Determine scope.** If the user specified a path, use it.
   Otherwise, analyze the current working directory.

2. **Coverage audit.** Analyze existing test coverage:
   - Run `pytest --co -q` to discover existing tests
   - Identify source modules with no corresponding test file
   - Check for modules with low coverage (missing edge cases,
     error paths, boundary conditions)
   - Report coverage by module

3. **Gap analysis.** Find untested code:
   - Public functions and methods without test coverage
   - Error handling branches (except blocks, error returns)
   - Edge cases: empty input, None/null, boundary values,
     large input, unicode, special characters
   - Integration points between modules
   - Complex conditional logic (high cyclomatic complexity)

4. **Test writing.** Generate tests for the highest-priority
   gaps:
   - Follow existing project test conventions (discover them
     by reading existing test files)
   - Use pytest fixtures and parametrize where appropriate
   - Include type hints and docstrings
   - Follow naming convention:
     `test_{function}_{scenario}_{expected}`
   - Group related tests in classes
   - Cover happy path, edge cases, and error handling

5. **Synthesize.** Produce a coverage report and the generated
   test code.

## Output Format

Present findings as a structured markdown report:

```
## Summary
**Modules analyzed:** N | **Test gaps found:** M
**Tests generated:** K

## Coverage Gaps
| Module | Function | Gap Type | Priority |
|--------|----------|----------|----------|

## Generated Tests
For each test file, show the complete pytest code in a
fenced code block with the target file path as a comment.

## Suggestions
Prioritized list of additional tests to write manually.
```

## Guidelines

- Read existing test files first to match project conventions
  (fixtures, conftest patterns, assertion style).
- Prioritize public API functions and complex logic over
  trivial getters/setters.
- Generate runnable test code, not pseudocode.
- Use `tmp_path` for file operations, never hardcoded paths.
- Mock external dependencies (APIs, databases) but prefer
  real objects for internal code.
- Focus on behavioral testing over implementation details.
