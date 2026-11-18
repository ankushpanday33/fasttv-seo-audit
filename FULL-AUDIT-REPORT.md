# SEO Audit: fasttv.app

Audit date: 18/11/2026 | Business type: Consumer streaming app: short-form micro-dramas (India) | Method: Crawler-eye smoke test, homepage plus 5 page checks, common-path probes, AI crawler matrix, one browser timing sample. Run inline, no subagents.

## SEO Health Score: 43 / 100

| Category | Weight | Score | Weighted |
|---|---|---|---|
| Technical SEO | 22% | 40 | 8.8 |
| Content Quality | 23% | 35 | 8.1 |
| On-Page SEO | 20% | 45 | 9.0 |
| Schema / Structured Data | 10% | 10 | 1.0 |
| Performance (CWV) | 10% | 80 | 8.0 |
| AI Search Readiness | 10% | 40 | 4.0 |
| Images | 5% | 85 | 4.2 |
| **Total** | | | **43** |

## Executive Summary

FastTV loads quickly and allows every crawler, but it gives search engines almost nothing to index: no sitemap, no robots.txt, no structured data and a catalogue that appears only after JavaScript runs. Giving each show a server-rendered page with a sitemap entry is the single change that opens organic search.

The score is held down by one root problem: **The site is built as an app shell. The shows are rendered in the browser and have no public, crawlable URLs, so there is nothing for a sitemap or schema to point at.**

Findings: 2 critical, 3 high, 2 medium, 3 low.

### Top 5 critical issues
1. **No sitemap.xml and no robots.txt (both return 404).** Neither /robots.txt nor /sitemap.xml exists.
2. **Show catalogue is invisible in the raw HTML (client-side rendering).** The homepage HTML a crawler first receives holds about 50 words and 21 links.
3. **Homepage has no H1 and a thin text body.** The homepage has no H1 and no H2, only two H3 headings in the footer.
4. **No canonical on the homepage or most pages.** The homepage, /feeds/, /search/ and /login/ have no canonical tag.
5. **No structured data anywhere.** No JSON-LD was found on the homepage.

