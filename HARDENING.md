# Hardening Report: devops-infra--action-pull-request/v1.2.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA digest. `image: docker://devopsinfra/action-pull-request:v1.2.1` uses the tag `v1.2.1`, which can be silently replaced or overwritten on the registry, enabling a supply-chain attack. It should be pinned to a full SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.2.1`.

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced mutable Docker image tag `devopsinfra/action-pull-request:v1.2.1` with immutable SHA256 digest `devopsinfra/action-pull-request@sha256:4b0d21de9f3a969cf6e927a8557ba217da16b6005cafd46fe9f4ed269e2821ca # v1.2.1` in action.yml at line 72. The original tag is preserved as a comment for readability.

