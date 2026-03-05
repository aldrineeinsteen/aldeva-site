# Copilot Instructions — Ald Eva (Hugo + Blowfish)

## Site goals
- Domain: aldeva.co
- Hugo + Blowfish theme
- Modern minimalist look (brand site, not blog-first)
- Main sections:
  - /organics (colonies + transparency)
  - /craft (crochet)
  - /about (Ald resume + Eva CV)

## Content model
### Colonies (hives)
- Stored as Markdown pages under: /content/organics/colonies/
- Each hive page MUST include YAML front matter:
  hive_id: "H1"
  queen_year: 2025
  location: "Hatfield, Hertfordshire"
  hive_type: "National"
  status: "Strong"   # Strong | Moderate | Needs attention
  temperament: "Calm" # Calm | Lively | Defensive
  last_updated: 2026-03-04

### Inspections
- Stored as Markdown pages under: /content/inspections/
- Each inspection MUST include YAML front matter:
  date: YYYY-MM-DD
  hive_id: "H1"
  queen_seen: true/false
  eggs_seen: true/false
  brood_pattern: "Good"|"Mixed"|"Patchy"
  stores_honey: "Low"|"Moderate"|"Good"
  stores_pollen: "Low"|"Moderate"|"Good"
  varroa_count: integer
  actions: [ ... ]
  public_summary: "short sentence"
  tags: [ "inspection", "hive-H1" ]

## Rendering requirements
- /organics/ must list all colonies as card grid (auto from /organics/colonies/ pages).
- Each colony page must show:
  1) Latest inspection (most recent by date)
  2) Recent inspections (last 7) with badges
  3) Link to full inspection history filtered to that hive

## Filtering logic in Hugo templates
- Use Hugo Go templates only.
- Filter inspections with: where site.RegularPages "Section" "inspections" then where Params.hive_id == .Params.hive_id
- Sort newest first by Date.

## Profiles
- /about/ has two cards: Ald (resume) and Eva (CV), linking to /about/ald and /about/eva.
- Resume/CV pages are clean markdown with headings and lists; no external embeds.

## Style
- Use Blowfish/Tailwind utilities when possible.
- Prefer cards, subtle borders, rounded corners, whitespace, badges for attributes.
- Avoid heavy JS; keep it static.

## Output rules
- Always include exact file paths for generated templates.
- Provide complete, working code blocks.