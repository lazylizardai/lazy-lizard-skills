---
name: viral-short-video-creator
description: Create viral, SILENT short-form video concepts (TikTok, Reels, YouTube Shorts, 15-60s) in the style of Pingu, Tom & Jerry, and Angry Birds Toons — no voice-over, no dialogue, no on-screen text. Use this skill whenever the user asks for a short video idea, viral cartoon short, silent animation, brainrot-style loop, feel-good cartoon, Pingu-style script, Tom & Jerry-style script, TikTok cartoon, Reels sketch, 2D animation short, or any scripted video aimed at TikTok/Shorts/Reels. Also triggers on "short video", "TikTok video", "Reels", "brainrot", "feel-good video", "silent cartoon", "no-talk video", "wordless animation", "hook", "retention", "viral short", "nano-banana", "Higgsfield", "Seedance", "BollyToons", or any request for scene-by-scene visual prompts. Always produces silent-first scripts built around visual hooks, slapstick escalation, feel-good payoff, and a loop cue — with image prompts and Higgsfield Seedance video prompts for every scene.
---

# viral-short-video-creator

Build silent, slapstick, feel-good short-form videos that stop the scroll.

Think Pingu, Tom & Jerry, Angry Birds Toons: **no voice-over, no dialogue, no on-screen text**. Only visuals, SFX, and optional light music. Language-agnostic — the same file lands in NL, US, BR, JP, MENA without translation.

## Hard rules — never break these

1. **No spoken words. Anywhere.** No voice-over. No character dialogue. No subtitles.
2. **No on-screen text.** Minor exception: a single "?" or "!" floating above a character's head, Pingu-style.
3. **No grotesque violence.** Tom & Jerry-level bonks max. No blood, no real harm, no trauma.
4. **Must end feel-good.** A truce, a smile, a warm landing. Viewer exhales.
5. **Every video must LOOP.** The final shot cues back to the first. Rewatches = algorithm fuel.
6. **Visual hook in second 0.** Something absurd, satisfying, or uncanny is ON SCREEN before the viewer's thumb even moves.

## The 6-step workflow

When the user asks for a video, walk through these in order. Don't skip.

### Step 1 — Niche & hoek
Pick a main niche → bend to an adjacent sub-niche the market is not saturating. Frame it from ONE specific character's physical comedy, not from a topic. See `references/niche-bending.md`.

### Step 2 — Hook engineering
Design the first 3 seconds as a single visual sight-gag that requires zero context. The viewer understands what's weird before they understand what the video is about. See `references/visual-hook.md`.

### Step 3 — Character design
Two or three characters max. Each one has:
- One signature silhouette (Pingu-round, pear-shaped, stick-thin, etc.)
- One signature SFX noise (noot-noot, hmph, eh-EH)
- One signature physical move (little hops, cane taps, eyebrow dance)
- A visual running gag (upside-down newspaper, bowl-hat, etc.)

See `references/character-design.md`.

### Step 4 — Beat structure (silent 6-beat)
Divide the video into 6 beats × ~10s each (for a 60s video), or 4 beats × ~8s for 30s. Each beat escalates visually. See `references/silent-beat-structure.md`.

### Step 5 — Scene pipeline
For every beat, write:
- **IMAGE PROMPT** (nano-banana / Higgsfield Popcorn) — full style lock + character tags repeated verbatim
- **MOTION PROMPT** (Higgsfield Seedance / DoP) — what moves, how long, camera behavior. **Only Higgsfield — no Grok, no Kling, no Runway.**
- **SFX cue** — no words, only sounds and Pingu-grunts

See `references/scene-pipeline.md`.

> **BollyToons characters** (Meera, Mogamba Jr., Ray) have Higgsfield Soul 2.0 character IDs for zero-drift consistency. When using these characters, add `character_ids` to the Higgsfield API call — see pipeline docs.

### Step 6 — Landing & loop
The final 5–10s MUST:
- Resolve with a warm payoff (characters on the same side)
- Include a rewatch hook (a detail that references the opening)
- Cut-loop to the first frame

See `references/feel-good-landing.md`.

## Output structure — always this order

Produce the deliverable in exactly this order:

1. **THE PITCH** — one paragraph, logline-style, ending with a "one location, N characters, zero words" line.
2. **HOOK (0:00–0:03)** — second-by-second description of the first three seconds.
3. **CHARACTER DESIGN** — each character: silhouette, SFX, signature move, running gag.
4. **STYLE LOCK** — one paragraph, to be pasted verbatim into every image prompt.
5. **BEATS × DURATION** — numbered beats. Each beat has IMAGE PROMPT + MOTION PROMPT + SFX. No voice-over lines anywhere.
6. **WHY THIS KEEPS PEOPLE WATCHING** — 4–6 retention mechanics (visual escalation, running gags, loop, payoff, rewatch bait).
7. **CAPTION + HASHTAGS + MUSIC NOTE** — caption is one short line (optional emoji). Music is either "SFX-only" or "light piano/xylophone, no lyrics".

## Banned patterns — if you catch yourself doing these, stop and redesign

- "Hook / Setup / Buildup / Climax / CTA" text labels AS SCRIPT SECTIONS. Silent videos express these beats through *visual escalation*, not through labeled prose blocks.
- Any line like *VOICE-OVER:*, *NARRATOR:*, *"he says"*, *"she whispers"*. Nuke on sight.
- Motivational taglines — "you got this", "don't give up", "hustle". Wrong genre.
- Explaining the joke in text. If it needs words, the gag isn't visual enough → redesign.
- Ending on "like and subscribe". The LOOP is the CTA.
- Drama, trauma, horror framings. Wrong skill.

## Confirming with the user

Before producing, ask ONE combined clarifying question if any of these are missing:
- **Target platform** (TikTok / Reels / Shorts — default TikTok)
- **Length** (15 / 30 / 45 / 60s — default 60)
- **Tone** (pure Pingu cute / Tom & Jerry slapstick / Angry Birds mischief — default Tom & Jerry)
- **Characters** (user ideas, or invent?)
- **Setting** (kitchen / park / office / invented?)

If the user gives only a topic, invent the rest and state assumptions in one line at the top of the output.

## References (load as needed — lazy load, don't dump all)

- `references/niche-bending.md` — main → sub-niche logic
- `references/visual-hook.md` — second-0 sight-gag patterns
- `references/character-design.md` — silhouette + SFX + signature move + running gag
- `references/silent-beat-structure.md` — 4-beat and 6-beat templates, escalation ladder
- `references/scene-pipeline.md` — image/motion/SFX prompt formatting
- `references/feel-good-landing.md` — payoff + loop patterns
- `references/competitor-analysis.md` — scrape Pingu/T&J/Angry Birds reference reels

## Assets

- `assets/master-prompt-template.md` — fill-in-the-blank scene prompt template (no voice-over fields)
