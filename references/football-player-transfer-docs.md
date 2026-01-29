---
name: football-player-transfer-docs
description: Documentation for the Football Player Transfer API endpoint, detailing player movements between clubs, transfer types, fees, and dates.
---

# Football Player Transfer API Documentation

## Endpoint: Player Transfer

**URL:** `GET /v1/football/player/transfer/list`

Tracks player transfers, loans, and releases across clubs globally.

### Request Parameters

Same as Team Injury (`page`, `time`, `uuid`).

### Response Structure

#### Result Fields (`results[]`)

| Field      | Type   | Description                       |
|:---------- |:------ |:--------------------------------- |
| `id`       | string | Player ID.                        |
| `player`   | object | Basic player info (`id`, `name`). |
| `transfer` | array  | List of transfer events.          |

#### Transfer Event Fields (`results[].transfer[]`)

| Field           | Type    | Description                                                                                         |
|:--------------- |:------- |:--------------------------------------------------------------------------------------------------- |
| `from_team_id`  | string  | Selling/loaning club ID.                                                                            |
| `to_team_id`    | string  | Buying/borrowing club ID.                                                                           |
| `transfer_type` | integer | 1: Rental, 2: Rental End, 3: Transfer, 4: Retirement, 5: Draft, 6: Released, 7: Signed, 8: Unknown. |
| `transfer_time` | integer | Date of transfer.                                                                                   |
| `transfer_fee`  | integer | Numeric fee.                                                                                        |
| `transfer_desc` | string  | Text description of the deal (including currency).                                                  |
