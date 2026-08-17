<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.2.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files use `uses:` references pinned to mutable tags or branch names instead of immutable 40-character commit SHAs. Additionally, action.yml references a Docker image by mutable tag rather than a SHA digest. Mutable refs can be silently updated to point to malicious code.

Workflow unpinned refs:
- auto-pull-request-create.yml: `uses: devops-infra/.github/.github/workflows/reusable-auto-pull-request-create.yml@v1`
- auto-release-create.yml: `uses: devops-infra/.github/.github/workflows/reusable-auto-release-create.yml@v1`
- cron-dependency-update.yml: `uses: devops-infra/.github/.github/workflows/reusable-cron-dependency-update.yml@v1`
- manual-e2e-validate.yml: `uses: devops-infra/triglav/.github/workflows/e2e-action-pull-request.yml@master`
- manual-release-branch-prepare.yml: `uses: devops-infra/.github/.github/workflows/reusable-manual-release-branch-prepare.yml@v1`
- manual-release-create.yml: `uses: devops-infra/.github/.github/workflows/reusable-manual-release-create.yml@v1`

Docker image unpinned ref in action.yml:
- `image: docker://devopsinfra/action-pull-request:v1.2.3` (tag, not a SHA digest)

Locations:

- `.github/workflows/auto-pull-request-create.yml:14`
- `.github/workflows/auto-release-create.yml:28`
- `.github/workflows/cron-dependency-update.yml:13`
- `.github/workflows/manual-e2e-validate.yml:22`
- `.github/workflows/manual-release-branch-prepare.yml:27`
- `.github/workflows/manual-release-create.yml:26`
- `action.yml:75`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Fixed all 7 unpinned references:
1. action.yml: Pinned Docker image `devopsinfra/action-pull-request:v1.2.3` to SHA digest `sha256:c7a688e89a7ceee1736076df615029cd4656282b28779fda8e3b6b621f219cb0`, preserving the `docker://` scheme.
2. auto-pull-request-create.yml: Pinned `devops-infra/.github/...@v1` → `@88b425df3a0f0415f12a0678b84d065562363bdc # v1`
3. auto-release-create.yml: Same SHA for devops-infra/.github@v1
4. cron-dependency-update.yml: Same SHA for devops-infra/.github@v1
5. manual-e2e-validate.yml: Pinned `devops-infra/triglav/...@master` → `@6b7cf10d8042334e484bdc14ea1c9b4b335cea3e # master`
6. manual-release-branch-prepare.yml: Same SHA for devops-infra/.github@v1
7. manual-release-create.yml: Same SHA for devops-infra/.github@v1
All SHAs were resolved via lookup_action_sha and lookup_container_digest.

