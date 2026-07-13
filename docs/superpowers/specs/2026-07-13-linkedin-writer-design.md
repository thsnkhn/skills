# LinkedIn Writer Skill Design

Date: 2026-07-13

## Context

The existing LinkedIn-writing skill produces formulaic content: reusable hook templates, one-sentence-per-line formatting, mandatory calls to action, hashtag bundles, and generic first-comment tactics. That output feels unlike the account owner's strongest writing.

The replacement will be a public skill named `linkedin-writer`, but its default voice will be deliberately personal. The account owner's name must not be added to any task-created or modified content, including the skill directory, metadata, instructions, references, examples, README additions, branch name, and commit messages. Existing repository attribution outside the task's changed lines remains untouched. A final review must scan all added lines for name leakage, profile URLs, bylines, screenshots, and browser metadata that identify the account owner.

## Evidence Base

The design is grounded in two live research passes:

- A 365-day review of the account owner's LinkedIn analytics, including posts ranked by impressions and by engagement.
- A review of concrete public high-engagement posts from multiple founder, operator, and technology voices using short theses, coherent essays, charts, timely analysis, and long personal stories. Public counts are evidence of visible engagement, not proof that a post was the creator's all-time best.

The evidence does not support one universal post format. The useful common pattern is:

> real source material -> clear claim -> concrete proof -> personal point of view -> stop

The strongest account posts are rooted in actual operating work, concise opinions, company or product milestones, invitations with a real reason to respond, and playful language. Strong external posts use the same ingredients while varying radically in length and structure.

## Goals

- Draft and revise LinkedIn posts in the account owner's recognizable voice.
- Preserve the author's natural lowercase, conversational cadence without manufacturing spelling mistakes.
- Base posts on real work, events, artifacts, numbers, decisions, and opinions.
- Let length follow substance instead of an algorithmic template.
- Use first comments only when they provide useful supporting material.
- Produce publish-ready copy with minimal explanation.
- Refresh the evidence when live analytics or current benchmarks are explicitly relevant and available.

## Non-goals

- Teaching generic personal-brand formulas.
- Optimizing every draft around a forced hook, question, call to action, or hashtag set.
- Copying another creator's voice or wording.
- Inventing proof, metrics, reactions, customer claims, or personal experiences.
- Intentionally preserving accidental typos merely to appear casual.
- Automatically interacting with LinkedIn, publishing posts, commenting, reacting, following, or messaging.

## Chosen Approach

Use an evidence-backed personal voice skill rather than a static style card or a large example bank.

The skill will contain:

- A concise operational workflow in `SKILL.md`.
- An unnamed default-author voice profile in `references/default-voice.md`.
- A dated evidence snapshot in `references/linkedin-evidence.md`. Each external benchmark will record the observation date, source URL, visible engagement counts, content mode, observed pattern, and the drafting inference. It will include multiple creators, distinguish observation from inference, and summarize rather than reproduce full posts.
- Skill metadata in `agents/openai.yaml`.
- A root README entry with installation instructions using the repository's current remote.

The voice reference will distill patterns instead of storing a large corpus of full posts. It will record account-specific findings from ranked posts: favored content lanes, opening behavior, paragraph rhythm, proof style, humor, and the differences between stronger posts and weaker formulaic ones. It may include short anonymized micro-examples and before/after transformations, but not a corpus of full posts. This reduces imitation, keeps the instructions legible, and makes future evidence refreshes straightforward.

## Skill Trigger and Scope

The skill should activate when the user asks to:

- Write, rewrite, tighten, or critique a LinkedIn post in their style.
- Turn rough notes, product updates, links, or milestones into a LinkedIn post.
- Prepare a main post plus an optional first comment.
- Diagnose why a draft feels formulaic, corporate, over-polished, or unlike them.
- Review current LinkedIn performance or benchmark posts before drafting when live access is available.

The skill uses its bundled default-author voice unless the user explicitly asks for a different author. Public metadata must describe that fixed, direct builder-operator voice accurately rather than implying that the skill automatically learns every installer's personal style.

## Writing Workflow

1. Extract the actual source material: event, observation, result, artifact, tension, and available proof.
2. Verify factual claims from supplied links, supplied files, clearly relevant in-scope workspace material, or live sources when accuracy matters. Do not inspect unrelated workspace files merely because they are accessible.
3. Choose the lightest fitting content mode.
4. State the event, tension, or thesis directly in the opening rather than applying a hook formula.
5. Build only the context needed to make the point land.
6. Add concrete proof such as numbers, product names, user behavior, decisions, or consequences.
7. Add the author's actual interpretation, humor, uncertainty, or conviction.
8. Stop when the thought is complete.
9. Run the voice and anti-pattern checks.
10. Add a first comment only if it carries useful supporting material.

