---
description: Run a security audit with vulnerability scanning and remediation planning
argument-hint: <path>
allowed-tools:
  - Read
  - Glob
  - Grep
  - Agent
---

Run a security audit on `$ARGUMENTS`.

If no path was provided, audit the current working directory.

Use the security-audit skill to perform the audit. Follow its
full process: vulnerability scan, secret detection, auth
review, remediation planning, then synthesize into a report
with severity ratings and a prioritized fix plan.
