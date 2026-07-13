# SIKA Web + Project Cyborg — Reference Summary
*Last updated: 2026-07-13*

Local-first, $0/month dual engine on the Mac Mini (Ebs-Mac-mini.local / ananseclaw).
Two connected platforms: SIKA earns attention, Cyborg finds what to sell.

---

## SIKA Web ("Seeker") — the free traffic engine
**What it is:** A public website that gets found by Google AND AI assistants
(ChatGPT, Gemini, Perplexity), pulling in free buyer traffic.

**What it does:**
- Writes a new page every 6 hours (throttled from 3h so a new domain doesn't look like spam).
- Every page is built for AI citation: clean summary box + JSON-LD structured data,
  written as a buyer question (e.g. "Best Mobile Money Platforms in Africa").
- Targets underserved topics (Africa finance, commerce) with low competition.
- Auto-publishes to GitHub Pages. No hosting cost.

**Running cron jobs (this chat = origin):**
- `sika-web-build-loop` (e10ff5c5d85e) — every 6h (content)
- `sika-winning-product` (c812d23b08e1) — Mon 11am (Cyborg product pick → SIKA page)
- `ai-visibility-weekly` (15c06d266fc3) — daily 7pm (is SIKA being cited?)
- `ai-news-daily-3pm` (08efba859739) — 3pm AI news
- `china-ai-watch` (570225be79c4) — 8pm
- `local-monetization-watch` (2d713cb2cbef) — 9pm

**Monetization:** OFF on purpose. ADSENSE_ON / AFFILIATE_ON / NEWSLETTER_ON = False.
See MONETIZATION_GATE.md — enable only after 30-60 day domain age + consistent ✅ citations.

---

## Project Cyborg — product finder + store operator
**What it is:** The dropship brain. Finds winning products and is built to run a store
SAFELY — no AI can ever spend money or publish without your OK.

**Proven working:**
- Research + scoring (free sources: DuckDuckGo lite + Wikipedia; Reddit/Google Trends
  are blocked on this Mac and self-heal).
- Local AI picks ONE specific product (banned-category list + 3-attempt re-score loop
  rejects vague categories — fixed Trap B).
- Dry run confirmed: scores a product, logs PENDING→RUNNING→COMPLETE in SQLite audit
  trail, compiles valid OraclePayload — ZERO live Shopify/Telegram calls.

**Built but waiting:**
- Store layer (Architect → Shopify DRAFT) — code complete, needs Shopify store URL + token.
- Telegram approval handshake — PARKED (user decision 2026-07-13).
- Runs isolated in its own `.venv` (no system Python conflicts).
- Original .env has PLACEHOLDER Shopify + Telegram tokens (never configured, not stale).

**Key files:**
- /Users/ananseclaw/Documents/Claude/Projects/PROJECT CYBORG/oracle/scorer.py (real scorer)
- /Users/ananseclaw/Documents/Claude/Projects/PROJECT CYBORG/core/{db,config,llm,models,telegram}.py
- /Users/ananseclaw/Documents/Claude/Projects/PROJECT CYBORG/dryrun_oracle.py (test harness)

---

## How they connect (the bridge)
Cyborg's product finder feeds SIKA: every Monday it picks a winning product →
`winning_product.py` writes a SIKA page about it → free traffic flows to your future store.
New product pages auto-link back into older SIKA pages (internal linking bridge, Phase 2c),
spreading indexing authority across the domain.

Script: /Users/ananseclaw/.hermes/site-builder/winning_product.py
 (reuses Cyborg's research+scoring logic; renders via build.py's own pipeline)

---

## Bottom line
Local-first, $0/month dual engine: SIKA earns attention, Cyborg finds what to sell.
Safe-shaped: slow cadence, specific content, money locked, human approval required.
Only thing left to "go live" on the store side = Shopify credentials (not rushed;
domain needs 30-60 day aging window first).

## Open items
- [ ] Path A finish: wire Shopify store URL + token → Architect → DRAFT → (manual approve) → publish
- [ ] Telegram approval for Cyborg: PARKED
- [ ] Monetization flip: gated on 30-60 day age + consistent citations
