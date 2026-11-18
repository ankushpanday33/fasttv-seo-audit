# Claude Code: SEO fix prompts
Site: https://fasttv.app  |  Open a terminal in your project folder, run `claude`, and paste each prompt.

## Prompt 1 of 3

````text
You are fixing SEO issues found by an audit of https://fasttv.app (part 1 of 3, critical and high priority).
Tech stack: Framework: Next.js (App Router); Hosting: nginx on Ubuntu; CMS: Custom
Work in this repository. Read the relevant files before editing.

Rules:
- Fix only the items below. Do not refactor unrelated code or change visible design.
- Server-render every SEO tag (title, meta, canonical, JSON-LD) so it is in the HTML without JavaScript.
- Keep structured data truthful: JSON-LD must match what is visible on the page.
- If an item does not apply to this codebase, say so instead of guessing.
- Using Claude Code: when done, list every file changed and how you verified each item.

### 1. [Critical] No sitemap.xml and no robots.txt (both return 404) (TECH-001)
Problem: Neither /robots.txt nor /sitemap.xml exists. Crawlers have no list of pages and no Sitemap hint, so discovery depends on following links that only appear after JavaScript runs.
Evidence from the live site: robots.txt returned 404 text/html; sitemap.xml and sitemap_index.xml returned 404.
Affected URLs: https://fasttv.app/robots.txt, https://fasttv.app/sitemap.xml
Required change: Add app/robots.ts and app/sitemap.ts (Next.js) listing the home, about, contact, privacy and terms pages plus every show and episode page, with a Sitemap line in robots.txt.
Done when: Both URLs return 200 and the sitemap validates in Search Console.

### 2. [Critical] Show catalogue is invisible in the raw HTML (client-side rendering) (TECH-002)
Problem: The homepage HTML a crawler first receives holds about 50 words and 21 links. After JavaScript runs the page shows about 650 words and 420 links with show titles such as 'Billionaire World', 'CEO Diaries' and 'Pati Patni Aur Padosan'. No show or episode URLs were found in the HTML, so individual dramas have no crawlable pages to rank.
Evidence from the live site: Raw HTML: 50 words, 21 links, 0 h1, 0 JSON-LD. Rendered DOM in a browser: about 650 words and 420 links.
Affected URLs: https://fasttv.app/
Required change: Create server-rendered, indexable pages per show (and per episode if public) such as /show/<slug>, link them from the homepage in plain anchor tags, and render title, synopsis and cast on the server.
Done when: curl the homepage and a show URL and confirm titles and links are in the HTML.

### 3. [High] Homepage has no H1 and a thin text body (ONP-001)
Problem: The homepage has no H1 and no H2, only two H3 headings in the footer. Raw text is about 50 words.
Evidence from the live site: Homepage HTML: 0 h1, 0 h2, 2 h3.
Affected URLs: https://fasttv.app/
Required change: Add a server-rendered H1 such as 'Binge Short Drama in Minutes' and section H2s (New This Week, genres), with a short intro paragraph.
Done when: One H1 present in the raw HTML.

