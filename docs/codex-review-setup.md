# Codex review for the Windows fork

Tracking issue: https://github.com/SafeContext/safecontext-windows/issues/3.

## Setup status

Repository guidance is prepared in `AGENTS.md`. GitHub's native Codex review
connection must be configured and verified before review is considered active.
The inherited Claude reviewer is not our selected reviewer and must remain
inactive in this fork. Do not copy upstream OAuth tokens or API credentials.

## Native review setup

1. Sign in to ChatGPT with the account that will run reviews.
2. Connect GitHub, granting access to `SafeContext/safecontext-windows` only where
   the integration supports repository selection. Inspect the actual permission
   request before approving; organization approval may also be required.
3. In https://chatgpt.com/settings/code-review, select the Windows repository and
   enable code review. Configure automatic review on PR open for this repository
   rather than changing global preferences for unrelated repositories.
4. Leave credit overage disabled unless separately requested. Account plan/access
   and remaining review capacity must be checked in the actual account settings.
5. Open a representative PR and request `@codex review`. Verify a completed review
   on the intended revision. A successful connection alone is not review proof.

The native integration does not require replacing Claude's GitHub Action with an
API-billed custom action. It follows applicable `AGENTS.md` guidance and can
review PRs automatically or through the manual mention above. A GitHub account
connection may grant permissions beyond posting review comments; inspect the
actual GitHub installation/authorization page rather than assuming read-only
credentials. Review instructions do not technically restrict integration access.

## Review workflow

Issue -> branch -> implementation and tests -> PR -> Codex review -> fixes ->
human review and merge. Request another review after relevant fixes if needed.
Codex findings complement tests and human review. The issue/PR format is retained
from upstream, while this fork uses its own reviewer account and configuration.

The product still integrates with Claude Code. Choosing Codex as the reviewer
does not add product support for protecting Codex traffic.

## Official references

- https://learn.chatgpt.com/docs/third-party/github
- https://developers.openai.com/blog/custom-code-review-rules-for-codex
