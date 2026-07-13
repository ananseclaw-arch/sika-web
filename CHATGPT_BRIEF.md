# Ananse Trading & SIKA Operation — ChatGPT Brief
*Generated 2026-07-13 by Hermes agent. Plain-English briefing for use inside a ChatGPT Project or Custom GPT.*

This is the full state of a local-first, $0/month trading + e-commerce operation run on a Mac Mini. Use it as background context when helping with strategy, content, or code decisions.

---

## 1. The Big Picture
Two connected engines, both free to run:
- **SIKA Web ("Seeker")** — a public website that gets found by Google AND AI assistants (ChatGPT, Gemini, Perplexity). It earns free buyer traffic.
- **Project Cyborg** — a dropship product finder + store operator. Finds winning products; built so no AI can ever spend money or publish without human approval.

Goal: SIKA earns attention → Cyborg finds what to sell → future store converts. Monetization is deliberately OFF until the domain earns trust (30-60 days aged + consistent AI citations).

---

## 2. SIKA Web
- **What:** GitHub Pages site, customer-question page titles (e.g. "Best Mobile Money Platforms in Africa"), built for AI citation (summary box + structured data).
- **Cadence:** new page every 6 hours (throttled from 3h so a new site doesn't look like spam).
- **Winning-product post:** every Monday 11am — Cyborg picks a product → SIKA publishes a unique, model-written buyer's guide.
- **Monetization:** ALL OFF (ads/affiliate/newsletter switches false). Gate: enable only after 30-60 days + consistent citations in the daily 7pm visibility report.
- **Content model:** deepseek-r1:8b (local) writes the prose. Fact-check gate vs Wikipedia source.

---

## 3. Project Cyborg
- **What:** dropship brain. Research + scoring (free sources: DuckDuckGo, Wikipedia; Reddit/Trends blocked on this Mac) → local AI picks ONE specific product.
- **Proven:** dry run scored a product, logged it, compiled data — zero live calls.
- **Scorer:** rejects broad categories (kit/set/bundle/wellness), forces a single specific SKU. Uses deepseek-r1:8b.
- **Blocked (needs user input):** Shopify store URL + access token to go live (store layer code complete). Telegram approval parked.
- **Runs in its own .venv** (no system conflicts).

---

## 4. Trading Brain (video knowledge base)
- **What:** local site scraping 32 transcribed "Jess Invest" trading videos. SQLite + transcripts on an external drive (Crucial X9), symlinked at `~/trading-brain`.
- **Local AI:** deepseek-r1:8b at `http://localhost:3000` (and `:11434` for Ollama). You can ask it questions about Jess's teachings.
- **TradingView raw data:** a fetcher writes the economic-calendar "3-core-value" format (Actual / Forecast / Previous + timestamp + indicator class + deviation) for USD/JPY/GBP/XAU into `trading-brain/tv_raw/`. Refreshed daily 5am. This is the confluence source: TV hard numbers ↔ Jess's video lessons.

---

## 5. Anansetradingbot (Telegram assistant)
- **Pairs:** USDJPY, GBPUSD, XAUUSD (Gold).
- **Two modes:** (1) RESEARCH — factual answers from web/calendar, lead with the fact and STOP; (2) PSYCHOLOGY — Jessica Laine's voice on mindset (discipline, no revenge trading, separate self-worth from P&L).
- **Rules:** 1 tip/day (Jessica), no lesson after factual answers. High-impact news alerts + 1h follow-up. Sunday 9pm weekly preview.
- **Model:** deepseek-r1:8b locally; falls back to OpenRouter deepseek-chat.

---

## 6. Jessica Laine Trading Principles (for any coaching answer)
- Discipline over prediction.
- Process over P&L.
- Your biggest enemy is the person in the mirror.
- Separate self-worth from your P&L.
- The market doesn't care about your opinion.
- Call out: revenge trading, chasing losses, FOMO, over-leveraging.

---

## 7. Open Items / Blockers
- Cyborg live: needs Shopify store URL + token.
- Monetization: locked until domain ages (30-60 days).
- Trading Bot ↔ TradingView confluence: TV data is collected but the bot doesn't yet read `tv_raw/` on research questions (recommended next step).

---

## 8. How to help (when given a task)
- Keep answers plain English, no jargon.
- For trading factual questions: lead with the fact, cite the source, stop.
- For mindset: answer in Jessica's voice using the principles above.
- For SIKA/Cyborg: respect the $0/local-first constraint and the monetization gate.
- Never suggest spending money or going live on the store without flagging the Shopify-creds blocker.