### 4. [High] No canonical on the homepage or most pages (ONP-002)
Problem: The homepage, /feeds/, /search/ and /login/ have no canonical tag. /about/ and /privacy/ use a relative canonical ('/about/'), which should be an absolute URL.
Evidence from the live site: Homepage and /feeds/ have no rel=canonical; /about/ canonical is '/about/'.
Required change: Set absolute self-referencing canonicals through Next.js metadata (alternates.canonical with metadataBase https://fasttv.app).

### 5. [High] No structured data anywhere (SCH-001)
Problem: No JSON-LD was found on the homepage. A video app can earn rich results with Organization, WebSite, TVSeries or VideoObject markup.
Evidence from the live site: Homepage HTML: 0 ld+json scripts.
Required change: Add Organization and WebSite with SearchAction on the homepage, and TVSeries, Episode or VideoObject on show pages.

Verification after all items:
1. Build the project and fix any build or type errors.
2. Fetch the built pages without JavaScript (for example `curl -sL https://fasttv.app`) and confirm each new tag is in the raw HTML.
3. Validate any JSON-LD at https://validator.schema.org and https://search.google.com/test/rich-results.
4. Re-run `/seo audit` (Claude SEO Master Skills) and confirm these finding IDs no longer appear.
````

## Prompt 2 of 3

````text
You are fixing SEO issues found by an audit of https://fasttv.app (part 2 of 3, medium priority).
Tech stack: Framework: Next.js (App Router); Hosting: nginx on Ubuntu; CMS: Custom
Work in this repository. Read the relevant files before editing.

Rules:
- Fix only the items below. Do not refactor unrelated code or change visible design.
- Server-render every SEO tag (title, meta, canonical, JSON-LD) so it is in the HTML without JavaScript.
- Keep structured data truthful: JSON-LD must match what is visible on the page.
- If an item does not apply to this codebase, say so instead of guessing.
- Using Claude Code: when done, list every file changed and how you verified each item.

### 1. [Medium] AI crawlers are allowed but have almost nothing to read (GEO-001)
Problem: GPTBot, ClaudeBot, PerplexityBot, Google-Extended and Googlebot all get 200, which is good. But the raw page has about 50 words, no llms.txt (404) and no structured data, so there is little for an AI engine to cite.
Evidence from the live site: Bot user agents returned 200; /llms.txt returned 404.
Required change: Server-render show descriptions, add FAQ-style text on the homepage and optionally publish /llms.txt.

### 2. [Medium] Weak titles, one shared description and no social tags (ONP-003)
Problem: The homepage description is 'FastTV - micro-dramas, trailers, and live reels.' while the title says 'Binge Short Drama in Minutes', and the manifest says something else. There are no Open Graph or Twitter tags on any page tested, so shared links show no preview image.
Evidence from the live site: 0 og: or twitter: tags on the homepage, /about/, /feeds/, /search/, /privacy/, /login/.
Required change: Write unique title and description per page, add og:title, og:description, og:image and twitter:card via Next.js metadata.

Verification after all items:
1. Build the project and fix any build or type errors.
2. Fetch the built pages without JavaScript (for example `curl -sL https://fasttv.app`) and confirm each new tag is in the raw HTML.
3. Validate any JSON-LD at https://validator.schema.org and https://search.google.com/test/rich-results.
4. Re-run `/seo audit` (Claude SEO Master Skills) and confirm these finding IDs no longer appear.
````

## Prompt 3 of 3

````text
You are fixing SEO issues found by an audit of https://fasttv.app (part 3 of 3, low priority).
Tech stack: Framework: Next.js (App Router); Hosting: nginx on Ubuntu; CMS: Custom
Work in this repository. Read the relevant files before editing.

Rules:
- Fix only the items below. Do not refactor unrelated code or change visible design.
- Server-render every SEO tag (title, meta, canonical, JSON-LD) so it is in the HTML without JavaScript.
- Keep structured data truthful: JSON-LD must match what is visible on the page.
- If an item does not apply to this codebase, say so instead of guessing.
- Using Claude Code: when done, list every file changed and how you verified each item.

### 1. [Low] Fast server and load in a lab sample; page weight is high (CWV-001)
Problem: In one browser load, time to first byte was about 162 ms, DOM ready about 349 ms and full load about 948 ms. HTML is cached by Next.js (x-nextjs-cache HIT). The page made 63 requests and transferred about 1.9 MB, of which about 395 KB was JavaScript and 14 were video or media files. LCP, INP and CLS were not captured.
Evidence from the live site: Navigation and Resource Timing in a browser on 18/11/2026; no field data.
Affected URLs: https://fasttv.app/
Required change: Lazy-load below-the-fold video posters, limit autoplaying previews and re-measure with PageSpeed Insights using an API key.

### 2. [Low] Missing security headers (TECH-003)
Problem: The response carries no Strict-Transport-Security, Content-Security-Policy, X-Frame-Options, Referrer-Policy or X-Content-Type-Options header. The 'X-Powered-By: Next.js' header is exposed.
Evidence from the live site: Response headers on https://fasttv.app.
Required change: Add the headers in next.config.js or nginx and disable the powered-by header.

### 3. [Low] Viewport blocks pinch-zoom (TECH-004)
Problem: The viewport sets maximum-scale=1 and user-scalable=no, which stops users from zooming and fails accessibility guidance.
Evidence from the live site: Viewport meta: maximum-scale=1, user-scalable=no.
Required change: Remove maximum-scale and user-scalable from the viewport tag.

Verification after all items:
1. Build the project and fix any build or type errors.
2. Fetch the built pages without JavaScript (for example `curl -sL https://fasttv.app`) and confirm each new tag is in the raw HTML.
3. Validate any JSON-LD at https://validator.schema.org and https://search.google.com/test/rich-results.
4. Re-run `/seo audit` (Claude SEO Master Skills) and confirm these finding IDs no longer appear.
````
