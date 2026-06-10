<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.3

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.3** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml uses a Docker image reference with a mutable version tag instead of an immutable SHA digest. `image: docker://devopsinfra/action-pull-request:v1.2.3` uses the tag `v1.2.3`, which can be silently overwritten on the registry, enabling supply-chain attacks. It should be pinned to a specific SHA digest, e.g. `image: docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `devopsinfra/action-pull-request:v1.2.3` with the immutable SHA256 digest `devopsinfra/action-pull-request@sha256:c7a688e89a7ceee1736076df615029cd4656282b28779fda8e3b6b621f219cb0 # v1.2.3` in action.yml at line 76. The original tag is preserved as a comment for readability.

