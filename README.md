# WrenchWise 🔧

**Is your mechanic ripping you off?** Paste any car repair estimate — WrenchWise checks every line against fair-price data, flags the inflated ones, and explains it all in plain English.

*This is a submission for the Hacktoberfest 2026 Open-Source AI Challenge — Week 2: Side Hustle.*

## Live demo

Open `index.html` in Chrome or Edge (WebGPU required for the AI explainer). No build step, no server, no API keys.

## How it works

**Two layers, each doing what it's actually good at:**

1. **Deterministic engine (plain JS)** — parses the pasted estimate, matches each line against a curated fair-price pack (India + US), and flags anything out of range. Every number on screen is computed by code. The AI never does math.
2. **Open-weight explainer (Gemma 2B, in-browser)** — Google's open-weight `gemma-2-2b-it` runs 100% on-device via [WebLLM](https://github.com/mlc-ai/web-llm). It turns the flagged lines into plain-English explanations, a verdict, and sharp questions to ask your mechanic. One-time ~1.5 GB download, cached in the browser after.

Nothing you paste ever leaves your device. There is no backend to leak your number plate, VIN, or service history.

## Why open weights make this business work

- **$0 marginal cost** — charging $2 a quote only works when each quote costs you nothing. No per-token API bill, no servers.
- **Privacy is the product** — an estimate carries your plate, VIN, and phone number. Local inference means that data never crosses a trust boundary.
- **Niche beats generic** — a general chatbot guesses at part prices. A curated price database + a small open model as explainer is more accurate where it counts.
- **No lock-in** — no provider can raise prices, throttle you, or deprecate the model under your business.

## Run it

```bash
# any static server works, e.g.
npx serve .
# then open http://localhost:3000 in Chrome/Edge
```

Or deploy the folder as a static site (Render config included via `render.yaml`).

## Price packs

`PRICE_PACKS` in `index.html` holds the fair-price data — `IN` (₹, 22 common jobs) and `US` ($, 14 common jobs, beta). Ranges are market estimates, not quotes. Adding a region is one object.

## Disclaimer

Fair ranges are estimates compiled from market data. Always confirm with a second garage before disputing a bill. WrenchWise is an information tool, not a mechanic.

## License

MIT
