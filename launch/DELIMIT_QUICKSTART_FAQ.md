# Delimit Quickstart — FAQ & Objection Responses

**Date:** 2026-03-12

Use these responses when engaging on HN, Reddit, X, or in GitHub issues. Keep the tone technical, calm, and direct.

---

### "Why not just use oasdiff?"

oasdiff is a solid diff tool with broad detection (300+ rules). If you need raw change detection, it works well.

Delimit adds a governance layer on top of detection: configurable policy presets (strict, default, relaxed), deterministic semver classification (tells you whether this is a MAJOR, MINOR, or PATCH bump), and migration guidance in the PR comment that explains how to fix each breaking change.

If you just need a diff, oasdiff is fine. If you want CI to enforce API compatibility policy and tell developers what to do about violations, that's what Delimit does.

---

### "Why not Spectral?"

Spectral is a great linter — it checks a single spec file against style rules (naming conventions, documentation requirements, security patterns).

Delimit does something different: it compares two versions of a spec and detects breaking changes between them. Spectral cannot do this (it's explicitly out of scope — see Spectral issue #1504).

You can run both in the same CI pipeline. They don't overlap.

---

### "Why should CI fail instead of warn?"

Delimit supports both modes:

- `mode: advisory` — posts a PR comment with findings but does not fail CI
- `mode: enforce` — fails CI on breaking changes

The quickstart uses enforce mode to demonstrate the strongest use case. Most teams start with advisory to understand what Delimit catches, then switch to enforce once they trust it.

---

### "Is this only for OpenAPI?"

Currently yes — Delimit supports OpenAPI 3.x specs (YAML or JSON).

It also has a Zero-Spec mode that can extract OpenAPI definitions from FastAPI, NestJS, and Express source code, so you don't need a checked-in spec file.

Support for AsyncAPI and GraphQL schemas is on the roadmap but not shipped yet.

---

### "Why do I need another GitHub Action?"

If your team has never shipped a breaking API change by accident, you probably don't.

But if you've had an incident where an endpoint was removed, a field type changed, or a required parameter was added — and downstream consumers broke — Delimit prevents that from happening again. It takes about 5 minutes to add to an existing repo.

---

### "Can this handle semver / policies / migration guides?"

Yes, all three:

- **Semver:** Delimit classifies every change as MAJOR, MINOR, PATCH, or NONE based on the breaking surface. Deterministic — same input always produces the same classification.
- **Policies:** Three built-in presets (strict, default, relaxed) plus custom YAML policy files for team-specific rules.
- **Migration guides:** PR comments include per-violation fix instructions (e.g., "Deprecate the endpoint instead of removing it").

---

### "How is this different from just diffing two YAML files?"

A raw YAML diff shows structural text changes. It doesn't know which changes break API compatibility.

Adding a required query parameter is a one-line YAML change that looks harmless in a diff. But it's a breaking change — every existing client that doesn't send that parameter will get a 400. Delimit understands API semantics, not just text changes.

---

### "What data does the Action access?"

The Delimit GitHub Action reads only the two spec files you point it at. It does not access source code, environment variables, secrets, or any files outside the specified paths. It needs `contents: read` to check out the repo and `pull-requests: write` to post the PR comment.

No data is sent to external servers. The diff runs locally in the GitHub Actions runner.
