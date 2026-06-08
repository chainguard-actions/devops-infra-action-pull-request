# Hardening Report: devops-infra--action-pull-request/v1.2.5

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.5** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA256 digest. The reference `docker://devopsinfra/action-pull-request:v1.2.5` can be silently replaced by a different image if the tag is overwritten on the registry, enabling a supply-chain attack. It should be pinned to a specific SHA256 digest, e.g. `docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.2.5`.

Locations:

- `action.yml:79`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from the mutable tag `devopsinfra/action-pull-request:v1.2.5` to the immutable SHA256 digest `devopsinfra/action-pull-request@sha256:fa2ca207ac54ab739a1cc977625b15033032a2127c1e4b89b75b2c46c9d1688e # v1.2.5`. The digest was resolved via the Docker Registry HTTP API v2.

