# Hardening Report: devops-infra--action-pull-request/v1.1.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.1.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA256 digest. `image: docker://devopsinfra/action-pull-request:v1.1.1` can be silently replaced by a different image if the tag is force-pushed, enabling a supply-chain attack. It should be pinned to a full SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.1.1`.

Locations:

- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.1.1` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:1b35bda07ef9bcb21d92a1ccec45271f3f1f58db7449f77f62677e8019db6e04 # v1.1.1` in action.yml at line 76. The original tag is preserved as a comment for readability.

