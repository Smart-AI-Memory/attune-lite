# Attune Lite (Deprecated)

> **This plugin has been deprecated.** All skills are now
> included in
> [attune-ai](https://github.com/Smart-AI-Memory/attune-ai),
> which offers 11 auto-triggering skills, MCP integration,
> security hooks, and the `/attune` hub command.

## Migrate to attune-ai

**Step 1:** Remove attune-lite:

```bash
claude plugin uninstall attune-lite
```

**Step 2:** Add attune-ai marketplace:

```bash
claude plugin marketplace add Smart-AI-Memory/attune-ai
```

**Step 3:** Install attune-ai:

```bash
claude plugin install attune-ai@attune-ai
```

## What Changed

All 6 attune-lite commands are now skills in attune-ai:

| attune-lite | attune-ai skill |
|-------------|-----------------|
| `/code-review` | `code-quality` (auto-triggered) |
| `/security-audit` | `security-audit` (auto-triggered) |
| `/smart-test` | `smart-test` (auto-triggered) |
| `/fix-test` | `fix-test` (auto-triggered) |
| `/bug-predict` | `bug-predict` (auto-triggered) |
| `/doc-gen` | `doc-gen` (auto-triggered) |

attune-ai adds 5 more skills (`planning`, `refactor-plan`,
`release-prep`, `memory-and-context`,
`workflow-orchestration`), plus the `/attune` hub command,
`/spec` spec-driven development, security hooks, and full
MCP server integration.

## License

Apache-2.0
