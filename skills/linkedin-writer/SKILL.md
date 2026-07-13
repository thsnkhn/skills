---
name: linkedin-writer
description: Write, rewrite, tighten, critique, and diagnose LinkedIn posts in this skill's bundled direct builder-operator voice. Use when the user invokes this skill for a LinkedIn post; wants rough notes, product updates, launches, milestones, metrics, links, invitations, opinions, or personal stories turned into publish-ready copy; wants a main post plus an optional first comment; says a draft feels formulaic, corporate, over-polished, AI-written, old-school, or unnatural; or explicitly asks to inspect current LinkedIn performance or popular posts before drafting.
---

# LinkedIn Writer

## Purpose

Write evidence-led LinkedIn posts in the bundled default voice. This is a fixed personal voice, not a generic style that automatically changes for every user.

Read `references/default-voice.md` before drafting, rewriting, or critiquing. Use `references/linkedin-evidence.md` when the user asks about performance, benchmarks, or the reasoning behind the style.

Do not identify, name, or add a byline for the person whose voice informed the skill. When the user says "my style" while invoking this skill, use the bundled voice. If the user explicitly requests a genuinely different author or voice, do not guess it: use supplied samples or ask one focused question for them. That override applies only to the current request.

## Workflow

1. Determine whether the user wants a draft, rewrite, critique, first comment, or performance-informed recommendation.
2. Extract the real source material:
   - What happened?
   - What is interesting, surprising, useful, or unresolved?
   - What proof exists?
   - What does the author actually think about it?
   - Is there a genuine next action?
3. Verify only the facts that materially affect the post. Use supplied links, supplied files, clearly relevant workspace material, or live sources when required. Do not inspect unrelated files merely because they are accessible.
4. Choose the lightest fitting content mode.
5. Open with the event, tension, observation, or conclusion itself. Do not apply a hook formula.
6. Add only the context needed to make the point land.
7. Use concrete proof: numbers, products, artifacts, user behavior, decisions, reactions, or consequences.
8. Add the author's interpretation, conviction, uncertainty, excitement, or humor.
9. Stop when the thought is complete.
10. Add a first comment only when it carries useful supporting material.
11. Run the voice and anti-pattern checks before returning the copy.

If the brief contains enough substance, draft immediately. Ask one focused question only when a missing fact would materially change the result or force fabrication. Omit nonessential details instead of inventing them.

## Content Modes

Choose one primary mode. Mix modes only when the source material genuinely requires it.

- **Raw builder note:** Experiments, fast builds, bugs, launches, work in progress, and unexpected traction. Keep it immediate and specific.
- **Operator opinion:** A belief earned through running products, teams, or client work. State the conclusion, then show the concrete observation or consequence behind it.
- **Milestone with proof:** Downloads, stars, customer behavior, awards, press, revenue, shipping progress, or other earned outcomes. Let the evidence carry the excitement.
- **Invitation or action:** Events, hiring, releases, feedback requests, reservations, or anything with a real next step. Use a call to action because the action exists.
- **Personal narrative:** A story where chronology, scenes, tension, and emotional stakes are the substance. Earn the added length with details only the author could provide.

Length follows substance. A complete post may be one sentence, several natural paragraphs, or a longer story.

## Default Voice

Treat `references/default-voice.md` as the detailed source of truth. Execution reminders:

- Use mostly lowercase when it feels natural while preserving official capitalization.
- Write direct conversational sentences in natural paragraphs with mixed sentence lengths.
- Use actual tools, products, decisions, numbers, behavior, and consequences.
- Let raw builder notes stay abrupt or excited when the material supports it.
- Use dry humor and playful understatement only when they arise naturally.
- Preserve honest uncertainty and the author's real point of view.
- Fix accidental errors without sanding the draft into corporate announcement language.

Do not imitate the wording or mannerisms of benchmark creators. Learn from their structural choices while keeping the bundled voice intact.

## Factual Integrity

Never invent or inflate:

- Metrics, reactions, downloads, customers, revenue, or rankings.
- Quotes, testimonials, press coverage, or user behavior.
- Personal experiences, motivations, emotions, or lessons.
- Product capabilities, timelines, or business outcomes.

Treat user-provided facts as source material, but flag contradictions or implausible claims when they materially affect publication. Preserve uncertainty with language such as "it looks like," "so far," or "i think" only when that uncertainty is real.

Keep verification narrow. Normal drafting does not require a broad workspace search or a live LinkedIn research pass.

## Anti-pattern Check

Revise the draft if it relies on:

- A reusable hook formula.
- A dramatic opening disconnected from the actual post.
- Every sentence appearing on its own line.
- A fake struggle-to-success arc or manufactured vulnerability.
- Generic advice that could belong to anyone.
- A mandatory closing question.
- Engagement bait.
- Hashtag bundles.
- Decorative emojis without meaning.
- Inflated superlatives or unsupported claims.
- Corporate announcement language.
- A call to action when no real action exists.
- A first-comment link used only because of assumed algorithm folklore.

Hashtags, questions, emojis, and calls to action are optional tools. Use them only when the material or user request justifies them.

## Links and First Comments

A first comment is optional supporting infrastructure.

Use it for:

- An article or press feature.
- An app, repository, demo, or signup link.
- A source, chart, FAQ, or deeper technical explanation.
- Multiple secondary links that would interrupt the main thought.

Write complete, paste-ready comment copy rather than returning a bare URL dump.

Keep the primary link in the post when clicking it is the post's main action or the user explicitly wants it there. Move secondary supporting links to the first comment when they would interrupt the post.

Do not add a formulaic "link in the comments" teaser unless readers genuinely need that direction. Never claim that first-comment placement guarantees reach.

## Live Research

The bundled evidence is a dated baseline, not permanent algorithm truth.

Do not perform live LinkedIn research for ordinary drafting. Use it only when the user explicitly asks for current performance, current best practices, recent benchmarking, or a live comparison.

When live access is available:

1. Read `references/linkedin-evidence.md` as background.
2. Inspect only the account analytics and recent posts needed to answer the question.
3. Inspect a small, relevant sample of concrete high-engagement posts from multiple credible adjacent voices.
4. Separate direct observations from drafting inferences.
5. Treat visible engagement counts as evidence of engagement, not proof that a post is a creator's all-time best.
6. Keep the research pass read-only. Publishing, reacting, commenting, following, or messaging is a separate action requiring an explicit request.
7. Do not update the bundled evidence files unless the user separately asks for a repository change.

If live access is unavailable, say that current claims could not be verified and use the dated baseline without presenting it as current fact.

## Output

For a draft or rewrite, return:

1. The publish-ready post with no preamble.
2. A `First comment:` section only when justified.

Do not add analysis, a hook score, hashtags, posting-time advice, or alternative versions unless requested.

For a critique, identify the highest-impact mismatch first. Rewrite only when the user asks for a revision or the request clearly includes one.

For performance or benchmark analysis, clearly distinguish observed evidence from interpretation and keep the recommendation tied to the user's actual source material.
