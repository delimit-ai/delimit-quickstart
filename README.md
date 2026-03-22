# delimit-quickstart

Fork this repo, push a breaking API change, and see Delimit catch it in CI.

## What's in the box

- `openapi.yaml` — a Pet Store API with 4 endpoints
- `openapi-changed.yaml` — the same spec with 5 breaking changes:
  - `GET /pets/{petId}` removed
  - `DELETE /pets/{petId}` removed
  - `Pet.id` type changed from `string` to `integer`
  - `Pet.tag` field removed
  - `Pet.status` enum value `pending` removed
- `.github/workflows/delimit.yml` — runs the Delimit action on every push/PR

## Try it

1. Fork this repo
2. Push any commit (or trigger Actions manually)
3. On a PR, Delimit posts a comment like this:

> **Breaking API Changes Detected**
>
> | Severity | Change | Location |
> |----------|--------|----------|
> | Critical | Endpoint removed | `/pets/{petId}` |
> | Warning | Type changed (string → integer) | `Pet.id` |
> | Warning | Enum value removed | `Pet.status` |
>
> **Semver: MAJOR** — 5 breaking changes, migration guide included

4. In enforce mode, CI fails until the breaking changes are resolved

## Use Delimit in your own repo

The simplest setup — auto-detects the base branch and diffs your spec:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    spec: api/openapi.yaml
```

Or compare two specific files:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    old_spec: openapi.yaml
    new_spec: openapi-changed.yaml
    mode: enforce
```

CLI:

```
npx delimit-cli lint openapi.yaml
```

No config. No API keys. No account.

---

[Delimit](https://delimit.ai) | [GitHub Action](https://github.com/marketplace/actions/delimit-api-governance) | [CLI](https://www.npmjs.com/package/delimit-cli) | [Live Demo](https://github.com/delimit-ai/delimit-action-demo/pull/2)
