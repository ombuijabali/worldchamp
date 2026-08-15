# Testing Protocol

## Phase gate

No phase advances until its current behavior is visually checked on TradingView.

## Seven-day development window

During development, the indicator can restrict overlays and diagnostics to the most recent seven calendar days. This keeps visual inspection manageable.

## Phase 0 checks

- Run on a standard 5-minute chart.
- Confirm the chart-timeframe guard reports 5M as valid.
- Confirm 4H, 1H, and 15M confirmed OHLC values update only after their source bars close.
- Confirm the New York active session toggles at the configured times.
- Confirm the dashboard updates without labels or boxes cluttering the chart.
- Confirm enabling Debug shows only lightweight test plots.
- Confirm disabling the seven-day window allows full-history display behavior.
