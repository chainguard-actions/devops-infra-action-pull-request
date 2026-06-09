# Hardening Report: devops-infra--action-pull-request/v1.2.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.4** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image referenced by a mutable version tag (`docker://devopsinfra/action-pull-request:v1.2.4`) instead of an immutable SHA digest. This means the image content could change without notice, enabling a supply-chain attack. It should be pinned to a full SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.2.4`.

Locations:

- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.2.4` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:ccaf4738774d4ec25dae582e50fb5017ff8346993558b5448ac5e5ddf699c64e # v1.2.4` in action.yml at line 76.

