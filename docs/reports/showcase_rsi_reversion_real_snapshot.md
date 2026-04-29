# AlphaEvo Real-Data Showcase: RSI Reversion

> Research tooling only. Not investment advice.

## Summary

| Item | Value |
|------|-------|
| Run ID | `20260429T143645Z_rsi_reversion_1181fd2d` |
| Generated At | `2026-04-29T14:36:45+00:00` |
| Data Source | bundled frozen yfinance snapshot |
| Snapshot | `us_tech_showcase_2025_2026` |
| Date Range | 2025-02-11 to 2026-04-10 |
| Symbols | AAPL, AMD, MSFT, NVDA, TSLA |
| Baseline | `rsi_reversion_v1` score 8.1% |
| Champion | `rsi_reversion_v4` score 37.7% |

## Evolution Results

| Round | Strategy | Change | Signals | Win Rate | Avg Return | Max DD | Score |
|-------|----------|--------|---------|----------|------------|--------|-------|
| 1 | `rsi_reversion_v1` | baseline | 0 | 0.0% | 0.00% | 0.0% | 8.1% |
| 2 | `rsi_reversion_v2` | `entry.logic`: `and` -> `or` | 79 | 40.5% | -0.01% | 54.1% | 17.8% |
| 3 | `rsi_reversion_v3` | `exit.stop_loss.value`: `0.05` -> `0.08` | 65 | 52.3% | 1.20% | 38.7% | 22.8% |
| 4 | `rsi_reversion_v4` | `exit.max_holding_days`: `10` -> `14` | 57 | 47.4% | 1.50% | 36.8% | 37.7% |

## Research Committee

| Round | Analyst | Status | Verdict |
|-------|---------|--------|---------|
| 1 | Technical Analyst | fail | Entry stack is too strict for a reliable research sample. |
| 1 | Risk Analyst | pass | Drawdown and loss clustering are within the research tolerance band. |
| 1 | Overfit Critic | fail | Sample is too small to trust improvement claims. |
| 1 | Data Quality Auditor | pass | Data source and symbol basket are explicit enough for a showcase. |
| 1 | Mutation Planner | pass | Plan starts by unlocking enough signals for a valid retest. |
| 2 | Technical Analyst | fail | Signals are tradable but expected return is not yet positive. |
| 2 | Risk Analyst | fail | Drawdown is too high for promotion. |
| 2 | Overfit Critic | fail | Anti-overfit checks reject promotion. |
| 2 | Data Quality Auditor | pass | Data source and symbol basket are explicit enough for a showcase. |
| 2 | Mutation Planner | pass | Plan changes one controlled lever at a time. |
| 3 | Technical Analyst | pass | Technical signal has enough trades and positive payoff shape. |
| 3 | Risk Analyst | watch | Risk is usable for research but still needs exit discipline. |
| 3 | Overfit Critic | fail | Anti-overfit checks reject promotion. |
| 3 | Data Quality Auditor | pass | Data source and symbol basket are explicit enough for a showcase. |
| 3 | Mutation Planner | pass | Plan changes one controlled lever at a time. |
| 4 | Technical Analyst | pass | Technical signal has enough trades and positive payoff shape. |
| 4 | Risk Analyst | watch | Risk is usable for research but still needs exit discipline. |
| 4 | Overfit Critic | fail | Anti-overfit checks reject promotion. |
| 4 | Data Quality Auditor | pass | Data source and symbol basket are explicit enough for a showcase. |
| 4 | Mutation Planner | watch | No mutation plan is available; evaluate current version only. |

## Mutation Evidence

### Round 2: `rsi_reversion_v2`
- `entry.logic` changed from `and` to `or`.
  Rationale: Baseline fired too few signals; test OR logic to unlock oversold reversal candidates without adding complexity.

### Round 3: `rsi_reversion_v3`
- `exit.stop_loss.value` changed from `0.05` to `0.08`.
  Rationale: Losses were being cut inside normal volatility; test a wider stop and require the retest to improve.

### Round 4: `rsi_reversion_v4`
- `exit.max_holding_days` changed from `10` to `14`.
  Rationale: Mean reversion needed more time to complete; test a longer holding window while watching drawdown.

## Run Provenance

| Field | Value |
|-------|-------|
| Strategy Hash | `41beb2349b71` |
| Data Fingerprint | `1181fd2d09f0` |
| Data Reproducibility | `replayable_snapshot` |
| Adapter | `yfinance` |
| Config | `showcase_default_v1` |

Live reruns can differ because public providers may revise historical data.
