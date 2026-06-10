<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.4** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml Docker image reference uses a mutable version tag (`v1.2.4`) instead of an immutable SHA digest. The line `image: docker://devopsinfra/action-pull-request:v1.2.4` can silently point to a different (potentially malicious) image if the tag is overwritten on the registry. It should be pinned to a specific SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest> # v1.2.4`.

Locations:

- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag reference `docker://devopsinfra/action-pull-request:v1.2.4` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:ccaf4738774d4ec25dae582e50fb5017ff8346993558b5448ac5e5ddf699c64e # v1.2.4` in action.yml line 76. The original tag is preserved as a comment for readability.

