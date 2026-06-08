# Hardening Report: devops-infra--action-pull-request/v1.2.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable tag instead of an immutable SHA digest. The reference `image: docker://devopsinfra/action-pull-request:v1.2.2` uses the tag `v1.2.2`, which can be silently overwritten on the registry, enabling a supply-chain attack. It should be pinned to a full SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.2.2`.

Locations:

- `action.yml:83`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.2.2` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:22c206837dab36be7f25e56497931ecd376df6d9535fc76c1fec3c6023e8df7a # v1.2.2` in action.yml at line 83. The original tag is preserved as a comment for readability.

