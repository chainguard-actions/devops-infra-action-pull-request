<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.2.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All workflow files reference reusable workflows using mutable tags (@v1 or @master) instead of full 40-character commit SHAs. This exposes the action to supply-chain attacks where a tag can be silently moved to point to malicious code. Additionally, action.yml references the Docker image `docker://devopsinfra/action-pull-request:v1.2.1` using a mutable version tag instead of an immutable SHA digest (e.g., `@sha256:<digest>`). Failing references: auto-pull-request-create.yml uses `devops-infra/.github/.github/workflows/reusable-auto-pull-request-create.yml@v1`; auto-release-create.yml uses `devops-infra/.github/.github/workflows/reusable-auto-release-create.yml@v1`; cron-dependency-update.yml uses `devops-infra/.github/.github/workflows/reusable-cron-dependency-update.yml@v1`; manual-e2e-validate.yml uses `devops-infra/triglav/.github/workflows/e2e-action-pull-request.yml@master`; manual-release-branch-prepare.yml uses `devops-infra/.github/.github/workflows/reusable-manual-release-branch-prepare.yml@v1`; manual-release-create.yml uses `devops-infra/.github/.github/workflows/reusable-manual-release-create.yml@v1`; action.yml image: `docker://devopsinfra/action-pull-request:v1.2.1`.

Locations:

- `.github/workflows/auto-pull-request-create.yml:14`
- `.github/workflows/auto-release-create.yml:24`
- `.github/workflows/cron-dependency-update.yml:14`
- `.github/workflows/manual-e2e-validate.yml:22`
- `.github/workflows/manual-release-branch-prepare.yml:26`
- `.github/workflows/manual-release-create.yml:26`
- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Fixed all 7 unpinned references:
1. auto-pull-request-create.yml: devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
2. auto-release-create.yml: devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
3. cron-dependency-update.yml: devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
4. manual-e2e-validate.yml: devops-infra/triglav workflow @master → @6b7cf10d8042334e484bdc14ea1c9b4b335cea3e # master
5. manual-release-branch-prepare.yml: devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
6. manual-release-create.yml: devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
7. action.yml: Docker image pinned to docker://devopsinfra/action-pull-request:v1.2.1@sha256:4b0d21de9f3a969cf6e927a8557ba217da16b6005cafd46fe9f4ed269e2821ca (docker:// scheme and tag preserved inline)

