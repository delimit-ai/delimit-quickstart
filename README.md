# delimit-quickstart

Fork this repo, push a breaking API change, and see Delimit catch it in CI.

## What's in the box

- `openapi.yaml` -- a Pet Store API with 4 endpoints
- `openapi-changed.yaml` -- the same spec with breaking changes:
  - `GET /pets/{petId}` removed
  - `DELETE /pets/{petId}` removed
  - `Pet.id` type changed from `string` to `integer`
  - `Pet.tag` field removed
  - `Pet.status` enum value `pending` removed
- `.github/workflows/delimit.yml` -- runs the Delimit action on every push/PR

## Try it

1. Fork this repo
2. Push any commit (or just trigger Actions manually)
3. Watch CI fail:

```
::error title=Delimit::Endpoint /pets/{petId} removed
::error title=Delimit::Field id type changed from string to integer
```

4. On a PR, Delimit posts a comment with a migration guide

## Fix the build

Delete `openapi-changed.yaml` and update the workflow to compare `openapi.yaml` against itself. Or better -- edit `openapi-changed.yaml` to only add new endpoints and fields. Additive changes pass.

## Use Delimit in your own repo

```yaml
# .github/workflows/delimit.yml
- uses: delimit-ai/delimit-action@v1
  with:
    old_spec: openapi.yaml
    new_spec: openapi.yaml
    mode: enforce
```

Point `old_spec` at your base spec and `new_spec` at the changed version. The action detects breaking changes and posts PR comments automatically.

Or use the CLI:

```
npx delimit-cli lint openapi.yaml
```

---

[GitHub Action](https://github.com/delimit-ai/delimit-action) | [CLI](https://www.npmjs.com/package/delimit-cli) | [delimit.ai](https://delimit.ai)
