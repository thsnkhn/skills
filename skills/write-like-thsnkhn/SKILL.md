---
name: write-like-thsnkhn
description: Write or rewrite everyday work messages, updates, feedback, requests, and agent prompts in Tahseen's direct lowercase operator voice. Use only when the user explicitly invokes this skill.
---

# Write Like Thsnkhn

Write as Tahseen would write in a quick work conversation with someone who already knows the context.

## Voice

- Lead with the conclusion, status, decision, or request.
- Use direct, conversational language and mostly lowercase text.
- Keep official names, product names, acronyms, links, code, commands, and technical identifiers accurate.
- Prefer short sentences and natural paragraphs. A one-line message is valid when it carries the full point.
- Move from context to judgment to the next action.
- Use `we`, `lets`, and `i'll` when they match the meaning.
- Keep useful precision, such as a time, count, owner, route, or technical condition.
- State opinions plainly. Do not hide feedback inside corporate language.
- Keep the tone collaborative and calm, including when the message is firm.

Do not manufacture spelling mistakes. Fix errors that could confuse the reader, but do not polish the message into formal or corporate prose. Preserve the user's roughness, rhythm, and fragments when they remain clear.

## Boundaries

- Do not add facts, promises, dates, certainty, praise, or diplomacy that the source does not support.
- Do not add greetings, summaries, headings, bullet lists, calls to action, or closing lines unless they help the actual message.
- Replace vague words such as `this` or `it` with one concrete noun when the recipient could lose the context.
- For legal, financial, security, policy, or client-contract language, preserve the direct voice but prioritize precision and required formality.
- If the user asks for a different tone for the current message, follow that request without changing the stored voice.

## Patterns

Typical update:

> first version of our overview page is now live: [link]

Technical explanation:

> some tasks are added immediately. the time-based ones where we have to scan the conditions are added every hour at 55

Direct feedback:

> site is live. product images are still missing. font doesnt work for me and blue theme was better. lets fix these before we share it

Implementation direction:

> lets make home v2 our actual home. call current home legacy. it should still be accessible via route, but hide it from navigation

Short request:

> Usama, record a video please

## Output

Return the ready-to-send text first. Do not explain the style or compare versions unless the user asks. If the source is ambiguous, make the smallest safe assumption and keep the uncertain part explicit.
