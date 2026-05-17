# X Algorithm Findings: Practical Playbook

This playbook turns the local `x-algorithm` source snapshot into practical operating instructions for performing better on X's "For You" feed.

The main takeaway: X is not ranking posts by one simple engagement metric. The feed first decides whether a post is eligible and relevant enough to become a candidate, then predicts many viewer-specific actions, combines those predictions into a score, applies diversity and out-of-network adjustments, and filters again before serving.

Use this as a behavior guide, not as a promise of exact reach. The local snapshot does not include live feature-switch values or final production weight values, and Phoenix is described as continuously trained in production.

## Snapshot Caveats

- I based this on the files currently present in this folder.
- Some README-referenced files are not present locally, especially deeper Phoenix runnable code and Thunder source files.
- The git working tree currently shows many tracked files as deleted and the same paths as untracked, so I did not treat git status as a clean source of truth.
- Exact production ranking weights are referenced through parameters and feature switches, but the live values are not available here.

## What The Algorithm Is Optimizing

The system has four important layers:

1. Candidate sourcing: posts come from people the viewer follows, ML-discovered out-of-network retrieval, topic retrieval, cached posts, and other sources.
2. Hydration and filtering: candidates are enriched with metadata, then removed if they are duplicate, stale, already seen, blocked, muted, off-topic, inaccessible, unsafe, or otherwise ineligible.
3. Scoring: Phoenix predicts probabilities for many actions, then the ranking scorer applies weights.
4. Final selection: posts are sorted, author repetition is discounted, out-of-network posts may be adjusted, and final visibility filters run.

This means a post has to win three battles:

- It must be retrieved as a candidate.
- It must survive filters.
- It must predict positive viewer actions without predicting negative ones.

## Ranking Signals To Care About

The code and README show positive scoring inputs for:

- Favorites or likes
- Replies
- Reposts
- Quotes
- Clicks
- Profile clicks
- Video quality views
- Photo expands
- Shares
- Shares via DM
- Shares via copied link
- Dwell
- Dwell time
- Click dwell time
- Follows of the author

The code also shows negative scoring inputs for:

- Not interested
- Block author
- Mute author
- Report
- Not dwelled

Practical interpretation:

- A post that earns a lot of passive impressions but little dwell, reply, share, follow, or click intent is weak.
- A post that generates blocks, mutes, reports, "not interested", or immediate skips can be actively harmful.
- A post that attracts the wrong audience can train bad prediction data around your account.

## The Operating Strategy

### 1. Be Easy For Retrieval To Understand

Phoenix retrieval uses user history and content representations to find out-of-network posts. Grox also creates content understanding signals, categories, summaries, tags, safety metadata, multimodal embeddings, and topic-related annotations.

Do this:

- Stay consistent around a small number of topic lanes.
- Use clear nouns, entities, and category language in the post itself.
- Make each post understandable without relying on vague inside jokes.
- Use media that reinforces the topic rather than generic decoration.
- Add enough text context to images and videos so the system and humans can understand the post.
- For video, make the spoken or visible content clear because video transcripts can feed embeddings.

Do not do this:

- Jump randomly between unrelated topics if you want a coherent audience graph.
- Post vague takes that require too much prior context.
- Use images or videos that are visually appealing but semantically unclear.
- Hide the actual subject behind clickbait phrasing.

### 2. Optimize For The Right Positive Actions

The scoring model predicts multiple actions rather than only likes. Treat a strong post as one that can plausibly generate several of these: dwell, replies, reposts, quotes, shares, profile clicks, and follows.

Do this:

- Write posts that deserve a real reply, not just a like.
- Make posts specific enough that people can quote them with their own commentary.
- Create reference-worthy posts people want to send in DMs or copy-link share.
- Make the first line carry the value so users dwell instead of skipping.
- Give people a reason to click your profile by keeping the post tied to a clear expertise lane.
- Use strong media when it adds information, proof, entertainment, or explanation.

Do not do this:

- Chase likes while ignoring replies, shares, follows, and dwell.
- Use shallow engagement bait that causes low-quality replies.
- Post content that creates curiosity but disappoints after the click.
- Ask for reposts or likes in a way that makes the post feel manipulative.

### 3. Avoid Negative Feedback At All Costs

The ranking scorer includes explicit negative actions: not interested, block, mute, report, and not dwelled. Filters also remove posts tied to muted keywords, blocked authors, visibility issues, and unsafe content.

Do this:

- Make the promise of the post match the payload.
- Avoid posting rage bait to audiences that do not want it.
- Avoid repetitive formats that make followers mute you.
- Keep controversial posts unusually precise and grounded.
- Remove spam-like patterns from replies, links, hashtags, and media.
- Keep a public, trustworthy profile that reduces block and report risk.

