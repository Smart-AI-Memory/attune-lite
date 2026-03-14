---
description: Run a multi-pass code review (security, quality, performance, architecture)
argument-hint: <path>
allowed-tools:
  - Read
  - Glob
  - Grep
  - Agent
---

Run a structured code review on `$ARGUMENTS`.

If no path was provided, review the current working directory.

Use the code-review skill to perform the review. Follow its
full process: security pass, quality pass, performance pass,
architecture pass, then synthesize into a single report with
scores and prioritized findings.
