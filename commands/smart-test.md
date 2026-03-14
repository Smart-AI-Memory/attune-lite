---
description: Find test gaps and generate tests for uncovered code
argument-hint: <path>
allowed-tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Agent
  - Write
---

Analyze test coverage and generate tests for `$ARGUMENTS`.

If no path was provided, analyze the current working directory.

Use the smart-test skill to perform the analysis. Follow its
full process: coverage audit, gap analysis, test writing, then
produce a report with coverage gaps and generated test code.