Do not do this:

- Farm outrage from people who are likely to block, mute, report, or click "not interested".
- Reply-promote under unrelated large accounts.
- Use misleading thumbnails, misleading first lines, or bait-and-switch links.
- Repeat the same message across many threads.
- Overuse hashtags, cashtags, or keyword stuffing.

### 4. Use Replies Carefully

The Grox code includes reply ranking and spam detection. Reply ranking appears to focus especially on replies where the target account or root account has enough reach. Spam detection is aimed at low-follower reply behavior.

Do this:

- Reply to large or relevant accounts when you can add a genuinely useful point.
- Make replies self-contained and specific to the parent post.
- Use replies to demonstrate expertise, not to dump links.
- Prioritize replies that can earn likes, replies, profile clicks, and follows.
- Reply early only when you can add quality quickly.

Do not do this:

- Leave generic "great thread" replies.
- Copy-paste the same promotional reply across accounts.
- Hijack unrelated posts with your own offer.
- Reply with only a link, image, or vague CTA.
- Argue in ways that drive blocks and reports.

### 5. Build A Coherent Audience, Not Just Reach

The model uses viewer history, followed accounts, followed topics, inferred topics, mutual-follow features, language, location/context fields, and user action sequences. That means relevance is personalized.

Do this:

- Attract followers who actually care about your core topics.
- Engage with accounts and communities in your target topic area.
- Keep your profile, bio, pinned post, and recurring topics aligned.
- Use language that matches the audience you want to reach.
- Create series and recurring formats that train audience expectations.

Do not do this:

- Build an audience from viral posts unrelated to what you want to be known for.
- Mix incompatible audiences if their interests conflict.
- Post for everyone. Phoenix is matching posts to specific histories and interests.

### 6. Respect Freshness, Seen-State, And Deduplication

The pipeline removes old posts, previously seen posts, previously served posts, duplicated post IDs, duplicate reposts, and duplicate conversation branches.

Do this:

- Publish fresh posts regularly.
- Turn a repeated idea into a genuinely new angle.
- If reposting or quoting, add enough new value to justify a new candidate.
- Space posts so your best ideas are not competing with each other in the same response.

Do not do this:

- Repost the same content repeatedly hoping it will re-enter feeds.
- Flood one conversation with multiple branches.
- Post many near-duplicate takes in a short window.
- Assume an old post can keep circulating without fresh engagement or context.

### 7. Account For Author Diversity

The ranking scorer applies an author diversity multiplier, reducing the score of repeated posts by the same author within a feed response.

Do this:

- Make fewer, stronger posts instead of many weak posts in one burst.
- Space important posts across the day.
- Avoid publishing multiple posts that target the exact same audience at the same time.
- Use threads only when each post adds distinct value.

Do not do this:

- Drop a large batch of standalone posts and expect all of them to rank.
- Split one complete thought into several weak posts unless the thread format improves it.

### 8. Make Media Earn Its Place

The scoring inputs include video quality views, photo expands, quoted video quality views, media presence, video duration, and transcripts. Media can help, but only if it improves understanding or engagement.

Do this:

- Use images that are legible on mobile.
- Use videos with a strong first few seconds and enough duration to earn quality-view signals.
- Add captions or visible context to videos.
- Use screenshots, charts, demos, and proof when they clarify the post.
- Make quoted media additive, not decorative.

Do not do this:

- Add generic images just to "have media".
- Post videos with long intros before the actual value.
- Use unreadable screenshots.
- Use media that triggers sensitive-content or brand-safety issues.

### 9. Be Safe And Brand-Safe

The local snapshot includes visibility filtering, safety labels, post-safety screening, PTOS policy checks, spam checks, adult content, violent media, illegal/regulated behavior, hate/abuse, violent speech, and self-harm policy categories.

Do this:

- Keep sensitive topics factual, careful, and necessary.
- Avoid graphic media and unsafe framing.
- Avoid abusive language aimed at protected groups or individuals.
- Treat regulated topics with extra care.
- Keep public posts suitable for broad recommendation surfaces.

Do not do this:

- Post gore, violent threats, hateful abuse, adult material, scams, or dangerous instructions.
- Use edgy phrasing when neutral phrasing would make the same point.
- Let jokes look like policy violations without context.

## Practical Posting Checklist

Before publishing, ask:

