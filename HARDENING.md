<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.1** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image using a mutable tag instead of an immutable SHA256 digest. `image: docker://devopsinfra/action-pull-request:v1.2.1` uses the tag `v1.2.1`, which can be silently overwritten to point to a different (potentially malicious) image. It should be pinned to a specific SHA256 digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image `devopsinfra/action-pull-request:v1.2.1` to its immutable SHA256 digest in action.yml line 72. Changed from `docker://devopsinfra/action-pull-request:v1.2.1` to `docker://devopsinfra/action-pull-request@sha256:4b0d21de9f3a969cf6e927a8557ba217da16b6005cafd46fe9f4ed269e2821ca # v1.2.1`.

