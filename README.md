# Corporate Actions Tracker

Tracks the dividend and stock split history for three blue-chip holdings:

- **Apple Inc. (AAPL)** — Cupertino, California
- **The Coca-Cola Company (KO)** — Atlanta, Georgia
- **Johnson & Johnson (JNJ)** — New Brunswick, New Jersey

Data is sourced from Yahoo Finance.

`.github/workflows/smoke.yml` is a placeholder workflow that stands in for the
corporate-actions pipeline until the real implementation lands.

## Data files

| File | Contents |
|------|----------|
| `data/splits.csv` | Stock split history — columns `ticker,date,ratio`, one row per split |

## Most recent dividends

Amounts and ex-dates exactly as returned by the Yahoo Finance data pull
(2026-10-25):

| Ticker | Company | Amount | Ex-date |
|--------|---------|--------|---------|
| AAPL | Apple Inc. | $0.27 | 2026-08-10 |
| KO | The Coca-Cola Company | $0.53 | 2026-09-15 |
| JNJ | Johnson & Johnson | $1.34 | 2026-08-25 |

## Data notes

- Yahoo's `exDividendDate` profile field can refer to the *next* announced
  ex-dividend date rather than the most recent one (KO: 2026-12-01; JNJ:
  2026-11-24, announced at $1.34). The table above reports the most recent
  dividend that has actually gone ex.
- Yahoo's chart-events endpoint reports KO's 1977 and 1986 splits with the
  ratios swapped (3:1 / 2:1). The values in `data/splits.csv` follow the
  actions feed (2:1 / 3:1), which is also the source of the dividend history.
- KO's 1965 and JNJ's 1967 splits appear in the actions feed but not in the
  chart-events feed; they are included per the actions feed.
