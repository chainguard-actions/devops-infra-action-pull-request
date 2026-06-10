<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.2** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image using a mutable tag (`v1.2.2`) instead of an immutable SHA digest. This means the image could be replaced with a different (potentially malicious) version without changing the reference. The failing reference is: `image: docker://devopsinfra/action-pull-request:v1.2.2`. It should be pinned to a SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:80`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.2.2` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:22c206837dab36be7f25e56497931ecd376df6d9535fc76c1fec3c6023e8df7a # v1.2.2` in action.yml at line 80.

