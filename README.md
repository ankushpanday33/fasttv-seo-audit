# FastTV SEO Audit

SEO audit of https://fasttv.app, run on 18/11/2026.

**Overall SEO health score: 43/100** (10 findings)

## Summary

FastTV loads quickly and allows every crawler, but gives search engines almost nothing to index: no sitemap, no robots.txt, no structured data, and a show catalogue that only appears after JavaScript runs.

## Top issues

- **Critical:** No sitemap.xml and no robots.txt (both return 404).
- **Critical:** Show catalogue is invisible in the raw HTML. About 50 words in the raw page versus about 650 after rendering.
- **High:** Homepage has no H1 and no canonical.
- **High:** No structured data (JSON-LD) anywhere.
- **Medium:** No Open Graph or Twitter tags, so shared links show no preview.

## Files

| File | What it is |
|---|---|
| [FULL-AUDIT-REPORT.md](FULL-AUDIT-REPORT.md) | Complete findings with evidence |
| [ACTION-PLAN.md](ACTION-PLAN.md) | Prioritised fixes and 30-day plan |
| [FIX-PROMPTS.md](FIX-PROMPTS.md) | Copy-paste prompts for all tools |
| [fix-prompts/claude-code.md](fix-prompts/claude-code.md) | Prompt for Claude Code |
| [fix-prompts/cursor.md](fix-prompts/cursor.md) | Prompt for Cursor |
| [fix-prompts/antigravity.md](fix-prompts/antigravity.md) | Prompt for Antigravity |
| [fix-prompts/lovable.md](fix-prompts/lovable.md) | Prompt for Lovable |

## Limits of this audit

LCP, INP and CLS were not measured, and Search Console and backlink data were not collected. No public show pages were found, so show-level indexability is untested. Scores are judgement-based estimates.

Confidential | Hungama Digital Media Entertainment Pvt. Ltd.
