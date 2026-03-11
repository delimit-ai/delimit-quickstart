# Delimit Quickstart

Detect breaking API changes in CI.

---

## The Problem

API changes can silently break clients. A developer removes an endpoint, renames a field, or changes a type — and downstream consumers discover it in production.

Delimit catches these changes automatically on every push and pull request.

## Example

This repo contains two OpenAPI specs:

**v1** (`openapi-v1.yaml`) — includes the endpoint:

```
GET /users/{id}
```

**v2** (`openapi-v2.yaml`) — the endpoint is removed.

Removing an endpoint is a breaking change. Any client calling `GET /users/{id}` will get a 404 after this change ships.

## Run the Demo

Push to this repo or open a pull request. The GitHub Action runs Delimit automatically and produces:

```
FAIL — Breaking change detected

Removed endpoint:
  GET /users/{id}
```

CI fails because a breaking change was detected.

## Why This Matters

Breaking API changes cost hours of debugging, broken integrations, and customer trust. Delimit prevents breaking changes from reaching production by detecting compatibility violations before release — automatically, on every PR.

## Use Delimit in Your Own Repo

Install the GitHub Action in your repository:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    old_spec: path/to/old-spec.yaml
    new_spec: path/to/new-spec.yaml
```

Learn more: [github.com/delimit-ai/delimit](https://github.com/delimit-ai/delimit)
