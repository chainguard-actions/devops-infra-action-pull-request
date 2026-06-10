<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.1.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.1.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image by mutable tag rather than an immutable SHA digest. The image `docker://devopsinfra/action-pull-request:v1.1.3` uses the tag `v1.1.3`, which can be silently replaced with different (potentially malicious) content at any time. It should be pinned to a specific SHA256 digest, e.g. `image: devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.1.3`.

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from the mutable tag `docker://devopsinfra/action-pull-request:v1.1.3` to the immutable digest `docker://devopsinfra/action-pull-request@sha256:6c6b319b2aa16d1cd488d71b6147769bd3f17fd307baf39e2a4fc252497c7e92 # v1.1.3`. The tag is preserved as a comment for readability.

