<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files reference reusable workflows using mutable tags or branch names instead of full 40-character SHA digests, making them vulnerable to supply-chain attacks if the referenced repository is compromised or the tag is moved. Additionally, action.yml uses a Docker image with a mutable tag (v1.2.5) instead of a SHA digest.

Failing references:
- auto-pull-request-create.yml: `uses: devops-infra/.github/.github/workflows/reusable-auto-pull-request-create.yml@v1`
- auto-release-create.yml: `uses: devops-infra/.github/.github/workflows/reusable-auto-release-create.yml@v1`
- cron-dependency-update.yml: `uses: devops-infra/.github/.github/workflows/reusable-cron-dependency-update.yml@v1`
- manual-e2e-validate.yml: `uses: devops-infra/triglav/.github/workflows/e2e-action-pull-request.yml@master`
- manual-release-branch-prepare.yml: `uses: devops-infra/.github/.github/workflows/reusable-manual-release-branch-prepare.yml@v1`
- manual-release-create.yml: `uses: devops-infra/.github/.github/workflows/reusable-manual-release-create.yml@v1`
- action.yml: `image: docker://devopsinfra/action-pull-request:v1.2.5` (mutable tag, not a SHA digest)

Locations:

- `.github/workflows/auto-pull-request-create.yml:17`
- `.github/workflows/auto-release-create.yml:27`
- `.github/workflows/cron-dependency-update.yml:14`
- `.github/workflows/manual-e2e-validate.yml:22`
- `.github/workflows/manual-release-branch-prepare.yml:27`
- `.github/workflows/manual-release-create.yml:26`
- `action.yml:79`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Fixed all 7 unpinned references:
1. .github/workflows/auto-pull-request-create.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
2. .github/workflows/auto-release-create.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
3. .github/workflows/cron-dependency-update.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
4. .github/workflows/manual-e2e-validate.yml: pinned devops-infra/triglav reusable workflow @master → @6b7cf10d8042334e484bdc14ea1c9b4b335cea3e # master
5. .github/workflows/manual-release-branch-prepare.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
6. .github/workflows/manual-release-create.yml: pinned devops-infra/.github reusable workflow @v1 → @88b425df3a0f0415f12a0678b84d065562363bdc # v1
7. action.yml: pinned Docker image docker://devopsinfra/action-pull-request:v1.2.5 with SHA digest @sha256:fa2ca207ac54ab739a1cc977625b15033032a2127c1e4b89b75b2c46c9d1688e, preserving docker:// scheme and :v1.2.5 tag inline

