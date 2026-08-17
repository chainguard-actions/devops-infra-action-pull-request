<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.1.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.1.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

action.yml uses a Docker image referenced by a mutable tag (`docker://devopsinfra/action-pull-request:v1.1.1`) instead of an immutable SHA digest. This means the image content can change without notice, enabling supply-chain attacks. It should be pinned to a SHA digest, e.g. `docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:68`

### unpinned-uses (severity: high)

All three workflow files reference reusable workflows using the mutable `@v1` tag instead of a full 40-character commit SHA. This allows the referenced workflow content to change without notice, enabling supply-chain attacks. Affected references: `devops-infra/.github/.github/workflows/reusable-auto-pull-request-create.yml@v1`, `devops-infra/.github/.github/workflows/reusable-cron-dependency-update.yml@v1`, `devops-infra/.github/.github/workflows/reusable-manual-release-create.yml@v1`.

Locations:

- `.github/workflows/auto-pull-request-create.yml:14`
- `.github/workflows/cron-dependency-update.yml:13`
- `.github/workflows/manual-release-create.yml:28`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Fixed all unpinned-uses findings:
1. action.yml (line 68): Pinned Docker image from `docker://devopsinfra/action-pull-request:v1.1.1` to `docker://devopsinfra/action-pull-request:v1.1.1@sha256:1b35bda07ef9bcb21d92a1ccec45271f3f1f58db7449f77f62677e8019db6e04` (preserved docker:// scheme and tag inline).
2. .github/workflows/auto-pull-request-create.yml (line 14): Pinned reusable workflow from `@v1` to `@88b425df3a0f0415f12a0678b84d065562363bdc # v1`.
3. .github/workflows/cron-dependency-update.yml (line 13): Pinned reusable workflow from `@v1` to `@88b425df3a0f0415f12a0678b84d065562363bdc # v1`.
4. .github/workflows/manual-release-create.yml (line 28): Pinned reusable workflow from `@v1` to `@88b425df3a0f0415f12a0678b84d065562363bdc # v1`.
All SHAs were resolved via lookup tools.

