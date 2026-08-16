# I Love Idro — Site Context & Content Guidelines

This skill activates whenever the user mentions **iloveidro**, **iloveidro.com**, **Lago d'Idro blog**, or asks to create, edit, or translate content for the site. Read this file first, then also read `.claude/skills/iloveidro-seo/SKILL.md` before producing any content or code.

---

## Site overview

- **URL:** https://www.iloveidro.com
- **Repo:** https://github.com/marcuzzer/iloveidro/ — cloned locally at `~/iloveidro`
- **Engine:** Jekyll static site with GitHub Pages
- **Author:** Marco — local resident, outdoor enthusiast, Lake Idro
- **Goal:** Authoritative, neutral travel blog about Lake Idro (Lago d'Idro) targeting Italian, German, and Dutch visitors. No commercial offers — only authentic experiences and practical guides.
- **Local dev:** `cd ~/iloveidro && bundle exec jekyll serve`
- **Publish:** `git add . && git commit -m "..." && git push`

---

## File structure

```
~/iloveidro/
├── _posts/
│   ├── it/          ← Italian posts (lang: it)
│   ├── en/          ← English posts (lang: en)
│   ├── de/          ← German posts (lang: de)
│   └── nl/          ← Dutch posts (lang: nl)
├── _includes/
│   ├── header.html  ← uses site.url (NOT site.github.url)
│   ├── footer.html
│   └── head.html    ← SEO meta tags, hreflang, OG
├── _layouts/
│   ├── home.html    ← filters posts by lang: where: "lang", current_lang
│   └── post.html    ← Schema.org JSON-LD, language switcher
├── assets/img/      ← all images go here
├── index.html       ← root redirect → /it/
├── index.it.md      ← Italian homepage (lang: it)
├── index.en.md      ← English homepage (lang: en)
├── index.de.md      ← German homepage (lang: de)
├── index.nl.md      ← Dutch homepage (lang: nl)
├── _config.yml      ← url: "https://www.iloveidro.com"
├── robots.txt
├── llms.txt         ← LLM site map (update with every new post)
└── llms-full.txt    ← full article text for AI indexing (update with every new post)
```

---

## Languages and names

| Lang | Code | Lake name | Audience |
|------|------|-----------|----------|
| Italiano | `it` | Lago d'Idro | Italian visitors |
| Deutsch | `de` | Idrosee | German visitors — precise, technical |
| Nederlands | `nl` | Idromeer | Dutch visitors — relaxed, outdoor |
| English | `en` | Lake Idro | International, first-time visitors |

Every new post **must be created in all 4 languages** with the same structure, adapted tone, and cross-linked via `translations:` in frontmatter.

---

## Mandatory post frontmatter

```yaml
---
layout: post
lang: it          # it | en | de | nl
title: "Keyword Principale — Titolo Descrittivo"
author: "Marco"
categories: [sport]   # sport | trekking-natura | borghi-cultura | gastronomia | eventi | gite
tags: [keyword1, keyword2, lago idro]
image: nome-immagine.jpg
description: "150-160 character meta description with primary keyword."
permalink: /url-keyword-breve/
date: YYYY-MM-DD
schema_type: Article   # Article | TouristAttraction | Event | Recipe
translations:
  it: /url-it/
  en: /url-en/
  de: /url-de/
  nl: /url-nl/
---
```

---

## Image rules

- Path always: `/assets/img/filename.jpg`
- Filename: descriptive with keyword, no spaces (e.g. `kayak-lago-idro-tramonto.jpg`)
- Alt text: in post language, with keyword and geographic context
- Same image file used across all language versions of the same post
- Max size: 300KB inline, 600KB featured

---

## Content rules

1. **First sentence** must be a complete standalone summary (LLMs often read only the opening)
2. **H2/H3 headings** must contain keywords
3. **FAQ section** at the end of every post — 3 to 5 real questions with complete answers
4. **2–3 internal links** per post with descriptive anchor text
5. **Geographic entities always explicit:** write "Lago d'Idro (Idrosee / Idromeer)" not just "il lago"
6. Translations are full translations — same structure and facts, tone adapted per market

---

## Content backlog (priority order)

1. Rocca d'Anfo — history, visit, opening hours (high volume IT + DE) → `TouristAttraction`
2. Kitesurf / Windsurf — Ander wind, spots, schools (DE + NL) → `SportsActivityLocation`
3. Carnevale di Bagolino — when, how to get there (NL: "Bagolino carnaval") → `Event`
4. Ferrate Sasse e Crènch — technical description, difficulty, access → `TouristAttraction`
5. Polenta di Storo e Bagòss — local gastronomy → `Recipe` / `Article`
6. Gita al Lago di Garda — from Idro, distance, what to see → `TouristTrip`
7. Trekking Monte Censo — route, duration, level → `TouristAttraction`
8. Glamping e campeggi — for Dutch market → `Campground`

---

## Key facts about Lake Idro (use in content)

- Alpine lake, Valle Sabbia, province of Brescia, Lombardy, Italy
- Coordinates: 45.7543°N, 10.5127°E — altitude: 368m above sea level
- One of the cleanest lakes in Italy — boat engines capped at 9.9 HP (no speedboats or water skiing; mostly slow fishing boats)
- Reliable thermal wind (Ander) ideal for windsurfing and kitesurfing
- Via ferrata routes: Sasse, Crènch
- Popular with Dutch and German tourists since the 1970s
- Nearby: Lago di Garda (40km), Madonna di Campiglio (50km), Dolomiti (90km)
- Villages: Anfo, Lemprato, Crone, Bagolino, Ponte Caffaro

---

## After creating or editing content

Always:
1. Update `llms.txt` — add new post URL and one-line description
2. Update `llms-full.txt` — add full post text
3. Verify image exists in `assets/img/` or create a placeholder
4. Run `bundle exec jekyll serve` locally to check for errors before pushing

For SEO implementation details (meta tags, Schema.org, hreflang, Open Graph) → read `.claude/skills/iloveidro-seo/SKILL.md`
