# SafeContext Windows downstream

This repository is `SafeContext/safecontext-windows`. Upstream is
`SafeContext/safecontext`. Read `CLAUDE.md` for the architecture and development
commands, and `SPEC.md` for the product's contracts and open decisions.

Track Windows work in this repository's pinned issue #1. Use one issue, branch,
and PR per task, with the existing PR template. Use `codex/issue-<n>-<description>`
for Codex-created branches. Target this repository for issues and PRs; do not
change upstream code, settings or issues as part of downstream work.

The copied `CLAUDE.md` describes upstream's macOS scope and branch settings;
it is not evidence of Windows compatibility or downstream branch protections.
Preserve upstream commit ancestry with normal merge commits for synchronization
PRs; ordinary feature PRs can use squash merging. A human decides when to merge.

## Code Review Rules

### Privacy boundaries

- Flag changes that expose raw prompts, tool text, restored sensitive values or
  device credentials through logs, errors, dashboard events or newly added
  network calls. Keep events metadata-only and local restoration within the
  approved tool/path boundaries. Preserve fail-closed behavior when required by
  the configured policy; report existing documented gaps separately from new
  regressions. A Windows workaround must not bypass enforcement or add a
  plaintext credential fallback.

### Windows compatibility

- Flag platform assumptions in changed runtime/setup paths: macOS-only commands,
  unquoted paths, drive letters, case differences, traversal or junction escapes,
  and secure credential storage. Use an appropriate platform implementation or
  an explicit unsupported/error path; do not silently fall back to weaker
  behavior. Windows support is under development, so assess the feature's stated
  acceptance criteria rather than treating all unfinished work as a regression.

### Shared behavior and contracts

- Preserve the schemas in `packages/policy`, hook input/output formats, pinned
  model verification and existing macOS behavior when changing shared code.
  Flag uncoordinated contract changes, weakened validation or checksum checks,
  and silent dependency/runtime changes that break existing clients. Prefer
  platform-specific adapters with shared policy/detection behavior. Keep lint
  and formatting checks in CI; give findings a concrete failure path and fix.

For review tasks, inspect and report findings; do not edit, commit, push or merge
code. Reviewer instructions guide analysis, while repository permissions, tests,
branch protections and human approval provide enforcement.
