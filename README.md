# delimit-quickstart

API governance in 2 minutes. Fork, push, see breaking changes blocked.

## Fastest way to try

No fork needed — run the self-contained demo:

```bash
npx delimit-cli demo
```

Creates a sample API, introduces breaking changes, runs governance, shows gate status. Done in seconds.

## What's in this repo

- `openapi.yaml` — a Pet Store API with 4 endpoints
- `openapi-changed.yaml` — the same spec with 5 breaking changes:
  - `GET /pets/{petId}` removed
  - `DELETE /pets/{petId}` removed
  - `Pet.id` type changed from `string` to `integer`
  - `Pet.tag` field removed
  - `Pet.status` enum value `pending` removed
- `.github/workflows/delimit.yml` — runs governance on every push/PR
- `.github/workflows/drift-monitor.yml` — weekly drift detection

## Try the GitHub Action

1. Fork this repo
2. Open a PR (or push any commit)
3. Delimit posts a governance cockpit comment:

> ### Governance Gates
>
> | Gate | Status | Chain |
> |------|--------|-------|
> | API Lint | Fail | lint -> semver -> gov_evaluate |
> | Policy Compliance | Fail (5 violations) | policy -> evidence_collect |
> | Security Audit | Pass | security_audit -> evidence_collect |
> | Deploy Readiness | Blocked | deploy_plan -> security_audit |
>
> **5 breaking changes detected** — deploy blocked until resolved.

4. In enforce mode, CI fails until the breaking changes are fixed

## Set up governance in your project

```bash
npx delimit-cli init         # Guided wizard: detect framework, choose policy, first lint
npx delimit-cli setup        # Configure Claude Code, Codex, Cursor, Gemini CLI
```

Includes compliance templates (SOC2, PCI-DSS, HIPAA) and automatic evidence collection.

## GitHub Action

Simplest setup — auto-detects your spec:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    spec: api/openapi.yaml
```

Or compare two files explicitly:

```yaml
- uses: delimit-ai/delimit-action@v1
  with:
    old_spec: openapi.yaml
    new_spec: openapi-changed.yaml
    mode: enforce
```

No config. No API keys. No account.

---

[Delimit](https://delimit.ai) | [Dashboard](https://app.delimit.ai) | [GitHub Action](https://github.com/marketplace/actions/delimit-api-governance) | [CLI](https://www.npmjs.com/package/delimit-cli) | [Docs](https://delimit.ai/docs)
