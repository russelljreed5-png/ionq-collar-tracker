# IonQ / SkyWater Collar Tracker

A live, shared tracking tool for monitoring the stock component of the IonQ / SkyWater Technology merger payout.

## Background

IonQ announced an acquisition of SkyWater Technology in which SkyWater shareholders receive **$35.00 per share** at closing:

- **$15.00 in cash** (fixed)
- **$20.00 in IonQ common stock** (subject to a stock collar mechanism)

The stock component isn't a fixed dollar amount — it's converted to IonQ shares based on IonQ's **20-trading-day volume-weighted average price (VWAP)** measured just before the deal closes. A collar mechanism puts guardrails on that conversion:

| IonQ 20-day VWAP | Shares received per SKYT share | Stock payout value |
|---|---|---|
| Above $60.19 | 0.3326 (capped) | More than $20 |
| $38.01 – $60.19 | Floats (tracks $20 target) | ~$20 |
| Below $38.01 | 0.5265 (floored) | Less than $20 |

This tracker lets shareholders monitor where IonQ's VWAP sits relative to the collar boundaries in real time, so there are no surprises at closing.

## Features

- **Live shared data** — powered by Firebase Realtime Database. Any price entry added by one person is instantly visible to everyone viewing the page.
- **Rolling 20-trading-day VWAP** — automatically recalculates as new closing prices are added.
- **Collar zone indicator** — shows whether the current VWAP is above the collar (payout > $20), inside (payout ~$20), or below (payout < $20).
- **Share count display** — shows exactly how many IonQ shares per SkyWater share you would receive if the merger closed today.
- **Interactive chart** — plots daily closing prices and the 20-day VWAP against the upper and lower collar boundaries over time.
- **CSV export** — download the full price log with all calculated values.
- **Contributor names** — entries show who added them so everyone knows who's keeping the data current.

## How to use

1. Open the tracker in any browser
2. Enter your name in the "Posting as" field (saved locally on your device)
3. Each trading day after market close, enter IonQ's closing price and click **Add entry**
4. The VWAP, share count, payout value, and collar zone update automatically for everyone viewing the page

## Collar mechanics explained

The collar exists to protect both sides from large swings in IonQ's stock price between the announcement date and the closing date. If IonQ's stock rises significantly, SkyWater shareholders benefit (they still receive 0.3326 shares, which are now worth more than $20). If IonQ's stock falls significantly, SkyWater shareholders are protected from a complete collapse (they still receive 0.5265 shares), though the payout will be less than $20.

The conversion ratio that will actually determine the final payout is calculated using the 20-trading-day VWAP ending three business days before the official closing date — so the window that matters most is the final month of trading before the merger closes.

## Merger timeline

- **Deal announced:** 2025
- **Shareholder vote:** May 8, 2026 (approved)
- **Regulatory status:** FTC Second Request issued April 2026; both companies cooperating
- **Expected closing:** Q3 2026 (estimated)

## Data sources

Historical IonQ closing prices were sourced from public market data. Daily prices going forward are entered manually by contributors. This tracker is for informational purposes only and does not constitute financial advice.