### Top 5 quick wins
1. **No sitemap.xml and no robots.txt (both return 404).** Add app/robots.ts and app/sitemap.ts (Next.js) listing the home, about, contact, privacy and terms pages plus every show and episode page, with a Sitemap line in robots.txt.
2. **Homepage has no H1 and a thin text body.** Add a server-rendered H1 such as 'Binge Short Drama in Minutes' and section H2s (New This Week, genres), with a short intro paragraph.
3. **No canonical on the homepage or most pages.** Set absolute self-referencing canonicals through Next.js metadata (alternates.canonical with metadataBase https://fasttv.app).
4. **Weak titles, one shared description and no social tags.** Write unique title and description per page, add og:title, og:description, og:image and twitter:card via Next.js metadata.

### Key metrics

| Metric | Value |
|---|---|
| Sitemap URLs | 0 |
| Raw homepage words | 50 |
| Rendered homepage words | 650 |
| Rendered links | 420 |
| Requests | 63 |

## Technical SEO (40)

No sitemap or robots.txt, catalogue not crawlable.

| Finding | Severity | Fix |
|---|---|---|
| No sitemap.xml and no robots.txt (both return 404) (TECH-001) | Critical | Add app/robots.ts and app/sitemap.ts (Next.js) listing the home, about, contact, privacy and terms pages plus every show and episode page, with a Sitemap line in robots.txt. |
| Show catalogue is invisible in the raw HTML (client-side rendering) (TECH-002) | Critical | Create server-rendered, indexable pages per show (and per episode if public) such as /show/<slug>, link them from the homepage in plain anchor tags, and render title, synopsis and cast on the server. |
| Missing security headers (TECH-003) | Low | Add the headers in next.config.js or nginx and disable the powered-by header. |
| Viewport blocks pinch-zoom (TECH-004) | Low | Remove maximum-scale and user-scalable from the viewport tag. |

## Content Quality (35)

Almost no indexable text; shows are JavaScript-only.


## On-Page SEO (45)

No H1, no canonicals, no social tags.

| Finding | Severity | Fix |
|---|---|---|
| Homepage has no H1 and a thin text body (ONP-001) | High | Add a server-rendered H1 such as 'Binge Short Drama in Minutes' and section H2s (New This Week, genres), with a short intro paragraph. |
| No canonical on the homepage or most pages (ONP-002) | High | Set absolute self-referencing canonicals through Next.js metadata (alternates.canonical with metadataBase https://fasttv.app). |
| Weak titles, one shared description and no social tags (ONP-003) | Medium | Write unique title and description per page, add og:title, og:description, og:image and twitter:card via Next.js metadata. |

## Schema / Structured Data (10)

None present.

| Finding | Severity | Fix |
|---|---|---|
| No structured data anywhere (SCH-001) | High | Add Organization and WebSite with SearchAction on the homepage, and TVSeries, Episode or VideoObject on show pages. |

## Performance (CWV) (80)

Fast server; vitals not fully measured.

| Finding | Severity | Fix |
|---|---|---|
| Fast server and load in a lab sample; page weight is high (CWV-001) | Low | Lazy-load below-the-fold video posters, limit autoplaying previews and re-measure with PageSpeed Insights using an API key. |

## AI Search Readiness (40)

Crawlers allowed but little content.

| Finding | Severity | Fix |
|---|---|---|
| AI crawlers are allowed but have almost nothing to read (GEO-001) | Medium | Server-render show descriptions, add FAQ-style text on the homepage and optionally publish /llms.txt. |

## Images (85)

3 images in raw HTML, all with alt text.


## Limitations

- L
- C
- P
- ,
-  
- I
- N
- P
- ,
-  
- C
- L
- S
- ,
-  
- L
- i
- g
- h
- t
- h
- o
- u
- s
- e
- ,
-  
- s
- c
- r
- e
- e
- n
- s
- h
- o
- t
- s
- ,
-  
- S
- e
- a
- r
- c
- h
-  
- C
- o
- n
- s
- o
- l
- e
-  
- a
- n
- d
-  
- b
- a
- c
- k
- l
- i
- n
- k
-  
- d
- a
- t
- a
-  
- w
- e
- r
- e
-  
- n
- o
- t
-  
- c
- o
- l
- l
- e
- c
- t
- e
- d
-  
- (
- p
- e
- r
- f
- o
- r
- m
- a
- n
- c
- e
-  
- i
- s
-  
- f
- r
- o
- m
-  
- o
- n
- e
-  
- b
- r
- o
- w
- s
- e
- r
-  
- l
- o
- a
- d
- )
- .
-  
- S
- h
- o
- w
-  
- a
- n
- d
-  
- e
- p
- i
- s
- o
- d
- e
-  
- p
- a
- g
- e
- s
-  
- c
- o
- u
- l
- d
-  
- n
- o
- t
-  
- b
- e
-  
- t
- e
- s
- t
- e
- d
-  
- b
- e
- c
- a
- u
- s
- e
-  
- n
- o
-  
- p
- u
- b
- l
- i
- c
-  
- s
- h
- o
- w
-  
- U
- R
- L
- s
-  
- w
- e
- r
- e
-  
- f
- o
- u
- n
- d
- ;
-  
- i
- f
-  
- t
- h
- e
- y
-  
- e
- x
- i
- s
- t
-  
- b
- e
- h
- i
- n
- d
-  
- t
- h
- e
-  
- a
- p
- p
- ,
-  
- i
- n
- d
- e
- x
- a
- b
- i
- l
- i
- t
- y
-  
- t
- h
- e
- r
- e
-  
- i
- s
-  
- u
- n
- k
- n
- o
- w
- n
- .
-  
- S
- c
- o
- r
- e
- s
-  
- a
- r
- e
-  
- j
- u
- d
- g
- e
- m
- e
- n
- t
- -
- b
- a
- s
- e
- d
-  
- e
- s
- t
- i
- m
- a
- t
- e
- s
- .

Evidence, code and checks for every finding: `SEO-Report.pdf`. Fix prompts: `FIX-PROMPTS.md`.
