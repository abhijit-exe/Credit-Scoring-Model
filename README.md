# Aave V2 Wallet Credit Scoring

## Goal
Assign a credit score (0–1000) to each wallet based on its historical transaction behavior on Aave V2 (Polygon). The goal is to detect responsible vs. risky usage patterns using unsupervised ML.

## Methodology

- **Input:** JSON file with wallet-level transactions
- **Feature Engineering:**
  - Counts: deposits, borrows, repays, redemptions, liquidations
  - Monetary volume: total USD deposited, borrowed, repaid
  - Ratios: repay-to-borrow, liquidation rate
  - Duration: activity timespan
- **Scoring Model:** `IsolationForest` to detect behavioral anomalies
- **Output:** Scaled score from 0 (risk) to 1000 (reliable)

## Architecture & Flow

```text
Raw JSON → Feature Extraction → IsolationForest Scoring → Score Normalization → Analysis
