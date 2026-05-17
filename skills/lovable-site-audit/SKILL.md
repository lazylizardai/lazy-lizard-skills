---
name: lovable-site-audit
description: "Autonomous end-to-end site audit and fix workflow for Lovable projects. Crawls the live site, identifies design/UX/SEO/navigation issues, creates credit-efficient Lovable prompts, sends them via MCP, monitors builds, publishes, and verifies fixes on production. Use this skill whenever the user says 'review the site', 'check the website', 'audit the landing page', 'fix the site', 'update SEO', 'check all URLs', 'deploy to production', 'publish changes', 'site nalopen', 'kijk naar de site', or any request that involves inspecting a Lovable-hosted site and pushing improvements through the Lovable build pipeline. Also triggers when the user wants to send prompts to Lovable autonomously, batch site fixes, or do a full publish cycle."
---

# Lovable Site Audit & Deploy

An autonomous workflow that takes a Lovable project from "something's off" to "verified and live" — without bouncing tasks back to the user.

## Why this skill exists

Manually auditing a site, writing Lovable prompts, sending them, waiting for builds, publishing, and verifying is a 30-minute multi-tool dance. This skill chains it all together so the user can say "review and fix the site" and come back to a deployed result.

The skill is credit-aware: it batches related fixes into minimal prompts (following the Lovable credit rules) and warns before expensive operations.

## Prerequisites

Before starting, confirm you have:

1. **Lovable MCP tools** — `send_prompt`, `get_design_status`, `read_recent_message_history`, `read_artifact_files`, `list_version_history`, `get_editor_id_from_url`
2. **Browser tools** — Claude in Chrome or similar for visual inspection and live-site verification
3. **The Lovable project URL or editor ID** — either from memory, the user, or project config

If you don't have the editor ID, ask once: "What's the Lovable project URL?" Then resolve it via `get_editor_id_from_url` and remember it for the session.

---

## Workflow

### Phase 1: Reconnaissance

**Goal:** Build a complete picture of what's wrong before touching anything.

1. **Check current Lovable state**
   - Call `get_design_status(editorId)` to see if a build is already running
   - Call `read_recent_message_history(editorId)` to see what was last sent/built
   - If a build is in progress, wait for it to finish before proceeding

2. **Crawl the live site visually**
   - Navigate to the production URL (e.g., reynardai.com)
   - Scroll through every section systematically, top to bottom
   - Take note of: layout issues, empty gaps, broken styling, missing elements, alignment problems

3. **Test all key URLs**
   - Click every navigation link and verify it lands correctly
   - Check for 404s, wrong scroll positions, routes that require auth unexpectedly
   - Document: URL tested → result (works / 404 / wrong section / auth required)

4. **Check SEO fundamentals**
   - Inspect `<title>`, `<meta description>`, Open Graph tags, canonical URLs
   - Check for missing alt text on images
   - Verify structured data if applicable

5. **Review design consistency**
   - Colors match the design system? (dark mode layers, teal primary, amber secondary)
   - Typography correct? (Plus Jakarta Sans headings, Inter body, JetBrains Mono code)
   - Glassmorphism cards rendering properly?
   - No pure white anywhere?
   - Max 3 glow elements per screen?

6. **Compile the issue list**
   - Categorize each issue: Layout / Navigation / SEO / Design / Content / Functionality
   - Assign priority: P1 (blocks users), P2 (degrades experience), P3 (polish)
   - Group related issues that can be fixed in a single Lovable prompt

### Phase 2: Prompt Engineering

**Goal:** Create the fewest, most effective Lovable prompts to fix everything.

**Credit rules to follow:**
- Max 3 features/changes per prompt (Lovable works best with focused requests)
- Always specify what should NOT change (protect working features)
- Include exact design specs (colors, fonts, spacing values)
- Include exact URLs and link targets
- Group changes by affected component/page

**Prompt structure template:**

```
## What to change — ONLY [scope]. Do NOT touch [protected areas].

### 1. [CHANGE TITLE]
[Detailed description with exact specs, colors, links, conditional logic]

### 2. [CHANGE TITLE]
[...]

### IMPORTANT CONSTRAINTS:
- Do NOT change [list protected areas]
- Do NOT modify [list protected functionality]
- ONLY change: [explicit list of what changes]
- Keep [list things to preserve] exactly as they are
```

