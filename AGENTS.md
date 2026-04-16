# SEO Agent Configuration

## Skill Definition

skill:
  name: seo
  description: >
    LLM-first SEO analysis for websites, blog posts, and GitHub repositories.
    Provides audits, technical checks, content quality, schema validation,
    Core Web Vitals, GEO/AEO optimization, and link analysis.
  skillDir: ./Agentic-SEO-Skill
  triggerKeywords:
    - seo audit
    - seo analysis
    - seo check
    - technical seo
    - core web vitals
    - e-e-a-t
    - schema markup
    - sitemap
    - hreflang
    - geo optimization
    - aeo
    - link profile
    - programmatic seo
    - github seo
    - agentic engine optimization
    - llms.txt
    - token count
    - ai traffic

## Sub-Skills (16)

| Sub-Skill | File | Purpose |
|----------|------|---------|
| seo-audit | resources/skills/seo-audit.md | Full website audit |
| seo-article | resources/skills/seo-article.md | Article optimization |
| seo-page | resources/skills/seo-page.md | Single-page deep analysis |
| seo-technical | resources/skills/seo-technical.md | Technical SEO |
| seo-content | resources/skills/seo-content.md | Content quality & E-E-A-T |
| seo-schema | resources/skills/seo-schema.md | Schema.org validation |
| seo-sitemap | resources/skills/seo-sitemap.md | Sitemap analysis |
| seo-images | resources/skills/seo-images.md | Image optimization |
| seo-geo | resources/skills/seo-geo.md | AI search optimization |
| seo-aeo | resources/skills/seo-aeo.md | Answer engine optimization |
| seo-links | resources/skills/seo-links.md | Link profile analysis |
| seo-programmatic | resources/skills/seo-programmatic.md | Programmatic SEO safeguards |
| seo-competitors | resources/skills/seo-competitor-pages.md | Comparison pages |
| seo-hreflang | resources/skills/seo-hreflang.md | International SEO |
| seo-plan | resources/skills/seo-plan.md | Strategic planning |
| seo-github | resources/skills/seo-github.md | GitHub repository SEO |

## AEO Sub-Skills (5)

| Sub-Skill | File | Purpose |
|----------|------|---------|
| aeo-audit | AEO-Skills/skills/aeo-audit.md | Full AEO audit for websites |
| llms-txt-checker | AEO-Skills/skills/llms-txt-checker.md | Validate llms.txt files |
| token-counter | AEO-Skills/skills/token-counter.md | Count tokens in documentation |
| ai-traffic-detector | AEO-Skills/skills/ai-traffic-detector.md | Detect AI agent traffic |
| aeo-benchmark | AEO-Skills/skills/aeo-benchmark.md | Benchmark AEO performance |

## Specialist Agents (10)

| Agent | File | Focus |
|-------------|------|-------|
| seo-technical | resources/agents/seo-technical.md | Crawlability, indexability, security |
| seo-content | resources/agents/seo-content.md | E-E-A-T assessment |
| seo-performance | resources/agents/seo-performance.md | Core Web Vitals |
| seo-schema | resources/agents/seo-schema.md | JSON-LD validation |
| seo-sitemap | resources/agents/seo-sitemap.md | XML sitemap quality |
| seo-visual | resources/agents/seo-visual.md | Visual analysis |
| seo-github-analyst | resources/agents/seo-github-analyst.md | Repository metadata |
| seo-github-benchmark | resources/agents/seo-github-benchmark.md | Query ranking |
| seo-github-data | resources/agents/seo-github-data.md | API and archival |
| seo-verifier | resources/agents/seo-verifier.md | Deduplication |

## Script Commands

Primary evidence collection:

```
# Fetch & parse
python3 scripts/fetch_page.py <url> --output /tmp/page.html
python3 scripts/parse_html.py /tmp/page.html --url <url> --json

# Technical checks
python3 scripts/robots_checker.py <url>
python3 scripts/llms_txt_checker.py <url>
python3 scripts/security_headers.py <url>
python3 scripts/redirect_checker.py <url>

# Performance
python3 scripts/pagespeed.py <url> --strategy mobile

# Content
python3 scripts/readability.py /tmp/page.html
python3 scripts/article_seo.py <url>
python3 scripts/entity_checker.py <url>

# Links
python3 scripts/broken_links.py <url>
python3 scripts/internal_links.py <url>
python3 scripts/link_profile.py <url>

# Sitemap & schema
python3 scripts/validate_schema.py <file>
python3 scripts/broken_links.py <url>

# GitHub
python3 scripts/github_repo_audit.py --repo <owner/repo> --provider auto
python3 scripts/github_seo_report.py --repo <owner/repo> --markdown GITHUB-SEO-REPORT.md

# AEO (Agentic Engine Optimization)
python3 AEO-Skills/scripts/llms_txt_checker.py <url>
python3 AEO-Skills/scripts/robots_checker.py <url>
python3 AEO-Skills/scripts/token_counter.py <url>
python3 AEO-Skills/scripts/ai_traffic_detector.py --log-file <logfile>
python3 AEO-Skills/scripts/aeo_benchmark.py --url <domain>
```

## Output Artifacts

- `FULL-AUDIT-REPORT.md` — Detailed findings
- `ACTION-PLAN.md` — Prioritized fixes
- `SEO-REPORT.html` — Interactive dashboard (optional)
- `GITHUB-SEO-REPORT.md` — GitHub-specific report
- `GITHUB-ACTION-PLAN.md` — GitHub action plan

## Critical Rules

1. INP (not FID) — sole interactivity metric since Sept 2024
2. FAQPage schema — restricted to government/healthcare only
3. HowTo schema — deprecated (Sept 2023), never recommend
4. JSON-LD only — no Microdata or RDFa
5. E-E-A-T applies to all competitive queries (Dec 2025)
6. Mobile-first indexing complete (July 2024)
7. Location pages — warning at 30+, hard stop at 50+
8. AI crawlers — check for GPTBot, ClaudeBot, PerplexityBot in robots.txt