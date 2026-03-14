---
description: >-
  Auto-diagnose and fix your last failed tests. Identifies root causes
  (mock mismatches, assertion drift, import errors, etc.), applies fixes,
  and re-runs to verify — up to 3 attempts per test.
argument-hint: --lf
allowed-tools:
  - Read
  - Glob
  - Grep
  - Bash
  - Agent
  - Edit
---

Auto-diagnose and fix failing tests using `$ARGUMENTS`.

Default behavior: run `pytest --lf` to re-run last failed tests.
If a specific path or test name is provided, target those instead.

Use the smart-test skill as a reference for project test conventions,
then follow this process:

1. **Run failing tests.** Execute `pytest $ARGUMENTS` to capture
   failures and tracebacks. Default to `--lf` if no arguments given.

2. **Diagnose.** For each failure:
   - Read the test code and the source code it exercises
   - Identify the root cause (mock mismatches, assertion drift,
     import errors, missing fixtures, stale snapshots, etc.)
   - Determine whether the fix belongs in the test or the source

3. **Fix.** Apply the minimal fix:
   - If the source code has a bug, fix the source
   - If the test is outdated or incorrect, update the test
   - If a fixture or import is missing, add it
   - Preserve existing test conventions and style

4. **Verify.** Re-run the fixed test to confirm it passes.
   If it still fails, repeat diagnose-fix-verify up to 3 attempts.

5. **Report.** Summarize what failed and what was fixed.
