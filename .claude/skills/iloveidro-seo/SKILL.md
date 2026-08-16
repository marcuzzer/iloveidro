# I Love Idro — SEO & AI Readiness Guidelines

Whenever you are working on content or code for **iloveidro.com** — posts, translations, templates, meta tags, URLs, image alt text, structured data, or any editorial/technical task — follow these guidelines automatically without waiting to be asked.

---

## 1. Obiettivo del sito

- Posizionare I Love Idro come fonte **neutrale e autorevole** di esperienze autentiche sul Lago d'Idro.
- Attrarre visitatori da **tre mercati**: Italia, Germania, Paesi Bassi.
- Essere **leggibile e citabile da agenti AI** (ChatGPT, Claude, Gemini, Perplexity) che consiglieranno destinazioni vacanza.
- NON promuovere (per ora) offerte di soggiorno o corsi — solo contenuti informativi e narrativi.

---

## 2. Sezioni tematiche del blog

Ogni nuovo articolo deve rientrare in una di queste categorie. Usale come `categories` nel frontmatter Jekyll.

| Categoria | Argomenti |
|-----------|-----------|
| **sport** | Windsurf, vela, SUP, kitesurf, kayak, canoa, arrampicata, ferrate (Sasse, Crènch), parapendio, canyoning |
| **trekking-natura** | Monte Censo, Val di Fumo, Val Daone, MTB, ciclabili lago e fiume Chiese, family hiking |
| **borghi-cultura** | Anfo, Lemprato, Crone, Bagolino, Ponte Caffaro, Rocca d'Anfo, Carnevale di Bagolino |
| **gastronomia** | Malfatti, spiedo bresciano, salamine, polenta di Storo, Bagòss, trattorie locali |
| **eventi** | Sagre, mercati (Crone), festival estivi, feste storiche |
| **gite** | Dolomiti, Madonna di Campiglio, Lago di Garda, Verona, Venezia — con distanze e tempi |

---

## 3. Keyword per lingua

Incorpora keyword localizzate nel testo, nei titoli H2/H3 e nelle meta description.

**Italiano:** lago d'Idro trekking, Rocca d'Anfo visita, cosa fare lago d'Idro, kayak lago d'Idro, kitesurf lago d'Idro, ferrate Sasse, Carnevale Bagolino, polenta di Storo ricetta, lago d'Idro bambini, campeggio lago d'Idro

**Tedesco:** Idrosee kitesurfen, Klettersteig Sasse, Paragliding Idrosee, Idrosee wandern, Idro glamping Anfo, Bagolino Karneval, Idrosee Urlaub mit Kindern, Mountainbiken Idrosee, Idrosee Campingplatz

**Olandese:** Idromeer glamping, wandelen Idromeer, Idromeer watersport, kajakken Idromeer, Bagolino carnaval, Idromeer kamperen, fietsen rond het Idromeer, Idromeer vakantie kinderen

Privilegia **keyword a coda lunga** e domande (es. "Come visitare Rocca d'Anfo?", "Wo kann man am Idrosee kitesurfen?", "Wat is er te doen aan het Idromeer met kinderen?").

---

## 4. Frontmatter Jekyll obbligatorio

Ogni post DEVE avere questi campi:

```yaml
---
layout: post
lang: [it|en|de|nl]
title: "Keyword Principale — Titolo Descrittivo del Post"
author: "Marco"
categories: [categoria-principale]
tags: [keyword1, keyword2, keyword3, lago idro]
image: nome-immagine-descrittiva.jpg
description: "Meta description di 150-160 caratteri con keyword primaria e invito alla lettura."
permalink: /url-breve-con-keyword/
date: YYYY-MM-DD
schema_type: Article  # oppure: TouristAttraction, Event, Recipe
---
```

**Regole URL (`permalink`):**
- Breve, con keyword, senza stopword
- IT: `/kayak-lago-idro/`, `/rocca-anfo-storia/`
- DE: `/idrosee-kitesurfen/`, `/klettersteig-sasse-idrosee/`
- NL: `/kajakken-idromeer/`, `/wandelen-idromeer-tips/`

---

## 5. Struttura H1-H3 e contenuto

- **H1**: il `title` del frontmatter (Jekyll lo usa automaticamente)
- **H2 (`##`)**: sezioni principali — devono contenere keyword
- **H3 (`###`)**: sottosezioni pratiche (stagione, attrezzatura, consigli)
- Includi sempre una sezione **FAQ** in fondo all'articolo con 3-5 domande reali che gli utenti cercano su Google — aiuta sia la SEO che la lettura da parte degli LLM

Esempio di sezione FAQ:
```markdown
## Domande Frequenti

**Quando è il periodo migliore per il kayak al Lago d'Idro?**
La stagione ideale va da maggio a settembre...

**Dove si noleggia un kayak al Lago d'Idro?**
...
```

