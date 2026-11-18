# Action Plan: fasttv.app

SEO Health Score: 43/100 (18/11/2026).

Each action lists what it unblocks or depends on, how you would know it failed, and a leading indicator to watch.

## Phase 1: Remove risk (week 1)

| # | Action | Unblocks / depends on | Failure check | Leading indicator |
|---|---|---|---|---|
| 1 | **No sitemap.xml and no robots.txt (both return 404)** (TECH-001). Add app/robots.ts and app/sitemap.ts (Next.js) listing the home, about, contact, privacy and terms pages plus every show and episode page, with a Sitemap line in robots.txt. | Gives Google and AI crawlers a complete map of the catalogue. | Both URLs return 200 and the sitemap validates in Search Console. | - |
| 2 | **Show catalogue is invisible in the raw HTML (client-side rendering)** (TECH-002). Create server-rendered, indexable pages per show (and per episode if public) such as /show/<slug>, link them from the homepage in plain anchor tags, and render title, synopsis and cast on the server. | Turns the catalogue into searchable pages, the main source of organic traffic for a video app. | curl the homepage and a show URL and confirm titles and links are in the HTML. | - |
| 3 | **Homepage has no H1 and a thin text body** (ONP-001). Add a server-rendered H1 such as 'Binge Short Drama in Minutes' and section H2s (New This Week, genres), with a short intro paragraph. | Clear topic signal for search and AI summaries. | One H1 present in the raw HTML. | - |
| 4 | **No canonical on the homepage or most pages** (ONP-002). Set absolute self-referencing canonicals through Next.js metadata (alternates.canonical with metadataBase https://fasttv.app). | Avoids duplicate trailing-slash and parameter variants. |  | - |

## Phase 2: Earn rankings (weeks 2 to 3)

| # | Action | Unblocks / depends on | Failure check | Leading indicator |
|---|---|---|---|---|
| 5 | **No structured data anywhere** (SCH-001). Add Organization and WebSite with SearchAction on the homepage, and TVSeries, Episode or VideoObject on show pages. | Eligibility for video and series rich results. |  | - |
| 6 | **Weak titles, one shared description and no social tags** (ONP-003). Write unique title and description per page, add og:title, og:description, og:image and twitter:card via Next.js metadata. | Better snippets and link previews on WhatsApp, X and Facebook. |  | - |

## Phase 3: Authority and coverage (month 2)

| # | Action | Unblocks / depends on | Failure check | Leading indicator |
|---|---|---|---|---|
| 7 | **AI crawlers are allowed but have almost nothing to read** (GEO-001). Server-render show descriptions, add FAQ-style text on the homepage and optionally publish /llms.txt. | More chances to appear in AI answers about short dramas. |  | - |

## Phase 4: Hygiene and monitoring (ongoing)

| # | Action | Unblocks / depends on | Failure check | Leading indicator |
|---|---|---|---|---|
| 8 | **Fast server and load in a lab sample; page weight is high** (CWV-001). Lazy-load below-the-fold video posters, limit autoplaying previews and re-measure with PageSpeed Insights using an API key. | Keeps LCP low on mobile data. |  | - |
| 9 | **Missing security headers** (TECH-003). Add the headers in next.config.js or nginx and disable the powered-by header. | Hardening and trust signals. |  | - |
| 10 | **Viewport blocks pinch-zoom** (TECH-004). Remove maximum-scale and user-scalable from the viewport tag. | Accessibility and Lighthouse score. |  | - |

