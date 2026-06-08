# Hardening Report: devops-infra--action-pull-request/v1.1.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.1.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA digest. The reference `image: docker://devopsinfra/action-pull-request:v1.1.2` uses the tag `v1.1.2`, which can be changed at any time by the image owner, enabling supply-chain attacks. It should be replaced with a SHA256 digest reference, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`

Locations:

- `action.yml:63`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag reference `docker://devopsinfra/action-pull-request:v1.1.2` with the immutable SHA256 digest reference `docker://devopsinfra/action-pull-request@sha256:0a2478172679bff88daf706e96152f64042d7a337212792ccde2ab49b115df0e # v1.1.2` in action.yml line 63. The digest was resolved using the Docker Registry HTTP API v2.

