<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.1.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.1.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image using a mutable version tag instead of an immutable SHA digest. The reference `image: docker://devopsinfra/action-pull-request:v1.1.3` uses the tag `v1.1.3`, which can be silently updated or replaced by the image owner, enabling supply-chain attacks. It should be pinned to a specific SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from `docker://devopsinfra/action-pull-request:v1.1.3` to `docker://devopsinfra/action-pull-request:v1.1.3@sha256:6c6b319b2aa16d1cd488d71b6147769bd3f17fd307baf39e2a4fc252497c7e92`. The docker:// scheme and tag are preserved inline, with the immutable digest appended to prevent supply-chain attacks via mutable tags.

