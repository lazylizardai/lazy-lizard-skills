---
name: developer-collab-outreach
description: >
  Research a developer or open-source project, build a live proof-of-concept demo,
  write a collaboration proposal in the right tone, and post it as a GitHub issue or
  direct message — all the way through to follow-up replies. Use this skill whenever
  the user wants to reach out to a developer, maintainer, or technical creator about
  building something together, contributing to their project, or pitching a collaboration
  idea. Triggers on: "reach out to developer", "contact the maker of X", "propose
  collab with", "write GitHub issue for", "pitch this to a dev", "want to approach X
  for samenwerking", or any situation where the user has a tech idea and wants to find
  or contact a developer who could help bring it to life. Also use when the user gets
  a reply from a developer and needs help responding in the right tone.
---

# Developer Collaboration Outreach

This skill helps non-technical users (or anyone) reach out to open-source developers
and technical creators in a way that is honest, compelling, and well-matched to the
user's actual background and role. The goal is always a genuine, human message — not
a cold sales pitch.

## The core flow

1. **Understand what the user wants to build and why**
2. **Research the target developer**
3. **Build a live proof-of-concept** (if it helps show the idea)
4. **Write the proposal** in the right tone
5. **Post/send it** (GitHub issue, DM on X, Discord, etc.)
6. **Help with replies** when they come in

You don't always need all six steps. If the user already has a demo, skip step 3. If
they only need a reply drafted, jump straight to step 6.

---

## Step 1: Understand the user's idea and background

Before anything else, understand two things:

**The idea:** What does the user want to build? What would the collaboration look like?
What would the developer contribute vs. what would the user contribute?

**The user's background:** Are they a developer themselves? An enthusiast who uses AI
tools to build? Someone with business/product ideas but no technical skills? This
shapes the entire tone of the outreach. A non-technical person reaching out to a
developer is a completely different message than developer-to-developer.

Ask one focused question if anything is unclear. Don't over-interview.

---

## Step 2: Research the developer

When the user gives you a GitHub username, repo URL, or name, research:

- GitHub profile: bio, main projects, stars, activity
- README and documentation of their main project (especially extension points, roadmap, contributor guidelines)
- Social links: X/Twitter, Discord, personal site (check Linktree if present)
- Community: Discord server, existing issues/discussions on the repo

Use `WebFetch` on GitHub profile pages, raw README files, and documentation. Look for:
- How they prefer to be contacted (Discord, X, GitHub issues)
- Their stated vision for the project — what excites them
- Any "contribute" or "roadmap" sections that hint at openness to new features
- Their tone in existing issues and replies

**What to do with this:** Use it to write a proposal that genuinely speaks to their
vision, not a generic template. Reference specific things from their project. Mention
their roadmap if relevant.

---

## Step 3: Build a proof-of-concept demo (if it helps)

A live demo can transform a "nice idea" into a "let's actually do this." If the idea
is visual or interactive, building a quick prototype is almost always worth it.

**Good candidates for a demo:**
- UI/visual features ("I want agents to play football in 3D")
- Interactive tools, simulations, games
- Anything where "showing" is easier than "describing"

**Build approach:**
- Keep it simple: a single HTML file with vanilla JS/Three.js/CSS is usually enough
- Deploy it publicly so you can share a live link (Cloudflare Workers is ideal —
  use `wrangler deploy` via the Cloudflare MCP or bash)
- Label it clearly as a rough prototype, not production code

**If deploying to Cloudflare Workers:**
```bash
# Write worker.js that returns the HTML
# Write wrangler.toml with name + compatibility_date
# Run: CLOUDFLARE_API_TOKEN=<token> CLOUDFLARE_ACCOUNT_ID=<id> wrangler deploy --no-bundle
```

The live URL becomes a key asset in the proposal.

---

## Step 4: Write the collaboration proposal

This is the most important part. The proposal must feel human and honest.

### Tone calibration

The tone depends entirely on who the user is:

**If the user is non-technical / AI-assisted builder:**
Be explicit and proud about this. Don't pretend to be a developer. Something like:
"I'm not a developer myself — I'm someone full of ideas who uses AI to finally bring
them to life." This is honest, relatable, and often more compelling than faking
technical depth. Developers respect people who know their limits and are building
anyway.

**If the user is a developer:**
Peer-to-peer tone. Reference the code directly. Show you've read their docs.

**If the user is a business/product person:**
Lead with the value and vision. Reference technical architecture only as
context.

### What a good proposal includes

1. **A genuine compliment** — one specific thing about their project that you
   actually admire (don't be vague)
2. **Who you are** — honest and brief
3. **What you want to build** — the idea itself, clearly
4. **Why it fits their project** — connect it to their stated vision or roadmap
5. **What the collaboration would look like** — who does what
6. **A live demo link** (if you built one)
7. **A clear call to action** — Discord? X DM? A call?

### Markdown format for GitHub issues

Use clear headers, keep it scannable. Developers get a lot of noise in their inboxes
— make yours easy to skim and easy to say yes to.

### Length

Keep it focused. One page (in markdown) is ideal. If it needs to be longer, make sure
every section earns its place.

---

## Step 5: Post or send the proposal

**GitHub issue:** Guide the user to the repo's "New Issue" page. If there are issue
templates, "Feature request" is usually the right one. Provide copy-paste ready
title + body.

**X/Twitter DM:** Find the developer's handle (GitHub profile → X link → Linktree).
Provide a short, warm opening DM that references the GitHub issue if one was posted.

**Discord:** Only if their Discord is publicly listed. Don't cold-invite or guess
Discord handles. Ask the developer for their Discord handle via GitHub or X first.

---

## Step 6: Help with replies

When the developer replies — especially if positively — the tone of the follow-up
matters just as much as the initial pitch.

**Key principles:**
- Stay in the same honest voice as the initial message
- Acknowledge any prototype or test they've done ("That screenshot is incredible —
  you already built it!")
- Don't suddenly switch to technical jargon if the user isn't technical
- Be clear about next steps without being pushy
- If they ask to move to Discord/X, acknowledge that and ask for their handle if
  not already known

Always save important responses and collaboration status to memory
(`/sessions/.auto-memory/`) so the context persists across conversations.

---

## Common pitfalls to avoid

- **Overpromising technical contribution** — if the user can't code, don't write a
  proposal that implies they'll submit a PR
- **Generic proposals** — "I love your project" means nothing; "I love how you
  separated the retro office from the Phaser builder" means a lot
- **Wrong contact channel** — always check how the developer prefers to be contacted;
  posting a wall of text in the wrong place is counterproductive
- **Forgetting the demo** — a live link changes conversations; prioritize building one
  when the idea is visual

---

## Memory

After a successful outreach, save a project memory with:
- Developer name and handles
- What was proposed
- Their response
- Next steps
- Agreed task split
