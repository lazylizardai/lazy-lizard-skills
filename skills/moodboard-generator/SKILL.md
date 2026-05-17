---
name: moodboard-generator
description: >
  Fetch live design inspiration from 5 curated sites (Awwwards, Toolfolio, Andrew Reff,
  One Page Love, Foundry Basement) and compile an HTML moodboard with trends, color palettes,
  typography, and layout patterns. Use this skill whenever the user works on ANY design-related
  task: website design, logo creation, branding, color palette selection, font choices, UI/UX
  decisions, landing page design, visual identity, style guides, or moodboards. Also triggers
  on: "inspiratie", "design trends", "hoe moet het eruitzien", "welke stijl", "moodboard",
  "look and feel", "visual direction", "website stijl", "kleuren kiezen", "font kiezen",
  "design reference", "wat is mooi", "laat me voorbeelden zien". Even if the user doesn't
  explicitly ask for inspiration, use this skill when a design decision could benefit from
  real-world references.
---

# Design Inspiration Skill

You help the user gather design inspiration from 5 curated websites and compile findings into a visual HTML moodboard. This is especially valuable at the start of any design project or when making visual decisions — real-world references lead to better outcomes than designing in a vacuum.

## Inspiration Sources

Each site has a different strength. Use the right ones for the task at hand:

| Site | URL | Best For |
|------|-----|----------|
| **Awwwards** | https://www.awwwards.com | Award-winning websites, cutting-edge trends, animation/interaction patterns |
| **Toolfolio** | https://toolfolio.io | Portfolio designs, clean layouts, tool/SaaS landing pages |
| **Andrew Reff** | https://andrewreff.com | Designer portfolio craft, typography, personal brand expression |
| **One Page Love** | https://onepagelove.com | Single-page designs, templates, focused storytelling layouts |
| **Foundry Basement** | https://foundry.basement.studio | 3D/WebGL, experimental/interactive design, bold creative expression |

## Workflow

### Step 1: Understand the Design Context

Before fetching inspiration, clarify what the user needs. Ask (if not already clear):
- What type of project? (website, logo, landing page, branding, etc.)
- What industry/vibe? (professional, playful, luxury, minimal, etc.)
- Any existing brand colors or fonts to work with?

Keep it to 1-2 questions max — don't slow the user down.

### Step 2: Fetch Inspiration (Live Scraping)

Try to visit the relevant sites using `WebFetch` or browser tools. Focus on:

**Awwwards** — Check the homepage or `/websites/sites-of-the-day/` for recent winners:
- Note: color schemes, typography choices, layout patterns, interaction styles
- Look for sites in the same industry as the user's project

**Toolfolio** — Browse for portfolio and SaaS examples:
- Note: card layouts, hero sections, navigation patterns

**One Page Love** — Check for relevant one-page templates and examples:
- Note: storytelling flow, CTA placement, section transitions

**Andrew Reff** — Study the portfolio itself as a design reference:
- Note: typography pairing, whitespace usage, personal branding approach

**Foundry Basement** — Check for experimental/3D design approaches:
- Note: creative use of WebGL, bold color choices, immersive experiences

**If scraping fails** (blocked, timeout, etc.), don't get stuck. Move to the fallback guide in `references/fallback-guide.md` and tell the user which sites to check manually with specific things to look for.

### Step 3: Compile the HTML Moodboard

Generate a single self-contained HTML file that serves as a visual moodboard. The moodboard should include:

1. **Project Header** — What this moodboard is for
2. **Color Palettes** — Extracted or suggested palettes with hex codes, shown as visual swatches
3. **Typography Suggestions** — Font pairings with Google Fonts links and live previews
4. **Layout Patterns** — Descriptions of relevant layout approaches with sketched wireframes (CSS/SVG)
5. **Inspiration Links** — Direct links to specific examples found, with brief notes on what to look at
6. **Mood/Vibe Section** — Keywords, textures, and visual direction summary
7. **Recommendations** — Your top 3 actionable design suggestions based on what you found

Use the HTML template structure from `references/moodboard-template.md` as a starting point.

**Style the moodboard itself beautifully** — it should feel like a design artifact, not a data dump. Use:
- Clean grid layout with CSS Grid
- Subtle shadows and rounded corners
- A neutral background that lets the content breathe
- Google Fonts for the moodboard's own typography

### Step 4: Save and Present

Save the HTML moodboard to the user's workspace folder and provide a `computer://` link.

Keep your summary brief — the moodboard speaks for itself. Just mention:
- How many sites you successfully checked
- 1-2 standout findings
- Link to the file

## Important Notes

- **Be honest about what you found.** If a site was unreachable, say so. Don't fabricate trends.
- **Tailor to the project.** A Curaçao restaurant site needs different inspiration than a SaaS dashboard.
- **Include both safe and bold options.** Give the user a range — something proven and something adventurous.
- **Respect the user's existing brand.** If they already have colors/fonts, work with those, not against them.
- **Language:** Follow the user's language. If they speak Dutch, the moodboard text should be in Dutch.
