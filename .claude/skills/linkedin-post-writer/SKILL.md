---
name: linkedin-post-writer
description: Discover trending, relatable tech topics by researching the web and Reddit, then write a LinkedIn post about a chosen topic in the user's saved voice. Use when the user wants trending tech topic ideas for LinkedIn, wants to write/draft a LinkedIn post, or wants content ideas grounded in current discussion. Surfaces a shortlist of topics to pick from, then produces one polished post plus a menu of alternative hooks. Voice is loaded from voice-profile.md (filled once), not asked each run.
---

# LinkedIn Post Writer

Find what tech people are actually talking about right now, let the user pick a topic, then
write a publish-ready LinkedIn post in their own voice. No per-run interview — the voice,
story, and proof points live in `voice-profile.md` and are reused automatically.

## Files

- `voice-profile.md` (in this skill's directory) — the user's tone, story, and proof points.
  Filled in ONCE by the user. Read it every run.

## Workflow

### Step 0 — Load the voice profile

Read `voice-profile.md` from this skill's base directory.

- If it still contains the placeholder markers (lines with `<FILL IN ...>` or it's otherwise
  clearly the unfilled template), STOP and tell the user it needs to be filled in once. Offer
  to help: ask them the story/proof/tone questions conversationally, write their answers into
  `voice-profile.md`, and commit it — so they never have to enter it again. Then continue.
- If it's filled, silently absorb the voice (tone, sentence rhythm, vocabulary, story bank,
  proof points) and use it when writing. Do not re-ask the user for this information.

### Step 1 — Discover trending, relatable tech topics

Use `WebSearch` and `WebFetch`. Run searches in parallel where possible. The goal is topics
that are BOTH currently-buzzing AND relatable enough to carry a personal LinkedIn post —
not dry press-release news.

- **Web**: search for what's trending in tech right now — e.g. `trending tech topics`,
  `tech discourse this week`, debates among engineers/founders, plus anything tied to the
  user's domain if their profile names one.
- **Reddit**: search `site:reddit.com` across subreddits like r/programming, r/cscareerquestions,
  r/ExperiencedDevs, r/technology, r/startups, r/devops (pick ones matching the user's field).
  Fetch the hottest/most-discussed threads. You're mining for the topics people are emotional
  about — frustrations, hot takes, "am I the only one who..." — because those make relatable posts.

Filter to topics that:
- Have a clear human tension or opinion (not just an announcement).
- Connect to something in the user's voice profile (their role, story, or proof) where possible.
- Aren't overdone clichés unless there's a fresh angle.

### Step 2 — Present a shortlist (user picks)

Show the user ~5 trending topics as a numbered list. For each, give:
- A short title.
- One line on the **angle** — the tension or take that would make it a good post.
- A quick note on **why it's hot** (e.g. "blowing up on r/ExperiencedDevs this week").

Then ask the user to pick a number (or suggest their own). Wait for their choice.

### Step 3 — Deep-research the chosen topic

Once they pick, research that specific topic more closely on the web and Reddit:
- Pull 2-4 concrete facts, stats, or recent developments worth referencing.
- Capture the 1-2 most common pain points/objections and a few phrases showing how real
  people talk about it (for authentic language, not to copy verbatim).
- Cite sources internally so you can fact-check; the final post reads naturally (no footnotes).

If research contradicts an angle in the user's voice profile, surface it before drafting.

### Step 4 — Write the post (in the user's voice)

Compose ONE polished, publish-ready LinkedIn post, grounded in the voice profile + research.

Structure:
- **Hook** (line 1): a scroll-stopper — sharp claim, surprising number, tension, or story opener.
  No "I'm excited to share…".
- **Story / setup**: pull a relevant moment or proof point from the voice profile. Concrete.
- **Insight / payoff**: the take, reinforced by the research.
- **Proof**: weave in credibility lightly, only where it strengthens the point.
- **Close**: per the profile's preferred ending style.

Formatting rules for LinkedIn:
- Short paragraphs (1-3 lines). Generous line breaks — read on mobile.
- Plain text only: no markdown headers, no `**bold**`, no odd bullet characters.
- Conversational, first person. Match the profile's tone and rhythm.
- Length ~120-220 words unless the profile or user says otherwise.
- Hashtags only if the profile says yes (then 3-5 relevant ones at the end).

Hard "don't sound like AI" rules:
- Avoid "In today's fast-paced world", "game-changer", "delve", "leverage" spam, "unlock",
  "supercharge", "it's not just X, it's Y" templates, and em-dash-heavy cadence unless that's
  genuinely the user's voice.
- No fabricated stats or quotes. Every factual claim traces to Step 3 research or the profile.
- Don't invent personal details — only use what's in the voice profile.

### Step 5 — Deliver the post + a hook menu

Output, in order:
1. The full polished post, ready to copy-paste.
2. A **Hook menu**: 4-6 alternative opening lines in different styles (story-led, stat-led,
   contrarian, question, confession) the user can swap into line 1.
3. A one-line note on which sources informed the post.

Then ask if they want a tweak: different tone, shorter/longer, a different hook, or a different
topic from the shortlist.

## Notes

- Authenticity beats polish — a slightly rough post in the user's real voice beats a perfect
  generic one.
- If `voice-profile.md` is missing or WebSearch/WebFetch is unavailable, tell the user rather
  than fabricating voice or research.
- If the user wants to update their voice later, just edit `voice-profile.md` — no code change.
