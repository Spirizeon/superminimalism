# berzi.one

minimal, edge-delivered, AI optimised **hand-written HTML** portfolio. No framework, no build step, no dependencies. One small module script from [ascii.rest](https://ascii.rest) draws the animated art.

Measured, not claimed. Run `lighthouse https://berzi.one --view` yourself; the tables below record the state of the repo as of 2026‑10‑09.

## Measured transfer sizes

gzip ‑9, served from Cloudflare (brotli is ~15–20% smaller). `ascii.js` + `library.js` + `mount.js` are the shared 7.3 KB gzip core, cached across every page.

| page | HTML (gzip) | pieces (gzip) | total JS | requests to ascii.rest |
| --- | --- | --- | --- | --- |
| `index` | 6.4 KB | night‑coast, typewriter, boot‑log, terminal, nixos, rust, go | 24.3 KB | 10 |
| `hermetic` | 6.1 KB | candle | 11.9 KB | 4 |
| `coffee` | 5.1 KB | coffee, candle | 15.9 KB | 5 |
| `atlan` | 5.0 KB | big‑text | 9.2 KB | 4 |
| `404` | 1.8 KB | not‑found | 9.2 KB | 4 |

| piece | bytes (gzip) |
| --- | --- |
| ascii.js | 2.2 KB |
| library.js | 2.5 KB |
| mount.js | 2.6 KB |
| ascii-rest-mono.woff2 | 3.0 KB — injected by the library itself, and fetched **only** where the system monospace face has no box-drawing or block glyphs, e.g. Android. Not declared by this repo. |
| og-image.png | 15.9 KB — fetched by social crawlers, never by a visitor |

## What changed, and what it cost

This site used to ship **0 KB of JavaScript**. It now ships a module script, because animation needs one. The claim that replaced it.

| | before | now |
| --- | --- | --- |
| JavaScript | 0 KB | 9–24 KB gzip, one module chain |
| Requests | 1 | 1 HTML + 1 module + 1 per piece |
| FCP / LCP | ~0.15 s | ~0.15 s HTML, **then** the module chain and first frame |
| TBT | 0 ms | non‑zero: pieces animate |
| Lighthouse Performance | 100/100 | **must be re‑measured, not claimed** |
| Third‑party origin | none | ascii.rest (script, font, piece modules) |

## What is still true

- Hand‑written HTML and inline CSS. No framework, no bundler, no `node_modules`, no hydrate.
- Zero render‑blocking stylesheets, zero images on the critical path. `og-image.png` is crawler‑only.
- Edge‑delivered from Cloudflare, TTFB ~10–30 ms, unlimited bandwidth, no cold starts.
- `prefers-reduced-motion` holds every piece on its first frame. IntersectionObserver pauses pieces that scroll off screen.
- Every piece carries a `label`, which the component sets as the canvas/`pre`'s `aria-label`.
- `_headers` sets CSP, HSTS, `X-Content-Type-Options`, `Referrer-Policy`, `Permissions-Policy` and COOP. `'unsafe-inline'` stays in `script-src` because of the inline JSON‑LD, and in `style-src` because the CSS is inlined on purpose.

## Perf controls baked into the markup

- `fps` is lowered on every piece: night-coast 12, candle 12, boot-log 10, terminal 12, typewriter 12, logos 10.
- Only three logos are mounted (nixos, rust, go) — each is a 30 fps canvas at stock speed.
- No glyph webfont is declared here; the library injects its own 3 KB cut and only browsers lacking the glyphs fetch it.
- Prose and links are ordinary HTML, so the page is readable, selectable and indexable with the script still in flight.

## AEO / AI discoverability

The site treats LLM crawlers as a first‑class audience: `llms.txt`, `llms-full.txt` and `skill.md` describe the person, the projects and the stack in plain text, `robots.txt` allowlists the AI agents explicitly, and the prose is written so an LLM can quote it without guessing.

## Development

```sh
npx wrangler pages dev .     # or: wrangler dev
```

There is nothing to build. Edit HTML, commit, deploy.
