---
name: linkedin-post-writer
description: Research a topic across the web and Reddit, then write a LinkedIn post in the user's own voice, grounded in their personal story and proof points. Use when the user wants to draft, write, or generate a LinkedIn post about a topic, turn an idea into a post, or build content from research. Produces one polished post plus a menu of alternative hooks.
---

# LinkedIn Post Writer

Turn a topic into a publish-ready LinkedIn post that sounds like the user — not like
generic AI content. The post is grounded in (1) real research from the web and Reddit
and (2) the user's own story and proof points, gathered through a short interview each run.

## Inputs

- **Topic**: passed as the argument (e.g. `/linkedin-post-writer the hidden cost of meetings`).
  If no topic is given, ask for one before doing anything else.

## Workflow

Run these steps in order. Do not skip the interview — the user's voice and proof points
are what make the post worth publishing.

### Step 1 — Interview the user (voice, story, proof)

The user has chosen to be interviewed each run rather than store a profile, so always do
this. Ask the questions below in a single message (use the `AskUserQuestion` tool when the
answer is a clear choice; use plain text questions when you need their words). Keep it tight
— 4 to 6 questions max. Adapt the questions to the topic.

Gather:

1. **Personal angle / story** — "What's your personal connection to this topic? A moment,
   a mistake, a turning point, or something you've seen play out?" (This becomes the post's
   spine. Push for specifics: a scene, a number, a before/after.)
2. **Proof points** — "What gives you the right to talk about this? Results, experience,
   credentials, a thing you built or shipped." (Used sparingly for credibility, never as a brag.)
3. **The take / point of view** — "What do you actually believe about this that others might
   not? What's the contrarian or hard-won lesson?"
4. **Audience** — who is this for (e.g. founders, early-career engineers, recruiters)?
5. **Tone** — let them pick: e.g. *direct & punchy*, *warm & reflective*, *analytical*,
   *story-first*, *spicy/contrarian*. If they have a sample post handy, ask them to paste it
   so you can mirror sentence length, rhythm, and vocabulary.
6. **Call to action** (optional) — what should readers do or feel at the end?

Do not proceed until you have at least the story, the take, and the tone.

### Step 2 — Research the web and Reddit

Use `WebSearch` and `WebFetch`. Run searches in parallel where possible.

- **Web**: search the topic for current data, trends, expert framing, and counterpoints.
  Pull 2-4 concrete facts, stats, or recent developments worth referencing.
- **Reddit**: search `site:reddit.com <topic>` and fetch the most relevant threads. You're
  mining for *authentic human language* — the actual words, frustrations, and hot takes real
  people use. Note recurring pain points, surprising opinions, and phrasing that resonates.

Capture: 2-4 grounded facts, the 1-2 most common pain points/objections, and a few phrases
that show how real people talk about this. Cite sources internally so you can fact-check the
draft, but the final post should read naturally (LinkedIn posts don't carry footnotes).

If research surfaces something that contradicts the user's take, surface it before drafting —
don't silently override their point of view.

### Step 3 — Write the post

Compose ONE polished, publish-ready LinkedIn post. Make it sound like the user.

Structure that works on LinkedIn:
- **Hook** (line 1): a scroll-stopper. A sharp claim, a surprising number, a tension, or a
  one-line story opener. No "I'm excited to share…".
- **Story / setup**: the user's personal angle from Step 1. Concrete and specific.
- **Insight / payoff**: the take — what they learned or believe, reinforced by research.
- **Proof**: weave in credibility lightly, only where it strengthens the point.
- **Close / CTA**: a clean landing — a question, a takeaway, or a soft invitation.

Formatting rules for LinkedIn:
- Short paragraphs (1-3 lines). Generous line breaks — it's read on mobile.
- No markdown headers, no `**bold**`, no bullet characters that render oddly. Plain text only.
- Conversational, first person. Match the tone they chose.
- Length: ~120-220 words unless they ask otherwise.
- 3-5 relevant hashtags at the very end, only if the user wants them.

Hard "don't sound like AI" rules:
- No "In today's fast-paced world", "game-changer", "delve", "leverage" (as a verb spam),
  "unlock", "supercharge", "it's not just X, it's Y" templates, or em-dash-heavy cadence
  unless that's genuinely their voice.
- No fabricated stats or quotes. Every factual claim must trace to Step 2 research or the
  user's own input.
- Don't invent details about the user's life — only use what they told you in the interview.

### Step 4 — Deliver the post + a hook menu

Output, in this order:

1. The full polished post, ready to copy-paste.
2. A **Hook menu**: 4-6 alternative opening lines in different styles (e.g. story-led,
   stat-led, contrarian, question, confession). The user can swap any of these into line 1.
3. A one-line note on which sources informed the post (so they can sanity-check facts).

Then ask if they want a tweak: different tone, shorter/longer, or a different hook from the menu.

## Notes

- Authenticity beats polish. A slightly rough post in the user's real voice outperforms a
  perfect-sounding generic one.
- If WebSearch/WebFetch is unavailable in the environment, tell the user, and offer to write
  from their interview answers alone rather than fabricating research.