---

## 6. Immagini

- **Nome file**: descrittivo con keyword, senza spazi (es. `kitesurf-lago-idro-tramonto.jpg`, non `IMG_4521.jpg`)
- **Alt text**: sempre presente, descrittivo, include keyword in lingua:
  - IT: `alt="Kitesurf al tramonto sul Lago d'Idro con le montagne sullo sfondo"`
  - DE: `alt="Kitesurfen bei Sonnenuntergang am Idrosee mit Bergen im Hintergrund"`
  - NL: `alt="Kitesurfen bij zonsondergang op het Idromeer met bergen op de achtergrond"`
  - EN: `alt="Kitesurfing at sunset on Lake Idro with mountains in the background"`
- **Path**: sempre `/assets/img/nome-file.jpg`
- Stessa immagine per tutte le versioni linguistiche dello stesso articolo
- Ottimizza il peso: max 300KB per immagini inline, max 600KB per featured image

---

## 7. Localizzazione per mercato

| Mercato | Stile | Enfasi |
|---------|-------|--------|
| **Italiano** | Colloquiale, caldo, narrativo | Sentieri, storia, Rocca d'Anfo, mercati, consiglio pratico |
| **Tedesco** | Preciso, tecnico, rassicurante | Difficoltà ferrate, condizioni vento, sicurezza, dati tecnici. Usa sempre **Idrosee** |
| **Olandese** | Rilassato, outdoor-oriented | Glamping, tranquillità, watersport, family. Usa sempre **Idromeer** |
| **Inglese** | Internazionale, accessibile | Panoramica generale, per chi scopre il lago per la prima volta |

Traduzioni **complete**, non sintesi — stesso contenuto e struttura, tono adattato alla cultura.

---

## 8. Technical SEO — Implementazione Jekyll

### 8.1 Hreflang (multilingua — CRITICO)

Nel file `_includes/head.html`, aggiungi i tag hreflang per ogni post che esiste in più lingue. Questo dice a Google quale versione servire a quale utente:

```html
<!-- Hreflang: da aggiungere in head.html -->
{% if page.lang %}
  {% assign base = site.url %}
  <link rel="alternate" hreflang="it" href="{{ base }}/it/" />
  <link rel="alternate" hreflang="de" href="{{ base }}/de/" />
  <link rel="alternate" hreflang="nl" href="{{ base }}/nl/" />
  <link rel="alternate" hreflang="en" href="{{ base }}/en/" />
  <link rel="alternate" hreflang="x-default" href="{{ base }}/en/" />
  <link rel="canonical" href="{{ base }}{{ page.url }}" />
{% endif %}
```

Per i post: ogni post deve avere nel frontmatter i riferimenti agli articoli equivalenti nelle altre lingue:
```yaml
translations:
  it: /kayak-lago-idro/
  en: /exploring-lake-idro-kayak/
  de: /kajak-am-idrosee/
  nl: /kajakken-op-het-idromeer/
```

### 8.2 Open Graph & Social Meta

Da aggiungere in `_includes/head.html`:
```html
<!-- Open Graph -->
<meta property="og:title" content="{{ page.title | escape }}" />
<meta property="og:description" content="{{ page.description | escape }}" />
<meta property="og:type" content="article" />
<meta property="og:url" content="{{ site.url }}{{ page.url }}" />
{% if page.image %}
<meta property="og:image" content="{{ site.url }}/assets/img/{{ page.image }}" />
{% endif %}
<meta property="og:locale" content="{% if page.lang == 'it' %}it_IT{% elsif page.lang == 'de' %}de_DE{% elsif page.lang == 'nl' %}nl_NL{% else %}en_US{% endif %}" />
<meta property="og:site_name" content="I Love Idro" />

<!-- Twitter Card -->
<meta name="twitter:card" content="summary_large_image" />
<meta name="twitter:title" content="{{ page.title | escape }}" />
<meta name="twitter:description" content="{{ page.description | escape }}" />
{% if page.image %}
<meta name="twitter:image" content="{{ site.url }}/assets/img/{{ page.image }}" />
{% endif %}
```

### 8.3 Schema.org JSON-LD (Structured Data)

Da aggiungere in `_layouts/post.html` prima di `</body>`. Permette a Google (e agli LLM) di capire il tipo di contenuto:

