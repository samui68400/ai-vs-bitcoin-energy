# ⚡ AI vs Bitcoin — Live Energy Tracker

**The first open-source tracker that overlays, in real time, the electricity consumption of global AI and the Bitcoin network.**

🔴 **Live demo (EN):** https://samui68400.github.io/ai-vs-bitcoin-energy/en.html
🇫🇷 **Version française :** https://samui68400.github.io/ai-vs-bitcoin-energy/

---

## Why this exists

Everyone argues about whether AI or Bitcoin "wastes" more electricity. Almost nobody looks at the actual numbers side by side — because no tool existed to do it. Static comparisons exist (IEA, Cambridge, Digiconomist), but no live, overlaid view.

**The headline the chart shows:** AI overtook Bitcoin's power draw around late 2024, and the gap is widening every quarter. By 2030, AI is projected to consume **3× more** electricity than the entire Bitcoin network.

## Methodology — measured vs. modeled

The core insight behind this tracker is an asymmetry most comparisons ignore:

### 🟠 Bitcoin: measured, not estimated (high confidence)

Bitcoin is the only energy system on Earth whose total activity is publicly observable, second by second. Global computing power (hashrate) can be read directly from the blockchain.

```
Power (GW) = Hashrate (EH/s) × Fleet efficiency (J/TH) × PUE ÷ 1000
```

This page fetches the live hashrate (3-day average from the [mempool.space](https://mempool.space) public API) and applies a fleet efficiency (~16.5 J/TH) and PUE (1.10) calibrated to reproduce the central estimate of the **Cambridge Bitcoin Electricity Consumption Index (CBECI)** — the academic reference cited by the IEA. Model error margin: ~±15%.

### 🔵 AI: nowcast, honestly labeled (medium confidence)

There is no "hashrate" for AI. Hyperscalers do not publish real-time consumption — any tool claiming "live AI power" would be lying. The only honest approach is a **nowcast**: daily interpolation between solid annual anchor points, with an explicit uncertainty band.

Anchors: ~110 TWh (2024), ~190 TWh (2025, ≈40% of the 485 TWh consumed by global data centers), IEA trajectory toward a tripling of AI-focused facilities by 2030. The ±25% band spans the gap between published models (IEA, SemiAnalysis, de Vries/Digiconomist).

This is how central banks treat unobservable data: **anchor, bound, display the uncertainty.** The chart's reliability comes from showing its uncertainty instead of hiding it.

## Features

- 📡 Live Bitcoin power gauge from on-chain hashrate (updates on each load)
- ⚡ AI power nowcast, interpolated daily between IEA anchors
- 📈 Overlaid chart 2020 → 2030 with uncertainty bands, crossover point, and hover tooltip (incl. AI/BTC ratio)
- ⏱ Session counter: kWh consumed by both systems since you opened the page
- 🪶 Single HTML file, zero dependencies, zero build step — deploy anywhere

## Data sources

| Source | Used for |
|---|---|
| [Cambridge CBECI](https://ccaf.io/cbnsi/cbeci) | Bitcoin consumption model (reference) |
| [mempool.space API](https://mempool.space/graphs/mining/hashrate-difficulty) | Real-time on-chain hashrate |
| [IEA — Energy & AI](https://www.iea.org/reports/energy-and-ai) | Data center & AI trajectories (415 TWh 2024 → ~945 TWh 2030) |
| [Digiconomist](https://digiconomist.net/bitcoin-energy-consumption) | Upper-bound estimates |

## Run it yourself

No install needed. Clone or download, then open `index.html` (FR) or `en.html` (EN) in any browser. To self-host: drop the files on GitHub Pages, Cloudflare Pages, or any static host.

## Caveats

- AI figures are estimates, not measurements — that's the entire point of the uncertainty band. Anchor values are updated manually when IEA/CBECI publish revisions.
- Bitcoin fleet efficiency (J/TH) drifts as hardware improves; the constant is recalibrated against CBECI periodically.
- "AI" here means accelerated servers (GPU/TPU) + cooling overhead, not total data center consumption.

## Author

Built by **Nicolas** — macro, markets & crypto analysis.

- 🐦 X: [@YOUR_HANDLE](https://x.com/LCM_alpha)
- 📬 Newsletter (FR): [Les Clefs des Marchés](https://substack.com/@lesclefsdesmarches)

*If this tracker is useful, a ⭐ on the repo helps more people find it.*

## License

MIT — use it, fork it, embed it. Attribution appreciated.
