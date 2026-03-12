# Delimit — Mid-Tier Outreach Targets (v1)

**Date:** 2026-03-12
**Target band:** 1K–10K GitHub stars
**Criteria:** Repo has a checked-in OpenAPI spec or generates one from code

---

## Target Categories

### 1. OpenAPI-First Frameworks

**Why they fit:** These projects generate or consume OpenAPI specs as a core feature. Breaking changes in their own API surface directly affect downstream SDK generators and clients.

**Outreach angle:** "Your framework generates OpenAPI specs — have you considered adding a CI check that catches breaking changes between releases? Delimit does this automatically."

**What Delimit solves:** Prevents breaking changes from shipping in new framework versions, protecting the ecosystem of tools that depend on their spec output.

**Examples to research:**
- FastAPI extensions/plugins with their own API surfaces
- NestJS Swagger module ecosystem projects
- Go frameworks with OpenAPI generation (go-swagger, ogen)
- Rust API frameworks (poem-openapi, utoipa)

---

### 2. SDK Generators

**Why they fit:** SDK generators consume OpenAPI specs as input. If the upstream spec has a breaking change, every generated SDK breaks. These projects care deeply about spec stability.

**Outreach angle:** "You consume OpenAPI specs to generate SDKs. If the upstream spec changes in a breaking way, every generated client breaks. Delimit can validate spec compatibility in CI."

**What Delimit solves:** Validates that input specs haven't introduced breaking changes before regenerating SDKs.

**Examples to research:**
- openapi-generator ecosystem plugins
- Kiota (Microsoft) extensions
- Orval (TypeScript client generator)
- openapi-typescript

---

### 3. API Platforms & Gateways

**Why they fit:** API gateways and platforms manage multiple API versions. Breaking changes in gateway configuration or upstream APIs cause routing failures and consumer errors.

**Outreach angle:** "Your platform manages API routing and versioning. Delimit can validate that API spec changes don't break existing consumers before they're deployed."

**What Delimit solves:** Catches breaking changes in API specs before gateway configuration is updated.

**Examples to research:**
- Kong plugins/extensions with OpenAPI
- Tyk gateway projects
- API management tools with spec validation
- Developer portal generators

---

### 4. Internal Tooling & Backend Starters

**Why they fit:** Backend starter kits and internal tooling templates often include an API contract. Teams fork these starters and evolve the API — breaking changes are common and undetected.

**Outreach angle:** "Your starter kit includes an API spec. Teams that fork it will evolve that API — Delimit can catch breaking changes automatically so they don't ship regressions."

**What Delimit solves:** Adds a safety net to forked/evolved API contracts in template repos.

**Examples to research:**
- FastAPI project templates with OpenAPI
- NestJS boilerplate projects
- Express API starter kits
- Django REST framework templates with schema generation

---

### 5. Projects That Recently Had a Breaking API Change

**Why they fit:** The best time to adopt a breaking-change detector is right after a breaking change caused pain. These projects have a recent, lived experience of the problem.

**Outreach angle:** "I saw the recent discussion about the [specific breaking change]. Delimit would have caught that automatically in CI. Here's a quickstart if you want to try it."

**What Delimit solves:** Prevents recurrence of a specific, recent pain point.

**How to find them:**
- Search GitHub issues for "breaking change" + "API" in repos with 1K-10K stars
- Search for issues mentioning "backward compatibility" or "incompatible"
- Look at repos with recent major version bumps (v2.0, v3.0) that had migration issues

---

## Outreach Rules

1. **Read the repo first.** Understand what it does before reaching out.
2. **Reference specific files.** Mention their actual spec path (e.g., "I noticed `docs/openapi.yaml`").
3. **One touch per repo.** If they don't respond, move on.
4. **Open an issue, not a PR.** Issues are conversations. Unsolicited PRs are presumptuous.
5. **Accept no gracefully.** "Makes sense, thanks for considering it" and move on.
6. **Log every outreach** in the feedback log with the response (or lack thereof).

---

## Prioritization

| Priority | Category | Reason |
|----------|----------|--------|
| 1 | Projects with recent breaking changes | Highest pain, most receptive |
| 2 | SDK generators | Direct dependency on spec stability |
| 3 | OpenAPI-first frameworks | Natural fit, spec is core to their product |
| 4 | Backend starters | Easy to adopt, template effect multiplies |
| 5 | API platforms | Longer decision cycle, but high value |
