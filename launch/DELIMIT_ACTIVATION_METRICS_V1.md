# Delimit — Activation Metrics (v1)

**Date:** 2026-03-12

---

## Core Metrics

| Metric | Source | Cadence |
|--------|--------|---------|
| **Stars** | GitHub repo insights | Daily during launch, weekly after |
| **Forks** | GitHub repo insights | Daily during launch, weekly after |
| **Unique visitors** | GitHub traffic tab | Weekly |
| **Unique cloners** | GitHub traffic tab | Weekly |
| **Referring sites** | GitHub traffic tab | Weekly |
| **Action runs (from forks)** | GitHub Actions tab | Weekly |
| **Issues opened** | GitHub notifications | As they arrive |
| **npm installs (delimit-cli)** | npm stats | Weekly |
| **GitHub Action installs** | Marketplace stats | Weekly |

---

## Funnel

```
View quickstart README
        ↓
    Fork repo
        ↓
  CI runs on fork (Action executes)
        ↓
  Open issue or star
        ↓
  Add Delimit to own repo (workflow copy)
        ↓
  Retained usage (repeat runs across multiple PRs)
```

### Conversion Targets

| Stage | Target | How to Measure |
|-------|--------|---------------|
| View → Fork | >5% | GitHub traffic ÷ fork count |
| Fork → Action run | >50% | Fork count vs Action run count on forks |
| Fork → Star | >20% | Fork count vs star count |
| View → Own repo install | >1% | Referrer data on delimit-action installs |

---

## Outcome Gates

### Gate 1: Continue Current Motion

**Criteria (any 2 of 4 within 2 weeks):**
- 10+ forks
- 5+ stars from non-team accounts
- 3+ inbound issues or questions
- 1+ organic mention (someone posts about Delimit without being asked)

**Action if met:** Continue Wave 1 distribution. Begin Wave 2 (Dev.to, LinkedIn).

### Gate 2: Revise Quickstart Messaging

**Criteria (any 2 of 3 within 2 weeks):**
- <5 forks despite >500 unique visitors
- Repeated confusion in issues about what Delimit does
- Multiple comments asking "how is this different from X" without converting

**Action if met:** Rewrite README intro. A/B test different problem statements. Check if the "Expected Result" section is being read.

### Gate 3: Revise Distribution Channels

**Criteria (within 2 weeks):**
- HN post gets <5 points
- Reddit posts get <10 upvotes combined
- Zero inbound from any channel

**Action if met:** Shift to direct outreach only. Increase mid-tier repo issue volume to 5/day. Write a blog post targeting "prevent API breaking changes" keyword for SEO.

### Gate 4: Begin Multi-Agent Demo

**Criteria (all 3 required):**
- 20+ activated installs with repeat usage (not tourist forks)
- 2+ organic testimonials or positive issue comments
- Quickstart fork→action conversion rate is measured and >30%

**Action if met:** Time-box multi-agent-demo build to 5 days. Position as content/thought leadership, not primary adoption driver.

---

## Objection Tracking

| Objection Category | Count | Notes |
|-------------------|-------|-------|
| "Just use oasdiff" | | |
| "Just use Spectral" | | |
| "CI should warn, not fail" | | |
| "Only OpenAPI?" | | |
| "Don't need another Action" | | |
| "What about data/security?" | | |
| "How is this different from diff?" | | |
| Other | | |

Review this table weekly. If any single objection category exceeds 30% of all feedback, it indicates a positioning gap that needs addressing.

---

## Baseline Snapshot (Pre-Launch)

| Metric | Value | Date |
|--------|-------|------|
| Stars | | |
| Forks | | |
| npm weekly installs | | |
| Action marketplace installs | | |
| Open issues | 0 | 2026-03-12 |
