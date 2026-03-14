---
description: Predict likely bug locations based on code patterns and complexity
argument-hint: <path>
allowed-tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Agent
---

Predict bugs in `$ARGUMENTS`.

If no path was provided, scan the current working directory.

Use the bug-predict skill to perform the analysis. Follow its
full process: pattern scanning, risk correlation, prevention
advice, then produce a report with risk scores and a
prioritized prevention plan.
