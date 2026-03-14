# Changelog

## 1.0.1 — 2026-03-14

### Added
- `/fix-test` command — auto-diagnose and fix failing tests with
  up to 3 retry attempts per test. Identifies root causes (mock
  mismatches, assertion drift, import errors, etc.), applies fixes,
  and re-runs to verify.

### Fixed
- Plugin structure: commands and skills now at repo root for
  correct plugin marketplace layout.

## 1.0.0 — 2026-03-14

### Added
- `/code-review` — multi-pass code review (security, quality,
  performance, architecture)
- `/security-audit` — OWASP-aligned vulnerability scan with
  remediation plan
- `/smart-test` — find test gaps and generate tests for uncovered
  code
- `/bug-predict` — predict likely bug locations from patterns and
  complexity
- `/doc-gen` — generate documentation from source code
- Five matching skills powering each command
