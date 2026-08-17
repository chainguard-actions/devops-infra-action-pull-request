<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.5

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.2.5** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All workflow files reference reusable workflows using mutable tags (@v1 or @master) instead of full 40-character SHA commit hashes. This exposes the action to supply-chain attacks where a tag can be silently moved to point to malicious code. Affected references:
- auto-pull-request-create.yml: devops-infra/.github/.github/workflows/reusable-auto-pull-request-create.yml@v1
- auto-release-create.yml: devops-infra/.github/.github/workflows/reusable-auto-release-create.yml@v1
- cron-dependency-update.yml: devops-infra/.github/.github/workflows/reusable-cron-dependency-update.yml@v1
- manual-e2e-validate.yml: devops-infra/triglav/.github/workflows/e2e-action-pull-request.yml@master
- manual-release-branch-prepare.yml: devops-infra/.github/.github/workflows/reusable-manual-release-branch-prepare.yml@v1
- manual-release-create.yml: devops-infra/.github/.github/workflows/reusable-manual-release-create.yml@v1
All should be pinned to a full 40-character hex SHA, e.g. uses: owner/repo/.github/workflows/file.yml@<40-char-sha> # v1

Locations:

- `.github/workflows/auto-pull-request-create.yml:16`
- `.github/workflows/auto-release-create.yml:28`
- `.github/workflows/cron-dependency-update.yml:14`
- `.github/workflows/manual-e2e-validate.yml:25`
- `.github/workflows/manual-release-branch-prepare.yml:30`
- `.github/workflows/manual-release-create.yml:28`

### unpinned-uses (severity: high)

The action.yml Docker image reference uses a mutable version tag (v1.2.5) instead of an immutable SHA digest. The image `docker://devopsinfra/action-pull-request:v1.2.5` can be overwritten on the registry to point to a different (potentially malicious) image without changing the tag. It should be pinned to a SHA digest, e.g. `image: devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.2.5`.

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Fixed all 7 unpinned references:
1. auto-pull-request-create.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
2. auto-release-create.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
3. cron-dependency-update.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
4. manual-e2e-validate.yml: pinned devops-infra/triglav reusable workflow @master → @6b7cf10d8042334e484bdc14ea1c9b4b335cea3e # master
5. manual-release-branch-prepare.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
6. manual-release-create.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
7. action.yml: pinned Docker image docker://devopsinfra/action-pull-request:v1.2.5 → docker://devopsinfra/action-pull-request:v1.2.5@sha256:fa2ca207ac54ab739a1cc977625b15033032a2127c1e4b89b75b2c46c9d1688e (preserving docker:// scheme and tag inline)

