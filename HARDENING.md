# Hardening Report: devops-infra--action-pull-request/v1.1.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.1.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image referenced by a mutable version tag (`v1.1.3`) instead of an immutable SHA digest. This means the image could be replaced with a different (potentially malicious) version without changing the action reference. The failing reference is: `image: docker://devopsinfra/action-pull-request:v1.1.3`. It should be replaced with a SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:68`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag reference `docker://devopsinfra/action-pull-request:v1.1.3` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:6c6b319b2aa16d1cd488d71b6147769bd3f17fd307baf39e2a4fc252497c7e92 # v1.1.3` in action.yml at line 68. The original tag is preserved as a comment for readability.