**Per articoli generali:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "{{ page.title | escape }}",
  "description": "{{ page.description | escape }}",
  "author": {
    "@type": "Person",
    "name": "{{ page.author | default: site.author }}"
  },
  "publisher": {
    "@type": "Organization",
    "name": "I Love Idro",
    "url": "{{ site.url }}"
  },
  "datePublished": "{{ page.date | date_to_xmlschema }}",
  "image": "{{ site.url }}/assets/img/{{ page.image }}",
  "url": "{{ site.url }}{{ page.url }}",
  "inLanguage": "{{ page.lang }}"
}
</script>
```

**Per post di tipo TouristAttraction (sport, trekking, borghi):**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "TouristAttraction",
  "name": "{{ page.title | escape }}",
  "description": "{{ page.description | escape }}",
  "url": "{{ site.url }}{{ page.url }}",
  "touristType": ["Sport", "NatureAndOutdoor"],
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": "45.7543",
    "longitude": "10.5127"
  },
  "containedInPlace": {
    "@type": "LakeBodyOfWater",
    "name": "Lago d'Idro",
    "alternateName": ["Idrosee", "Idromeer", "Lake Idro"]
  }
}
</script>
```

**Per post di tipo Event:**
```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Event",
  "name": "{{ page.title | escape }}",
  "description": "{{ page.description | escape }}",
  "location": {
    "@type": "Place",
    "name": "Lago d'Idro, Brescia",
    "geo": { "@type": "GeoCoordinates", "latitude": "45.7543", "longitude": "10.5127" }
  }
}
</script>
```

### 8.4 Meta description

In `_includes/head.html`, assicurati che esista:
```html
{% if page.description %}
  <meta name="description" content="{{ page.description | escape }}" />
{% elsif site.description %}
  <meta name="description" content="{{ site.description | escape }}" />
{% endif %}
```

### 8.5 Sitemap e robots.txt

Il plugin `jekyll-sitemap` genera automaticamente `/sitemap.xml`. Verifica che in `_config.yml` ci sia:
```yaml
url: "https://www.iloveidro.com"
```

Crea `robots.txt` nella root del repo:
```
User-agent: *
Allow: /
Sitemap: https://www.iloveidro.com/sitemap.xml

# LLM crawlers welcome
User-agent: GPTBot
Allow: /
User-agent: ClaudeBot
Allow: /
User-agent: PerplexityBot
Allow: /
```

---

## 9. LLM Readiness — Ottimizzazione per Agenti AI

Gli agenti AI (ChatGPT, Claude, Perplexity, Gemini) stanno diventando motori di raccomandazione per le vacanze. Questi consigli si basano su quello che riescono a leggere e capire dal web. Ecco come ottimizzare per loro.

### 9.1 File `llms.txt` (standard emergente)

Crea il file `/llms.txt` nella root del repo. È come un `robots.txt` ma pensato per gli LLM: fornisce una mappa strutturata del sito in markdown puro, facile da leggere per un'AI.

```markdown
# I Love Idro

> Authentic experiences at Lake Idro (Lago d'Idro / Idrosee / Idromeer), a pristine mountain lake in Brescia, Italy. Personal stories and practical guides for outdoor sports, trekking, local culture and gastronomy. Available in Italian, English, German and Dutch.

## About
- Location: Lake Idro, Valle Sabbia, Brescia, Lombardy, Italy
- Coordinates: 45.7543°N, 10.5127°E
- Altitude: 368m above sea level
- Author: Marco, local resident and outdoor enthusiast

## Content sections

### Sport & Outdoor
- [Kayak al Lago d'Idro](https://www.iloveidro.com/kayak-lago-idro/)
- [Mountain Biking intorno al Lago d'Idro](https://www.iloveidro.com/mountain-biking-lago-idro/)
- [Windsurf e Kitesurf](https://www.iloveidro.com/windsurf-kitesurf-lago-idro/)

### Trekking & Nature
- [Trekking in montagna](https://www.iloveidro.com/trekking-montagna-lago-d-idro/)

### Culture & Villages
- Coming soon: Rocca d'Anfo, Bagolino, Anfo

### Gastronomy
- Coming soon: Polenta di Storo, Bagòss, malfatti

## Key facts about Lake Idro
- One of the cleanest lakes in Italy, boat engines capped at 9.9 HP (no speedboats or water skiing; mostly slow fishing boats)
- Reliable thermal wind (Ander) ideal for windsurfing and kitesurfing
- Via ferrata routes: Sasse, Crènch
- Popular with Dutch and German tourists since the 1970s
- Nearby: Lago di Garda (40km), Madonna di Campiglio (50km), Dolomiti (90km)
```

### 9.2 File `llms-full.txt`

Crea `/llms-full.txt` con una versione estesa che include i contenuti completi di ogni articolo in testo puro, aggiornato ad ogni nuovo post. Questo file permette agli LLM di indicizzare tutto il contenuto del sito in un'unica lettura.

