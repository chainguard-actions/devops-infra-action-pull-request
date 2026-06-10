<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.1.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.1.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable tag instead of an immutable SHA digest. `image: docker://devopsinfra/action-pull-request:v1.1.3` uses the tag `v1.1.3`, which can be silently overwritten to point to different (potentially malicious) code, enabling a supply-chain attack. It should be pinned to a full SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.1.3`.

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `devopsinfra/action-pull-request:v1.1.3` with the immutable SHA256 digest `devopsinfra/action-pull-request@sha256:6c6b319b2aa16d1cd488d71b6147769bd3f17fd307baf39e2a4fc252497c7e92 # v1.1.3` in action.yml line 72. The digest was resolved via the Docker Registry API.

