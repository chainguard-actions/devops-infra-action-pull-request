<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v0.5.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v0.5.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

All uses: references in the workflow files use mutable tag-based refs instead of pinned 40-character SHA commits, making the action vulnerable to supply-chain attacks if a tag is moved or hijacked. Failing references include: actions/checkout@v3, crazy-max/ghaction-github-labeler@v4.0.0, luke142367/Docker-Lint-Action@v1.1.1, brpaz/hadolint-action@v1.5.0, devops-infra/action-pull-request@v0.4.2. Additionally, action.yml uses a mutable Docker image tag (docker://devopsinfra/action-pull-request:v0.5.0) instead of a SHA digest.

Locations:

- `.github/workflows/CRON.yml:14`
- `.github/workflows/PUSH-MASTER.yml:13`
- `.github/workflows/PUSH-MASTER.yml:27`
- `.github/workflows/PUSH-MASTER.yml:38`
- `.github/workflows/PUSH-MASTER.yml:44`
- `.github/workflows/PUSH-MASTER.yml:55`
- `.github/workflows/PUSH-OTHER.yml:13`
- `.github/workflows/PUSH-OTHER.yml:27`
- `.github/workflows/PUSH-OTHER.yml:38`
- `.github/workflows/PUSH-OTHER.yml:44`
- `.github/workflows/PUSH-OTHER.yml:55`
- `action.yml:63`

### missing-permissions (severity: medium)

None of the workflow files define a top-level permissions: key, and no individual jobs define job-level permissions: blocks. Without explicit permissions, workflows run with the default (potentially broad) token permissions, violating the principle of least privilege.

Locations:

- `.github/workflows/CRON.yml:1`
- `.github/workflows/PUSH-MASTER.yml:1`
- `.github/workflows/PUSH-OTHER.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed all unpinned action references by resolving real commit SHAs via lookup_action_sha and lookup_container_digest. Pinned: actions/checkout@v3→SHA, crazy-max/ghaction-github-labeler@v4.0.0→SHA, luke142367/Docker-Lint-Action@v1.1.1→SHA, brpaz/hadolint-action@v1.5.0→SHA, devops-infra/action-pull-request@v0.4.2→SHA (6 occurrences in PUSH-OTHER.yml), and the Docker image in action.yml with its sha256 digest (preserving docker:// scheme and tag). Added top-level 'permissions: {}' to all three workflow files and minimal job-level permissions (contents: read for build/lint jobs, issues: write for label jobs, pull-requests: write for PR creation job).

