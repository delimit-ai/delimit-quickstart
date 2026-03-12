# Delimit Quickstart — Distribution Plan

**Date:** 2026-03-12

---

## Wave 1 — Initial Launch

### Posting Order

Launch on a **Tuesday or Wednesday morning** (US Eastern, 9-11 AM). This maximizes visibility on HN and Reddit. Stagger posts across the day.

| Order | Time | Channel | Format |
|-------|------|---------|--------|
| 1 | 9:00 AM ET | Hacker News | Show HN submission |
| 2 | 9:30 AM ET | X/Twitter | Short technical post |
| 3 | 11:00 AM ET | Reddit r/devops | Self-post with context |
| 4 | 2:00 PM ET | Reddit r/programming | Self-post, different angle |
| 5 | Ongoing | Mid-tier repo outreach | Issue comments, 2-3 per day |

### Channel Strategy

#### Hacker News — Show HN

**Angle:** "Here's what we built and why"

Post as Show HN. Lead with the problem, not the tool. HN readers respect technical honesty and dismiss anything that sounds promotional.

- Title: `Show HN: Delimit – Catch breaking API changes in CI before they ship`
- Body: Use the HN submission from MARKETING_SNIPPETS.md verbatim
- Respond to every comment. Be direct, acknowledge limitations, and link to the quickstart only when relevant.
- Do NOT ask for upvotes. Do NOT post from multiple accounts.

**Risk:** HN may ignore it (most Show HNs get <10 points). This is fine. The goal is signal, not virality.

#### X/Twitter

**Angle:** Short, technical, visual

Use Post 1 from MARKETING_SNIPPETS.md. If possible, attach a screenshot of the failing CI output. Visual content outperforms text-only on X.

- Post from the product or founder account
- Do not thread excessively — one post is enough
- Pin the post for the launch day

#### Reddit r/devops

**Angle:** "We had this problem, here's what we built"

r/devops is tolerant of tool announcements if they are genuine and the poster engages with feedback. Use the r/devops draft from MARKETING_SNIPPETS.md.

- Self-post, not a link post (link posts look promotional)
- Engage with every comment
- If someone suggests oasdiff or Spectral, respond with the FAQ answers — calmly, with acknowledgment of their strengths

#### Reddit r/programming

**Angle:** Technical exploration of the problem

r/programming is more skeptical of tool promotions. Frame the post around the problem (breaking API changes) not the tool. Use the r/programming draft from MARKETING_SNIPPETS.md.

- Expect harder questions and skepticism
- Do not get defensive — treat every objection as useful signal

#### Mid-Tier Repo Outreach

**Angle:** "I noticed you have an OpenAPI spec — have you considered CI checks?"

Start 2-3 issues per day using blurbs from MARKETING_SNIPPETS.md. Target repos from DELIMIT_MID_TIER_TARGETS_V1.md.

- Always read the repo first. Do not send generic messages.
- Reference specific spec files or endpoints in the repo.
- If the repo recently had a breaking API change (check issues/PRs), reference it.
- Accept no for an answer. Do not follow up more than once.

---

## Tone Rules

1. **Never say "we're excited to announce"** — just describe what it does
2. **Never compare to competitors unprompted** — only respond to direct questions
3. **Acknowledge limitations first** — "it only supports OpenAPI 3.x right now"
4. **Use the word "we" not "I"** — sounds more credible for a tool
5. **Link to the quickstart, not the main repo** — the quickstart is the activation path

---

## Anti-Patterns to Avoid

- Posting the same text to multiple channels (gets flagged as spam)
- Asking friends to upvote (HN detects this, Reddit detects this)
- Responding to criticism defensively
- Over-posting — one post per channel per launch window
- Linking to a landing page instead of the repo (developers distrust landing pages)

---

## Wave 2 — Week 2 (only if Wave 1 produces signal)

| Channel | Action |
|---------|--------|
| Dev.to | Cross-post blog article ("Your API Is Breaking and Nobody Told You") |
| LinkedIn | Longer-form post for engineering leaders |
| API-focused Discord servers | Share when contextually relevant |
| Hashnode | Cross-post blog article |

Wave 2 should only execute if Wave 1 produces at least one of:
- 5+ forks
- 3+ inbound questions or issues
- 1+ organic mention by someone who is not the maintainer