If the brief contains enough information, draft immediately. Ask a question only when a missing fact would materially change the post or force fabrication.

## Content Modes

### Raw builder note

Use for experiments, launches, bugs, fast builds, unexpected traction, and work-in-progress observations. Keep it immediate and specific.

### Operator opinion

Use for a belief earned through running products, teams, or client work. Lead with the conclusion, then give the concrete consequence or observation behind it.

### Milestone with proof

Use for downloads, stars, customer behavior, awards, press, shipping progress, and other earned outcomes. Keep gratitude and excitement proportionate; let the numbers and reactions carry the post.

### Invitation or action

Use for dinners, hiring, username reservations, feedback requests, releases, or other posts with a real next action. A call to action is appropriate because the action exists, not because every post needs one.

### Personal narrative

Use when chronology, tension, scenes, and emotional stakes are the substance. Earn the extra length with details only the author could provide.

## Default Voice

- Mostly lowercase when it feels natural, while preserving official capitalization for products, companies, acronyms, and people.
- Direct, conversational sentences and short natural paragraphs.
- Mixed sentence lengths; one-line paragraphs are occasional emphasis, not the whole layout.
- Calm confidence rather than announcement language. Raw builder notes may be more abrupt, excited, or fragmentary when the source material supports that mode.
- Builder and operator specificity: actual tools, products, people, decisions, and outcomes.
- Dry humor, playful understatement, and self-awareness when the material supports it.
- Honest excitement without words such as "thrilled," "honored," or "game-changing" by default.
- Clean spelling and punctuation while retaining informal phrasing.
- Specific nouns and numbers over abstract lessons.
- A distinct point of view rather than generic advice.

## Anti-patterns

Reject or revise drafts that rely on:

- Reusable hook formulas.
- A dramatic first line disconnected from the post.
- Every sentence on its own line.
- Manufactured vulnerability or a fake struggle-to-success arc.
- Generic lessons that could belong to anyone.
- Mandatory closing questions.
- Engagement bait.
- Hashtag bundles.
- Emoji decoration without meaning.
- Corporate launch language.
- Unsupported claims or inflated superlatives.
- A link in the first comment solely because of an assumed algorithm rule.

## First-comment Policy

The first comment is optional supporting infrastructure.

Use it for:

- An article or press feature.
- An app, repository, demo, or signup link.
- A source, chart, FAQ, or deeper technical explanation.
- Multiple supporting links that would interrupt the main thought.

Write the first comment as complete, paste-ready copy rather than a bare URL dump. Keep the primary action link in the main post when it is central to the requested action or when the user explicitly asks for it there; move secondary supporting links to the comment when they would interrupt the main thought. Do not add a formulaic "link in the comments" teaser unless clarity genuinely requires it. Never claim that first-comment placement guarantees better reach.

## Output Contract

Default output:

1. The publish-ready post with no preamble.
2. A `First comment:` section only when justified.

Do not add an analysis, hook score, hashtag list, posting-time advice, or alternative versions unless the user requests them.

## Freshness and Live Research

The bundled evidence is a dated baseline, not permanent algorithm truth.

When the user explicitly asks for current performance, current best practices, or benchmarking and live access is available:

- Inspect the account's current analytics and relevant recent posts.
- Inspect concrete high-performing posts from credible adjacent voices.
- Keep browser work read-only unless the user separately authorizes an interaction.
- Update drafting decisions from the observed evidence rather than generic LinkedIn folklore.

Live research changes the current drafting decision only. Updating bundled evidence files requires a separate, explicit repository-edit request. Normal drafting should use the bundled voice profile without requiring a browser pass.

## Validation

Validate the skill structure with the skill-creator validation script, then forward-test it on at least these cases:

- A product milestone with metrics, a feature article, and two links.
- A raw builder update.
- A concise operator opinion.
- An invitation with a genuine call to action.
- A long personal story.
- A formulaic draft that needs to sound natural.
- A thin brief where fabrication must be avoided.

Review each output for factual grounding, voice fit, natural paragraph rhythm, contextual CTA use, and correct first-comment behavior.

Before completion, inspect the branch's added lines for any account-owner name, identifying profile URL, byline, screenshot, or browser metadata. Existing unrelated repository text is not part of this check unless the task modifies it.

## Repository Changes

- Add `skills/linkedin-writer/` with the files described above.
- Add the skill to the root README and use the repository's current remote in install examples.
- Do not alter the existing `x-content-writer` skill beyond any root README correction needed for accurate installation.
