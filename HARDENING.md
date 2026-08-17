<!-- markdownlint-disable -->

# Hardening Report: devops-infra--action-pull-request/v1.2.4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **devops-infra--action-pull-request/v1.2.4** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The action.yml references a Docker image using a mutable version tag (`docker://devopsinfra/action-pull-request:v1.2.4`) instead of an immutable SHA digest. This means the image could be replaced with a different (potentially malicious) version without changing the action configuration, creating a supply-chain risk. It should be pinned to a specific SHA digest, e.g. `docker://devopsinfra/action-pull-request@sha256:<64-hex-char-digest>`.

Locations:

- `action.yml:76`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned the Docker image reference in action.yml from `docker://devopsinfra/action-pull-request:v1.2.4` to `docker://devopsinfra/action-pull-request:v1.2.4@sha256:ccaf4738774d4ec25dae582e50fb5017ff8346993558b5448ac5e5ddf699c64e`. The docker:// scheme and version tag are preserved inline, with the immutable SHA digest appended to prevent supply-chain attacks.

