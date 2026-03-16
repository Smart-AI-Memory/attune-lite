# Attune Lite

Six developer workflow commands for Claude Code: code review,
security audit, test generation, test fixing, bug prediction,
and documentation generation. No dependencies required.

## Install

**Step 1:** Add the marketplace:

```bash
claude plugin marketplace add Smart-AI-Memory/attune-lite
```

**Step 2:** Install the plugin:

```bash
claude plugin install attune-lite
```

Verify it loaded:

```bash
/plugins
```

## Commands

| Command | What it does |
|---------|--------------|
| `/code-review <path>` | Multi-pass code review (security, quality, performance, architecture) |
| `/security-audit <path>` | OWASP-aligned vulnerability scan with remediation plan |
| `/smart-test <path>` | Find test gaps and generate tests for uncovered code |
| `/fix-test --lf` | Auto-diagnose and fix failing tests with retry loop (up to 3 attempts) |
| `/bug-predict <path>` | Predict likely bug locations from patterns and complexity |
| `/doc-gen <path>` | Generate documentation from source code |

All commands default to the current working directory if no
path is provided.

## How It Works

Each command triggers a structured, multi-pass analysis skill.
For example, `/code-review` runs four passes (security,
quality, performance, architecture) and synthesizes findings
into a single report with scores, file references, and
prioritized fixes.

Skills are prompt-based -- they guide Claude through a
systematic analysis process. No external tools, APIs, or
package installations are needed.

## Example

```
/code-review src/
```

Produces a report like:

```
## Summary
Score: 82/100 | Files reviewed: 24 | Issues: 11

## Security
| Severity | File       | Line | Issue              | Fix           |
|----------|------------|------|--------------------|---------------|
| HIGH     | auth.py    | 45   | Missing input validation | Add schema check |
| MEDIUM   | config.py  | 12   | Hardcoded secret   | Use env var   |

## Top Priorities
1. Add input validation to auth.py:45
2. Move secrets to environment variables
3. Add error handling to db.py:88
```

## When to Use

- Before opening a PR -- run `/code-review` to catch issues
  early
- During security reviews -- run `/security-audit` for a
  structured vulnerability assessment
- When adding features -- run `/smart-test` to generate tests
  for new code
- When tests fail -- run `/fix-test --lf` to auto-diagnose and
  fix failures instead of manually reading each traceback
- Before releases -- run `/bug-predict` to find high-risk
  areas
- When onboarding -- run `/doc-gen` to generate documentation
  for unfamiliar code

## Troubleshooting

**Command not recognized:** Make sure the plugin is installed.
Run `/plugins` to verify attune-lite appears in the list.

**Review seems incomplete:** For large codebases, specify a
narrower path (e.g., `/code-review src/auth/` instead of
`/code-review .`).

## About

Attune Lite surfaces the best workflow patterns from
[attune-ai](https://pypi.org/project/attune-ai/) as native
Claude Code skills. For the full framework with 15 workflows,
CLI integration, and multi-agent orchestration:

```bash
pip install 'attune-ai[developer]'
```

## License

Apache-2.0
