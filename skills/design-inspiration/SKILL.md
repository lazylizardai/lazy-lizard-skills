---
name: design-inspiration
description: "Fetch live design inspiration from curated websites (Awwwards, Toolfolio, Andrew Reff, One Page Love, Foundry, and user-added sites) for any creative project. Use this skill whenever the user works on website design, landing pages, UI/UX, fonts, typography, color palettes, branding, portfolios, presentations, pitch decks, visual identity, or any task where design quality and visual reference matter. Also triggers on: 'inspiratie', 'design reference', 'how should this look', 'mooie websites', 'font ideas', 'layout inspiration', 'look and feel', 'visual direction', 'design trends', or when the user is building something visual and could benefit from seeing real-world examples — even if they don't explicitly ask for inspiration."
---

# Design Inspiration

You have access to a curated set of design inspiration websites. Your job is to use these as active resources — not just a list to recite, but sites to visit, scrape for examples, and reference when helping with creative work.

## How it works

### 1. Load the site list

Read `references/sites.json` (relative to this skill's directory) to get the current list of inspiration sources. Each entry has a name, URL, categories, and what it's best for. The user can add or remove sites — treat this file as the source of truth.

### 2. Match sites to the task

When the user is working on something creative, figure out which sites are most relevant:

- **Landing page or SaaS site?** → One Page Love, Awwwards
- **Portfolio or personal brand?** → Toolfolio, Andrew Reff
- **Typography or font choices?** → Andrew Reff, Awwwards
- **Experimental / 3D / interactive?** → Foundry
- **General "make it look good"?** → Start with Awwwards for trends, then narrow down

Don't overthink this — if in doubt, Awwwards is a solid default for most web design tasks.

### 3. Actively fetch inspiration

This is the key differentiator of this skill. Don't just say "check Awwwards." Actually visit the relevant sites using WebFetch or browser tools and extract useful information:

- **Trending designs** — What's winning awards or featured right now?
- **Layout patterns** — How are similar sites structured?
- **Color palettes** — What color schemes are popular in this space?
- **Typography** — What fonts and type treatments are trending?
- **Specific examples** — Find 2-3 concrete sites that match what the user is building

When fetching, be practical. Not every page will render perfectly — grab what you can (titles, descriptions, featured site names, categories) and move on. The goal is to give the user concrete, current references rather than generic advice.

### 4. Present inspiration concisely

When sharing what you found, keep it actionable:

- Name the specific sites/designs you found relevant and why
- Note any patterns you spotted (e.g., "most trending SaaS sites right now use large serif headings with minimal color")
- If the user is building something, suggest how to apply what you found
- Link directly to the inspiration sources so the user can explore further

Don't write a research paper — a few targeted examples with clear takeaways are worth more than an exhaustive list.

## Managing the site list

The user can ask to add or remove sites at any time. When they do:

1. Read the current `references/sites.json`
2. Add/remove the entry with appropriate metadata (name, url, category, description, best_for)
3. Write the updated file back
4. Confirm the change

If the user mentions a new design resource they like, proactively offer to add it to the list.

## When NOT to fetch

Sometimes the user just wants a quick reference or is asking which sites you know about. In that case, just list the sites from `sites.json` without visiting them. Use your judgment — if the user says "what inspiration sites do we have?" that's a list request. If they say "I'm designing a landing page, show me what's trending" that's a fetch request.
