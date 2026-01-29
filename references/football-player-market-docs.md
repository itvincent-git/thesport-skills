---
name: football-player-market-docs
description: Documentation for the Football Player Market API endpoint, tracking historical changes in player market values and currency units.
---

# Football Player Market API Documentation

## Endpoint: Player Market

**URL:** `GET /v1/football/player/market/list`

Historical market value data for players.

### Response Structure

#### Market Record Fields (`results[].history[]`)

| Field                   | Type    | Description                          |
|:----------------------- |:------- |:------------------------------------ |
| `market_time`           | integer | Timestamp of value change.           |
| `market_value`          | integer | Numeric market value.                |
| `market_value_currency` | string  | Currency unit.                       |
| `team_id`               | string  | Team ID at the time of valuation.    |
| `age`                   | integer | Player age at the time of valuation. |
