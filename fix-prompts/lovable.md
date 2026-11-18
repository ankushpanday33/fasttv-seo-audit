# Lovable: SEO fix prompts
Site: https://fasttv.app  |  Open your project in Lovable and paste each prompt into the chat, one at a time.

## Prompt 1 of 4

````text
I ran an SEO audit on my site https://fasttv.app. Please make these critical and high priority SEO fixes (part 1 of 4). Do not change the design, layout or copy beyond what each item asks. After the changes, tell me which pages you edited.

1. No sitemap.xml and no robots.txt (both return 404)
   Where: https://fasttv.app/robots.txt, https://fasttv.app/sitemap.xml
   Change: Add app/robots.ts and app/sitemap.ts (Next.js) listing the home, about, contact, privacy and terms pages plus every show and episode page, with a Sitemap line in robots.txt.
   Check: Both URLs return 200 and the sitemap validates in Search Console.

2. Show catalogue is invisible in the raw HTML (client-side rendering)
   Where: https://fasttv.app/
   Change: Create server-rendered, indexable pages per show (and per episode if public) such as /show/<slug>, link them from the homepage in plain anchor tags, and render title, synopsis and cast on the server.
   Check: curl the homepage and a show URL and confirm titles and links are in the HTML.

3. Homepage has no H1 and a thin text body
   Where: https://fasttv.app/
   Change: Add a server-rendered H1 such as 'Binge Short Drama in Minutes' and section H2s (New This Week, genres), with a short intro paragraph.
   Check: One H1 present in the raw HTML.

4. No canonical on the homepage or most pages
   Where: the whole site
   Change: Set absolute self-referencing canonicals through Next.js metadata (alternates.canonical with metadataBase https://fasttv.app).

When you are done, publish a preview and list the pages you changed.
````

## Prompt 2 of 4

````text
I ran an SEO audit on my site https://fasttv.app. Please make these critical and high priority SEO fixes (part 2 of 4). Do not change the design, layout or copy beyond what each item asks. After the changes, tell me which pages you edited.

1. No structured data anywhere
   Where: the whole site
   Change: Add Organization and WebSite with SearchAction on the homepage, and TVSeries, Episode or VideoObject on show pages.

When you are done, publish a preview and list the pages you changed.
````

## Prompt 3 of 4

````text
I ran an SEO audit on my site https://fasttv.app. Please make these medium priority SEO fixes (part 3 of 4). Do not change the design, layout or copy beyond what each item asks. After the changes, tell me which pages you edited.

1. AI crawlers are allowed but have almost nothing to read
   Where: the whole site
   Change: Server-render show descriptions, add FAQ-style text on the homepage and optionally publish /llms.txt.

2. Weak titles, one shared description and no social tags
   Where: the whole site
   Change: Write unique title and description per page, add og:title, og:description, og:image and twitter:card via Next.js metadata.

When you are done, publish a preview and list the pages you changed.
````

## Prompt 4 of 4

````text
I ran an SEO audit on my site https://fasttv.app. Please make these low priority SEO fixes (part 4 of 4). Do not change the design, layout or copy beyond what each item asks. After the changes, tell me which pages you edited.

1. Fast server and load in a lab sample; page weight is high
   Where: https://fasttv.app/
   Change: Lazy-load below-the-fold video posters, limit autoplaying previews and re-measure with PageSpeed Insights using an API key.

2. Missing security headers
   Where: the whole site
   Change: Add the headers in next.config.js or nginx and disable the powered-by header.

3. Viewport blocks pinch-zoom
   Where: the whole site
   Change: Remove maximum-scale and user-scalable from the viewport tag.

When you are done, publish a preview and list the pages you changed.
````