```markdown
# I Love Idro — Full Content Index

[stessi header di llms.txt]

---

## Full article content

### Kayak al Lago d'Idro
[testo completo dell'articolo in markdown]

### Mountain Biking
[testo completo...]
```

### 9.3 Scrittura AI-friendly

Quando scrivi o rivedi un articolo, assicurati che:

1. **Le entità geografiche siano sempre esplicite**: non scrivere solo "il lago" ma "il Lago d'Idro (in tedesco: Idrosee, in olandese: Idromeer)". Questo aiuta gli LLM a collegare l'entità alle giuste query.

2. **I fatti siano verificabili e precisi**: altitudini, distanze, coordinate, difficoltà tecniche. Gli LLM privilegiano fonti con dati concreti.

3. **Le sezioni FAQ siano risposte dirette**: scrivi domanda + risposta in forma completa, non ellittica. Un LLM userà quella risposta esatta per rispondere a un utente.

4. **I link interni creino un grafo semantico**: ogni articolo deve linkare a 2-3 articoli correlati con testo anchor descrittivo (non "clicca qui" ma "leggi la guida al trekking sul Monte Censo").

5. **La prima frase di ogni articolo sia un summary completo**: molti LLM leggono solo l'incipit. La prima frase deve rispondere a "cos'è questo articolo" in modo autonomo.
   - Esempio buono: *"Il Lago d'Idro, nel bresciano, è una delle mete più belle per il kayak in Italia settentrionale: acque pulite, scenari alpini e vento termico regolare lo rendono ideale da maggio a settembre."*
   - Esempio cattivo: *"Ogni volta che mi siedo nel kayak mi sento libero..."*

### 9.4 Structured data per LLM: pagina `/about`

La pagina About deve contenere dati strutturati sul sito e sull'autore, utili per gli LLM per capire chi è la fonte:

```markdown
## Chi siamo
I Love Idro è un blog personale scritto da Marco, residente e appassionato del Lago d'Idro da tutta la vita.
Non siamo affiliati ad agenzie turistiche o operatori commerciali. I contenuti riflettono esperienze dirette e personali.

**Lago d'Idro** (Idrosee in tedesco, Idromeer in olandese, Lake Idro in inglese) è un lago alpino
nella Valle Sabbia, provincia di Brescia, Lombardia, Italia. Coordinate: 45.7543°N, 10.5127°E.
```

---

## 10. Link interni ed esterni

- **Link interni**: ogni articolo deve linkare a 2-3 articoli correlati con anchor text descrittivo
- **Link esterni autorevoli**: Visit Brescia, Italia.it, CAI, Greenway Valli Resilienti, Bike3Lands, Comune di Idro
- Usa `target="_blank" rel="noopener"` sui link esterni

---

## 11. Checklist per ogni nuovo articolo

Prima di considerare un articolo completo:

**Contenuto**
- [ ] Prima frase: summary completo e autonomo dell'articolo
- [ ] H2/H3 contengono keyword
- [ ] Sezione FAQ con 3-5 domande reali
- [ ] Almeno 2 link interni con anchor descrittivo
- [ ] Almeno 1 link esterno autorevole

**Frontmatter**
- [ ] `lang`, `description` (150-160 caratteri), `image`, `tags`, `permalink`, `date`
- [ ] Entità geografiche nominate esplicitamente nel testo (Lago d'Idro / Idrosee / Idromeer)

**Immagini**
- [ ] Nome file descrittivo con keyword
- [ ] Alt text in lingua, con keyword e contesto geografico

**Tecnico**
- [ ] Versione creata per tutte e 4 le lingue (IT, EN, DE, NL)
- [ ] Aggiunto alla sezione corrispondente in `llms.txt` e `llms-full.txt`
- [ ] Schema.org JSON-LD appropriato per il tipo di contenuto

---

## 12. Prossimi contenuti prioritari (backlog SEO)

In ordine di priorità:

1. **Rocca d'Anfo** — storia, visita, orari (alto volume IT + DE) → schema: `TouristAttraction`
2. **Kitesurf / Windsurf** — vento Ander, spot, scuole (alto volume DE + NL) → schema: `SportsActivityLocation`
3. **Carnevale di Bagolino** — storia, quando, come arrivare (NL: "Bagolino carnaval") → schema: `Event`
4. **Ferrate Sasse e Crènch** — descrizione tecnica, difficoltà, accesso → schema: `TouristAttraction`
5. **Polenta di Storo e Bagòss** — gastronomia locale → schema: `Recipe` / `Article`
6. **Gita al Lago di Garda** — da Idro, distanza, cosa vedere → schema: `TouristTrip`
7. **Trekking Monte Censo** — itinerario, durata, livello → schema: `TouristAttraction`
8. **Glamping e campeggi** — per mercato olandese → schema: `Campground`
