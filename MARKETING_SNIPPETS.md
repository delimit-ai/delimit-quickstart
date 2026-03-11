# Marketing Snippets

For internal use. Do not check into public-facing docs.

---

## X/Twitter Posts

### Post 1
We built a GitHub Action that catches breaking API changes before they ship. Remove an endpoint? CI fails. Change a type? CI fails. Add a required param? CI fails.

Try it: github.com/delimit-ai/delimit-quickstart

### Post 2
How many breaking API changes shipped to production last quarter because nobody diffed the spec?

Delimit runs in CI and blocks them automatically. Fork the quickstart and see it work in 5 minutes.

github.com/delimit-ai/delimit-quickstart

### Post 3
OpenAPI specs are contracts. When you remove an endpoint, that contract is broken.

Delimit enforces API compatibility in CI — same way a linter enforces code style. Except it catches the bugs that actually page people.

github.com/delimit-ai/delimit

---

## Reddit Posts

### r/devops — "We built a CI check that catches breaking API changes"

We kept running into the same problem: someone removes an endpoint or changes a response type, it passes code review, and downstream services break in production.

So we built Delimit — a GitHub Action that diffs your OpenAPI specs on every PR and fails CI when it detects a breaking change. It tells you exactly what broke and how to fix it.

There's a quickstart repo you can fork to see it work in under 5 minutes: https://github.com/delimit-ai/delimit-quickstart

It removes a `GET /users/{id}` endpoint between two spec versions, and CI fails with: `Endpoint /users/{id} cannot be removed. Deprecate it first.`

Would appreciate any feedback. We're early and trying to make this actually useful.

### r/programming — "Detecting breaking API changes automatically in CI"

If you maintain an API, you've probably shipped a breaking change by accident. Removed an endpoint, changed a field type, added a required parameter — and found out when consumers started failing.

We built a tool that catches this in CI by diffing OpenAPI specs. It classifies changes by severity, recommends the correct semver bump, and blocks the merge if policy is violated.

Quickstart repo (fork and try in 5 minutes): https://github.com/delimit-ai/delimit-quickstart

Main repo: https://github.com/delimit-ai/delimit

---

## Hacker News

### Submission Title
Show HN: Delimit — Catch breaking API changes in CI before they ship

### Body Text
We built Delimit because we kept shipping breaking API changes that passed code review. Someone removes an endpoint, renames a field, or changes a type — and downstream consumers discover it in production.

Delimit is a GitHub Action that diffs your OpenAPI specs on every PR. It detects breaking changes, classifies the semver impact, and posts a comment with migration guidance. In enforce mode, it fails CI.

There's a quickstart repo you can fork to see it work: https://github.com/delimit-ai/delimit-quickstart

It contains two specs — v1 has `GET /users/{id}`, v2 removes it. Push, and CI fails with: "Endpoint /users/{id} cannot be removed. Deprecate it first."

What it catches: endpoint removals, required parameter additions, type changes, enum value removals, field removals, and more (23 change types total, 10 classified as breaking).

It also works without a checked-in spec — it can extract OpenAPI definitions from FastAPI, NestJS, and Express source code.

Main repo: https://github.com/delimit-ai/delimit
GitHub Action: https://github.com/delimit-ai/delimit-action
npm: https://www.npmjs.com/package/delimit-cli

---

## Outreach Blurbs (for mid-tier repo maintainers)

### Blurb 1 — Issue comment style
I noticed this project has an OpenAPI spec checked into the repo. Have you considered adding a CI check for breaking API changes?

We built a GitHub Action called Delimit that diffs your spec on every PR and catches things like removed endpoints, type changes, and required parameter additions before they ship.

There's a quickstart you can fork to see it work: https://github.com/delimit-ai/delimit-quickstart

Happy to help set it up if you're interested.

### Blurb 2 — Shorter, for smaller projects
Your project has an OpenAPI spec — nice. If you ever want to automatically catch breaking changes in CI, check out Delimit: https://github.com/delimit-ai/delimit-quickstart

It diffs your spec on every PR and blocks breaking changes. Takes about 5 minutes to set up.

### Blurb 3 — For projects that recently had a breaking change
I saw the recent discussion about the API change in [version]. Delimit is a GitHub Action that would have caught that automatically — it diffs OpenAPI specs on every PR and flags breaking changes before merge.

Quickstart (fork and try): https://github.com/delimit-ai/delimit-quickstart
Main repo: https://github.com/delimit-ai/delimit