- Candidate: Would the system clearly know who this is for?
- Topic: Does it reinforce one of my core lanes?
- Hook: Will the first line stop the right person?
- Value: Is there a concrete idea, proof, story, data point, or useful opinion?
- Action: What positive action should this predict: reply, repost, quote, share, dwell, click, profile click, follow?
- Media: Does the media add meaning, or is it decoration?
- Safety: Could this trigger mute, block, report, not interested, spam, or safety filters?
- Repetition: Have I posted this same point too recently?
- Audience: Is this attracting the people I want X to associate with me?

## Dos

- Do post around consistent topics.
- Do write for the audience you want the algorithm to learn.
- Do create posts with high reply, share, quote, and dwell potential.
- Do make claims specific and easy to respond to.
- Do use media when it improves comprehension or proof.
- Do keep videos clear, captioned, and immediately useful.
- Do reply thoughtfully to relevant high-reach conversations.
- Do keep your profile aligned with the topics you post about.
- Do avoid repetition inside the same posting window.
- Do track which posts generate follows, profile clicks, replies, quotes, and shares, not only likes.
- Do delete or stop repeating formats that cause low dwell, mutes, blocks, or hostile replies.
- Do keep sensitive content precise and safe.

## Don'ts

- Don't optimize only for likes.
- Don't chase controversy that creates blocks, mutes, reports, or "not interested".
- Don't post generic AI slop, vague advice, or recycled platitudes.
- Don't keyword-stuff topics or hashtags.
- Don't reply-spam under large accounts.
- Don't reuse the same promotional reply across threads.
- Don't flood your feed with many similar posts at once.
- Don't rely on old posts, duplicate reposts, or repeated conversation branches.
- Don't use misleading hooks that reduce trust after the click.
- Don't use unclear media, unreadable screenshots, or videos with slow starts.
- Don't mix unrelated niches if you need the algorithm to understand your account.
- Don't post from a protected/private posture if you want full public content-understanding and recommendation benefits.

## A Simple Weekly Operating System

1. Pick 2 to 4 topic lanes for the week.
2. Publish a mix of:
   - One high-depth post per lane.
   - One media-backed proof or demo post.
   - Several high-quality replies to relevant accounts.
   - One post designed for saves/shares/reference value.
3. For each post, record:
   - Replies
   - Reposts
   - Quotes
   - Shares
   - Profile visits
   - Follows
   - Video retention or views, if applicable
   - Negative feedback clues, such as hostile replies, unfollows, or reduced reach after similar posts
4. Repeat formats that bring the right audience and positive actions.
5. Retire formats that bring empty likes, wrong-audience controversy, or negative feedback.

## What Not To Overfit

- Exact weights: the local snapshot references feature-switch weights, but the actual live values are not present in the folder.
- Exact posting times: the code emphasizes freshness, relevance, and viewer-specific prediction more than a universal time slot.
- One viral metric: scoring is multi-action and personalized.
- Hacky tactics: spam, duplication, and rage bait are directly risky because filters and negative predictions exist.

## Source Map From This Folder

- `README.md`: overall architecture, candidate sources, ranking stages, positive and negative action predictions, filtering stages.
- `phoenix/README.md`: retrieval plus ranking architecture, two-tower retrieval, transformer ranking, candidate isolation, multi-action prediction, demo action indices.
- `home-mixer/candidate_pipeline/phoenix_candidate_pipeline.rs`: actual Home Mixer pipeline composition, sources, hydrators, filters, scorers, selector, post-selection filters, side effects.
- `home-mixer/scorers/ranking_scorer.rs`: weighted scoring inputs, negative action terms, author diversity, out-of-network weighting.
- `home-mixer/scorers/weighted_scorer.rs`: weighted score formula and positive/negative score components.
- `home-mixer/scorers/author_diversity_scorer.rs`: repeated-author score attenuation.
- `home-mixer/filters/*.rs`: age, duplicate, previously seen, previously served, muted keyword, social graph, topic, video, visibility, and conversation filters.
- `home-mixer/sources/*.rs`: in-network, Phoenix retrieval, topic retrieval, cached posts, and TweetMixer source behavior.
- `home-mixer/models/candidate.rs`: candidate fields such as media, language, engagement counts, topic IDs, safety labels, author data, reply/repost/quote fields, and Phoenix scores.
- `grox/classifiers/content/*.py`: content quality, spam, reply ranking, safety, and PTOS classification workflows.
- `grox/embedder/*.py` and `grox/summarizer/*.py`: multimodal content embeddings, post summaries, and transcript-aware video embedding.

## Final Rule

Create posts that the right people are likely to dwell on, reply to, share, quote, click through from, and follow you for, while avoiding anything that makes the wrong people mute, block, report, skip, or mark you as uninteresting.
