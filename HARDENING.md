<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.1.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.1.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image using a mutable version tag instead of an immutable SHA digest. `image: docker://devopsinfra/action-pull-request:v1.1.1` uses the tag `v1.1.1`, which can be silently overwritten on Docker Hub, enabling a supply-chain attack. It should be pinned to a specific SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.1.1`.

Locations:

- `action.yml:68`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.1.1` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:1b35bda07ef9bcb21d92a1ccec45271f3f1f58db7449f77f62677e8019db6e04 # v1.1.1` in action.yml line 68. The digest was resolved via the Docker Registry HTTP API v2.

