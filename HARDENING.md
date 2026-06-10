<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.1.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.1.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml runs.image field references a Docker image using a mutable tag (v1.1.2) instead of an immutable SHA digest. This means the image could be replaced with a different (potentially malicious) version without changing the action reference, creating a supply-chain attack vector. The failing reference is: `image: docker://devopsinfra/action-pull-request:v1.1.2`. It should be pinned to a SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:68`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.1.2` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:0a2478172679bff88daf706e96152f64042d7a337212792ccde2ab49b115df0e # v1.1.2` in action.yml line 68.

