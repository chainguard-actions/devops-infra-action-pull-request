<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `1`

Action **devops-infra--action-pull-request/v1.2.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action's Docker image reference uses a mutable version tag (`v1.2.0`) instead of an immutable SHA digest. If the image at this tag is replaced (e.g., via a supply-chain attack or accidental overwrite), the action will silently execute different code. The reference `docker://devopsinfra/action-pull-request:v1.2.0` should be replaced with a pinned digest such as `docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:72`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Replaced the mutable Docker image tag `docker://devopsinfra/action-pull-request:v1.2.0` with the immutable SHA256 digest `docker://devopsinfra/action-pull-request@sha256:45bbe273ec096dd9b2f657d0cdb34ec3fb58999070a3aac5bed032f2b10e210d # v1.2.0` in action.yml at line 72.

