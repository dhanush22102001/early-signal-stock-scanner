# Early-Signal Stock Scanner

A research-only Python tool that scores a list of stock candidates on four early signals and ranks the ones worth a closer look. Built for learning and watchlist research — **not financial advice, no predictions, no trading.**

## What it does

Reads a CSV of candidates and scores each one out of 100:

| Signal | Weight | Idea |
|---|---|---|
| Unusual volume | 30 | Today's volume vs its 20-day average |
| 5-day momentum | 25 | Price change over the last 5 sessions |
| News count | 25 | News items in the last 7 days |
| Attention | 20 | Mentions vs their usual average |

Candidates scoring **50+** are written to `watchlist.csv` marked `REVIEW REQUIRED`. An empty watchlist is a valid result — it means nothing passed the bar that day.

## Run it

```bash
python3 scanner.py sample_data.csv
```

`sample_data.csv` is fictional example data so you can see the output format. To scan real stocks, supply your own CSV with these columns:

```csv
candidate,volume_today,volume_avg_20d,price_change_5d_pct,news_items_7d,mentions_7d,mentions_avg_7d
```

## First real run (Oct 5, 2026)

Scored a 9-stock India + US watchlist (NIFTY as benchmark, MSFT, GOOG, HINDUNILVR, AMZN, CUPID, TITAN, LALITHAA, WMT). None passed the 50-point threshold; CUPID ranked highest at 46.6 on strong momentum and a guidance-raise catalyst. Attention data was unavailable from free public sources, so that signal scored 0 for every stock (effective cap 80/100) — disclosed, not hidden.

## Rules this project follows

- Scores are a *setup/probability* lens, never a prediction or a buy/sell call.
- Never invent a reason for a price move; if no clear catalyst exists, say so.
- Always check the original sources behind any number before acting on it.

Standard library only (`csv`, `sys`, `datetime`). No network calls, no broker connection, no live feed.
