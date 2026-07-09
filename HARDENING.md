<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v0.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v0.5.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Multiple workflow files and action.yml use unpinned (tag-based) references instead of full 40-character SHA commit digests. This exposes the action to supply-chain attacks if the referenced tag is moved or the image is replaced. Affected references include: actions/checkout@v3, crazy-max/ghaction-github-labeler@v4.0.0, luke142367/Docker-Lint-Action@v1.1.1, brpaz/hadolint-action@v1.5.0, devops-infra/action-pull-request@v0.4.2 (in workflow files), and docker://devopsinfra/action-pull-request:v0.5.0 (in action.yml runs.image — uses a mutable tag instead of a SHA digest).

Locations:

- `.github/workflows/CRON.yml:14`
- `.github/workflows/PUSH-MASTER.yml:12`
- `.github/workflows/PUSH-MASTER.yml:27`
- `.github/workflows/PUSH-MASTER.yml:35`
- `.github/workflows/PUSH-MASTER.yml:40`
- `.github/workflows/PUSH-MASTER.yml:46`
- `.github/workflows/PUSH-OTHER.yml:13`
- `.github/workflows/PUSH-OTHER.yml:28`
- `.github/workflows/PUSH-OTHER.yml:36`
- `.github/workflows/PUSH-OTHER.yml:41`
- `.github/workflows/PUSH-OTHER.yml:47`
- `.github/workflows/PUSH-OTHER.yml:55`
- `action.yml:62`

### missing-permissions (severity: medium)

None of the workflow files define a top-level 'permissions:' key, and no individual jobs define job-level 'permissions:' keys. Without explicit permissions, workflows run with the default (potentially broad) token permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/CRON.yml:1`
- `.github/workflows/PUSH-MASTER.yml:1`
- `.github/workflows/PUSH-OTHER.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all unpinned action references by resolving them to full 40-character SHA commit digests using lookup_action_sha and lookup_container_digest. Added top-level 'permissions: {}' to all three workflow files and job-level minimal permissions (contents: read, issues: write for label jobs, pull-requests: write for PR creation job). The docker image in action.yml was pinned to its sha256 digest.

