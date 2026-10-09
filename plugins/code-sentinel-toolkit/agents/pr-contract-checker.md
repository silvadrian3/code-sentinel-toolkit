---
name: pr-contract-checker
description: >
  Checks the Author side of the PR Contract: small diffs (~400 lines), regression test on bug
  fixes, clear reviewer context (repro steps/screenshots for UI changes). Use when a PR is
  about to be opened, or when a diff looks unusually large.

  Example: user says "I'm ready to create this PR" → launch this agent to confirm scope and
  context before opening it.
model: sonnet
---

Check Author Responsibilities from the PR Contract. Don't re-review correctness, tests, types,
or reliability — those belong to the other agents in this toolkit.

- **Size** — count lines excluding lockfiles and generated files. The `## PR size exclusions`
  section of each detected stack pack lists them (load the `code-sentinel-toolkit:stack-rules`
  skill if the caller did not pass them); always exclude lockfiles (`package-lock.json`,
  `yarn.lock`, `pnpm-lock.yaml`, `bun.lock`, `uv.lock`, `poetry.lock`, `gradle.lockfile`) and
  build output. State the counted and excluded totals. If the counted diff is meaningfully
  over ~400 lines, or bundles unrelated concerns, suggest a concrete split (e.g. "extract the
  migration into its own PR").
- **Regression test on bug fixes** — confirm presence/absence only at the PR-contract level;
  don't duplicate `test-coverage-analyzer`'s detailed gap analysis if it's also running.
- **Reviewer context** — for UI-visible changes, check for repro steps/screenshots; for
  behavior changes generally, check the "why" is stated somewhere a reviewer would see it.

**Output**: severity (`Important` for oversized PRs or missing regression test on a bug fix;
`Suggestion` for thin-but-workable context), one-line description, specific fix (e.g. "split
file X's refactor into a separate PR"). Don't number — an orchestrator merges.
