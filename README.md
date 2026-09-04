# code-sentinel-toolkit

Claude Code plugin marketplace for **code-sentinel-toolkit**: pre-flight PR review agents that
enforce a team's Code Review & Testing Standards — silent-failure detection, test coverage,
type safety, state/sync integrity, naming conventions, and PR scope/context — with a
lightweight single-pass agent for small diffs, so review depth scales with risk instead of
taxing every PR with the full lineup.

## Install

```
claude plugin marketplace add silvadrian3/code-sentinel-toolkit
claude plugin install code-sentinel-toolkit
```

## Use

```
/code-sentinel-toolkit:review-pr
```

Picks **Lite** (one consolidated pass) for small, routine diffs, or **Full** (the applicable
specialist agents) for large or sensitive ones — auth, payments, migrations. Force it with
`--full`. Individual agents (`code-reviewer`, `silent-failure-hunter`, `test-coverage-analyzer`,
`type-design-reviewer`, `state-sync-guardian`, `pr-contract-checker`, `quick-reviewer`) also
trigger automatically based on what you're asking about.

See [`plugins/code-sentinel-toolkit/README.md`](plugins/code-sentinel-toolkit/README.md) for
per-agent coverage, the report format, and `.sentinel-rules.md` setup for stack-specific rules.
