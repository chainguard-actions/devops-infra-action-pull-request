<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.4.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.4.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image using a mutable tag (`v1.4.0`) instead of an immutable SHA digest. This means the image could be silently replaced with a malicious version without any change to the action configuration, enabling a supply-chain attack. The failing reference is: `image: docker://devopsinfra/action-pull-request:v1.4.0`. It should be pinned to a SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.4.0`.

Locations:

- `action.yml:88`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.4.0` with the immutable SHA digest `docker://devopsinfra/action-pull-request@sha256:0b9b65d3ef022278175eb1036714abee203a3b22c33859f2f2dbdf866afcab34 # v1.4.0` in hardened/action/action.yml line 88.

