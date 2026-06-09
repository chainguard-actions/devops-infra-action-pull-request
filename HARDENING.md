# Hardening Report: devops-infra--action-pull-request/v1.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA digest. The image `docker://devopsinfra/action-pull-request:v1.2.0` is pinned to the tag `v1.2.0`, which can be overwritten at any time on the registry, exposing the action to supply-chain attacks. It should be replaced with a SHA256 digest reference, e.g. `docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.2.0` with the immutable SHA256 digest reference `docker://devopsinfra/action-pull-request@sha256:45bbe273ec096dd9b2f657d0cdb34ec3fb58999070a3aac5bed032f2b10e210d # v1.2.0` in action.yml at line 76. The tag is preserved as a comment for readability.

