<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.1.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.1.2** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a mutable Docker image tag (`docker://devopsinfra/action-pull-request:v1.1.2`) in `runs.image:` instead of a SHA digest. This is vulnerable to supply-chain attacks if the tag is moved to a different image. It should be pinned to a SHA digest (e.g., `docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`).

Locations:

- `action.yml:73`

### unpinned-uses (severity: high)

All 5 workflow files use mutable tag refs (`@v1`) for their `uses:` references instead of full 40-character commit SHA digests. Mutable tags can be silently moved to point to different (potentially malicious) commits, enabling supply-chain attacks. Affected references: `devops-infra/.github/.github/workflows/reusable-auto-pull-request-create.yml@v1`, `reusable-auto-release-create.yml@v1`, `reusable-cron-dependency-update.yml@v1`, `reusable-manual-release-branch-prepare.yml@v1`, `reusable-manual-release-create.yml@v1`.

Locations:

- `.github/workflows/auto-pull-request-create.yml:17`
- `.github/workflows/auto-release-create.yml:24`
- `.github/workflows/cron-dependency-update.yml:14`
- `.github/workflows/manual-release-branch-prepare.yml:31`
- `.github/workflows/manual-release-create.yml:31`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Fixed two unpinned-uses findings:
1. action.yml: Pinned Docker image from `docker://devopsinfra/action-pull-request:v1.1.2` to `docker://devopsinfra/action-pull-request:v1.1.2@sha256:0a2478172679bff88daf706e96152f64042d7a337212792ccde2ab49b115df0e`, preserving the docker:// scheme and tag inline.
2. All 5 workflow files: Pinned reusable workflow references from `@v1` to `@88b425df3a0f0415f12a0678b84d065562363bdc # v1` (the resolved SHA for devops-infra/.github at tag v1) in auto-pull-request-create.yml, auto-release-create.yml, cron-dependency-update.yml, manual-release-branch-prepare.yml, and manual-release-create.yml.

