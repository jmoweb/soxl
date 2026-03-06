# SOXL Morning Analysis Dashboard

A production-ready, single-file trading dashboard for daily SOXL technical analysis — built with live TradingView data feeds, EMA signal logic, and a clean terminal-style UI.

## Features

- **Live TradingView Chart** — Advanced candlestick chart with EMA 9 & EMA 21 overlays, RSI, and Volume built in
- **Live Ticker Tape** — Real-time prices for SOXL, SOXX, NVDA, AMD, INTC, AVGO, TSM, QCOM, SOX Index, S&P 500
- **SOX Index Mini Chart** — Live semiconductor index overview panel
- **Signal Engine** — Auto-reads BUY / WATCH / CAUTION / WAIT based on price vs EMA positioning
- **Sell Target Calculator** — Auto-generates +10% and +15% exit targets from entry price
- **Risk/Reward Panel** — Stop loss at -5%, R/R ratio display
- **Key Level Tracker** — Bull trigger, resistance levels, danger zone, hard stop — all dynamic
- **Signal History Log** — Tracks daily signals over 7 days
- **Morning Notes** — Timestamped notes pad for pre-market observations
- **Entry Risk Bar** — Visual risk gauge based on average EMA distance

## Usage

### Option 1 — Open directly in browser
```bash
# No server needed — just open the file
open index.html
```

### Option 2 — Serve locally
```bash
# Python
python3 -m http.server 8080

# Node
npx serve .
```

### Option 3 — Deploy to GitHub Pages
1. Fork or push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to `main` branch, root `/`
4. Your dashboard will be live at `https://yourusername.github.io/soxl-dashboard`

## Daily Workflow

Each morning:
1. Open the dashboard
2. Check the live TradingView chart for current price
3. Enter **Current Price**, **EMA 9**, **EMA 21**, and **Previous Close**
4. Hit **↺ UPDATE** (or press Enter)
5. Read the signal and key levels
6. Add morning notes as you watch the open

## Signal Logic

| Signal | Condition | Meaning |
|--------|-----------|---------|
| **BUY** | Price > EMA9 > EMA21 | Full bullish stack — clean entry zone |
| **WATCH** | Price > EMA9, Price < EMA21 | Building momentum — wait for EMA21 break |
| **CAUTION** | Price < EMA9, Price > EMA21 | Short-term weakness in broader uptrend |
| **WAIT** | Price < EMA9 < EMA21 | Full bearish stack — no entry signal |

## Targets (from entry price)

| Target | Level | Action |
|--------|-------|--------|
| T1 | +10% | First sell / partial exit |
| T2 | +15% | Full exit target |
| Stop Loss | -5% | Exit without hesitation |

## Tech Stack

- **Vanilla HTML/CSS/JS** — zero dependencies, zero build step
- **TradingView Widgets** — Advanced Chart, Ticker Tape, Mini Symbol Overview (all free embeds)
- **Google Fonts** — Orbitron + Space Mono
- Single file: `index.html`

## Customization

To track a different ticker, find and replace all instances of `SOXL` / `NASDAQ:SOXL` in `index.html` with your symbol.

---

> **Disclaimer**: Not financial advice. For personal analysis use only.
