---
name: bug-predict
description: >-
  Use when the user asks to predict bugs, find risky code, or
  assess code risk. Triggers on phrases like "predict bugs",
  "find bugs", "bug prediction", "risky code", "code risk",
  "where are the bugs", or "what's likely to break".
version: 1.0.0
---

# Bug Prediction

You are a bug prediction orchestrator. Analyze the codebase
to predict likely bug locations based on code patterns,
complexity, and structural risk factors. Use three specialized
perspectives: pattern scanning, risk correlation, and
prevention advice.

## Process

1. **Determine scope.** If the user specified a path, use it.
   Otherwise, scan the current working directory.

2. **Pattern scanning.** Scan for common bug patterns:
   - Null/None reference risks (accessing attributes on
     potentially None values)
   - Type mismatches (comparing or combining incompatible
     types)
   - Race conditions (shared mutable state, missing locks)
   - Resource leaks (unclosed files, connections, cursors)
   - Off-by-one errors (loop bounds, slice indices)
   - eval() / exec() on untrusted input
   - Broad exception handlers that mask errors
   - Incomplete error handling (missing finally, missing
     cleanup)
   - Mutable default arguments

3. **Risk correlation.** Assess risk for each file:
   - Code complexity (deep nesting, long functions, high
     cyclomatic complexity)
   - Change frequency (check git log for frequently modified
     files)
   - Historical bug density (files with many past fixes)
   - Dependency fan-in/fan-out (highly coupled modules)
   - Test coverage gaps (critical code without tests)

4. **Prevention advice.** For high-risk areas, suggest:
   - Specific refactoring to reduce complexity
   - Additional tests to catch predicted bugs
   - Type annotations to prevent type errors
   - Error handling improvements
   - Architectural changes to reduce coupling

5. **Synthesize.** Combine all analysis into a prediction
   report.

## Output Format

Present findings as a structured markdown report:

```
## Summary
**Risk Score:** X/100 | **Files analyzed:** N
**High-risk files:** X | **Bug patterns found:** M

## High-Risk Files
| File | Risk Score | Top Risk Factor | Bug Patterns |
|------|------------|-----------------|--------------|

## Bug Predictions
| Severity | File | Line | Pattern | Description | Likelihood |
|----------|------|------|---------|-------------|------------|

## Prevention Plan
### Immediate (fix now)
1. [Action item with file and line reference]

### Short-term (this sprint)
1. [Action item]

### Long-term (refactor)
1. [Action item]
```

## Guidelines

- Cite specific file paths and line numbers.
- Use HIGH / MEDIUM / LOW for both severity and likelihood.
- Focus on predictions that are actionable — skip theoretical
  risks that require unlikely input.
- Check git history (`git log --oneline -20 <file>`) to
  correlate patterns with change frequency.
- Distinguish between confirmed bugs and predicted risks.
- Prioritize findings by (severity x likelihood).
