# AltSecCon OIDC demo (safe)

This repository demonstrates a GitHub Actions trust boundary without
exposing or replaying any OIDC JWT.

- `remediated-ci.yml` runs tests for pull requests with read-only contents
  permission and no `id-token: write`.
- `remediated-deploy.yml` runs only after a successful push workflow from
  this repository's default branch. It requests a real OIDC token inside
  the trusted job and prints only selected identity claims. It never logs,
  stores, transmits, or exchanges the token.
- `vulnerable-ci.yml` is a non-runnable reference. It does not check out
  fork code or grant OIDC permissions.

Do not add cloud credentials or relax the workflow gates for this demo.