**Before sending, verify:**
- [ ] Is the prompt specific enough that Lovable won't misinterpret it?
- [ ] Are design specs included (hex colors, font names, spacing)?
- [ ] Are URLs complete and correct?
- [ ] Are constraints clear about what NOT to change?
- [ ] Is this max 3 changes? If more, split into multiple prompts.

**Credit estimation:** Tell the user approximately how many credits each prompt will cost:
- Simple text/link changes: ~1 credit
- New component (nav bar, section): ~1-2 credits
- Multiple structural changes: ~2-3 credits
- If total exceeds 5 credits, flag it and ask if the user wants to proceed

### Phase 3: Send & Monitor

**Goal:** Send prompts to Lovable and wait for builds to complete.

1. **Pre-flight check**
   - Call `get_design_status(editorId)` — confirm `isGenerating: false`
   - If generating, wait and poll every 60 seconds

2. **Send the prompt**
   - Call `send_prompt(editorId, prompt)`
   - Immediately inform the user: "Prompt verstuurd. Lovable is aan het bouwen, dit duurt 2-10 minuten."

3. **Poll for completion**
   - Call `get_design_status(editorId)` every 60 seconds
   - Do NOT poll more frequently — Lovable builds take time
   - Maximum wait: 10 minutes. If still generating after 10 minutes, alert the user.

4. **Review the build result**
   - Call `read_recent_message_history(editorId)` to see Lovable's response
   - If Lovable reports errors or asks clarifying questions, address them
   - If multiple prompts are queued, repeat steps 1-4 for each

### Phase 4: Publish

**Goal:** Deploy the changes to all production domains.

1. **Navigate to the Lovable publish panel**
   - Use browser tools to go to the Lovable project editor
   - Open the Publish panel (usually top-right)
   - Click "Update" to publish to all connected domains

2. **Wait for deployment**
   - Lovable deploys to all domains simultaneously (e.g., reynard.lovable.app, reynardai.com, www.reynardai.com)
   - Wait for the publish confirmation

3. **Inform the user**
   - "Gepubliceerd naar alle domeinen. Ik ga nu verifiëren."

### Phase 5: Verification

**Goal:** Confirm every fix works on the live production site.

1. **Hard refresh the production URL** (not Lovable preview — the actual domain)
2. **Walk through each fix from Phase 1:**
   - [ ] Navigation links work and land correctly
   - [ ] Layout issues resolved (no gaps, overlaps, broken sections)
   - [ ] SEO meta tags present and correct (view page source)
   - [ ] Design consistency maintained
   - [ ] No regressions introduced
3. **Test on mobile viewport** if responsive issues were part of the audit
4. **Report results to user:**
   - Which fixes are confirmed working
   - Any remaining issues
   - Suggestions for follow-up improvements

---

## Edge Cases & Troubleshooting

**Lovable build fails or loops:**
- Max 2 retry attempts per prompt
- If the same error occurs twice, stop and suggest a GitHub code fix instead
- Flag to user: "Dit veroorzaakt een debug loop. Beter om dit via GitHub op te lossen, scheelt credits."

**Lovable is already generating:**
- Never send a new prompt while `isGenerating: true`
- Wait for the current build to finish, review the result, then decide if your prompt is still needed

**Protected pages accidentally modified:**
- Always include explicit constraints in every prompt
- If workspace pages get touched, immediately send a revert prompt

**User has limited credits:**
- Ask how many credits they have before starting
- Prioritize P1 fixes first
- Suggest GitHub code edits for simple CSS/text changes: "Dit is 1 regel CSS, doe het in GitHub, bespaar een credit"
- Remind about daily free credits: "Heb je vandaag je 5 gratis credits al opgehaald?"

---

## Reynard AI Design System Reference

When writing prompts, always use these exact specs:

**Dark mode layers:** `#07070b` → `#0c0c14` → `#12121e` → `#1a1a2a` → `#222236`
**Primary (actions):** `#14b8a6` (teal)
**Secondary (warmth/streaks):** `#fbbf24` (amber)
**Text:** `#f0f0f5` (primary), `#a0a0b8` (secondary), `#62627a` (muted)
**Never:** pure white (`#ffffff`)
**Typography:** Plus Jakarta Sans (headings), Inter (body), JetBrains Mono (code)
**Effects:** Glassmorphism cards, max 3 glow elements per screen

---

## Output Behavior

- Work autonomously — don't ask the user to run commands or click buttons
- Communicate in Dutch unless the user writes in English
- Lovable prompts are always written in English
- Be direct about credit costs before sending expensive prompts
- After verification, provide a concise summary — no need to re-explain every change
