# Hardening Report: devops-infra--action-pull-request/v1.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA digest. `image: docker://devopsinfra/action-pull-request:v1.2.5` uses the tag `v1.2.5`, which can be changed at any time by the image owner, exposing the action to supply-chain attacks. It should be pinned to a specific SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.2.5`.

Locations:

- `action.yml:90`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from the mutable tag `devopsinfra/action-pull-request:v1.2.5` to the immutable digest `devopsinfra/action-pull-request@sha256:fa2ca207ac54ab739a1cc977625b15033032a2127c1e4b89b75b2c46c9d1688e # v1.2.5`. The original tag is preserved as a comment for readability.

