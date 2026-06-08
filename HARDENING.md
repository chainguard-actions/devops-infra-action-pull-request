# Hardening Report: devops-infra--action-pull-request/v1.2.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `ff50f15e4b79bfbf764dafdfd2579175a6ea9771`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA digest. `image: docker://devopsinfra/action-pull-request:v1.2.3` uses the tag `v1.2.3`, which can be silently replaced with a different (potentially malicious) image. It should be pinned to a specific SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from `docker://devopsinfra/action-pull-request:v1.2.3` to `docker://devopsinfra/action-pull-request@sha256:c7a688e89a7ceee1736076df615029cd4656282b28779fda8e3b6b621f219cb0 # v1.2.3`. The SHA digest was resolved via the Docker Registry API to ensure it is accurate and immutable.

