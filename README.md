# Delimit Quickstart

**Catch breaking API changes before they reach production.**

[![CI](https://github.com/delimit-ai/delimit-quickstart/actions/workflows/delimit.yml/badge.svg)](https://github.com/delimit-ai/delimit-quickstart/actions/workflows/delimit.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

This repo demonstrates Delimit detecting a breaking API change in CI. Fork it, push, and see CI fail in under 5 minutes.

---

## The Problem

A developer removes an endpoint, renames a field, or changes a response type. The change passes code review because nobody checked the API spec. Downstream clients break in production.

Delimit runs in CI and catches these changes before they ship.

## What This Repo Demonstrates

Two OpenAPI specs are checked in:

**v1** (`openapi-v1.yaml`):
```
GET /users/{id}    # Returns a user by ID
```

**v2** (`openapi-v2.yaml`):
```
# Endpoint removed
```

Removing an endpoint is a breaking change. Any client calling `GET /users/{id}` will get a 404.

## Expected Result

When CI runs, Delimit detects the breaking change and fails the build:

```
Error: Endpoint /users/{id} cannot be removed. Deprecate it first.

Process completed with exit code 1.
```

[See the actual failing run.](https://github.com/delimit-ai/delimit-quickstart/actions)

## How to Fix the Breaking Change

To make CI pass, you would keep the endpoint in `openapi-v2.yaml` and mark it as deprecated instead of removing it:

```yaml
paths:
  /users/{id}:
    get:
      summary: Get a user by ID
      deprecated: true
```

Delimit allows deprecated endpoints. It blocks removals.

## Why This Matters

Breaking API changes cause silent failures, broken integrations, and production incidents. Delimit detects compatibility violations on every push and pull request — before they reach production.

## Use Delimit in Your Own Repo

Add the GitHub Action to any repository with OpenAPI specs:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    old_spec: path/to/old-spec.yaml
    new_spec: path/to/new-spec.yaml
```

Or install the CLI:

```
npx delimit-cli init
```

## Next Step

1. **Fork this repo** and see Delimit catch the breaking change in your own CI
2. **Add Delimit to your project** — copy the [workflow file](.github/workflows/delimit.yml) and point it at your specs
3. **Learn more** at [github.com/delimit-ai/delimit](https://github.com/delimit-ai/delimit)

---

[Delimit](https://github.com/delimit-ai/delimit) | [GitHub Action](https://github.com/delimit-ai/delimit-action) | [npm](https://www.npmjs.com/package/delimit-cli)
