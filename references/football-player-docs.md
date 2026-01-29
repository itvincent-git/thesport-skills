---
name: football-player-docs
description: Detailed documentation for the Football Player API endpoint, including authentication, request parameters, and response field descriptions.
---

# Football Player API Documentation

## Endpoint: Player List

**URL:** `GET /v1/football/player/with_stat/list`

This endpoint returns full player data, including statistics and personal information. Supports both full and incremental updates based on time.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type    | Required | Description                                                                                  |
|:------ |:------- |:-------- |:-------------------------------------------------------------------------------------------- |
| `page` | integer | No       | Page number (starts at 1). Default is 1000 records per page. Use for full updates.           |
| `time` | integer | No       | Unix timestamp. Returns records updated at or after this time. Recommended frequency: 1 min. |
| `uuid` | string  | No       | Filter by a specific unique identifier.                                                      |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP-like status code (e.g., 200).
- **query** (object): Metadata about the request.
- **results** (array): List of player objects.

#### Player Object Fields (`results[]`)

| Field                   | Type    | Description                                                                                                     |
|:----------------------- |:------- |:--------------------------------------------------------------------------------------------------------------- |
| `id`                    | string  | Unique Player ID.                                                                                               |
| `team_id`               | string  | Current Team ID. (0 if retired, free agent, or unknown).                                                        |
| `name`                  | string  | Full name of the player.                                                                                        |
| `short_name`            | string  | Abbreviated name.                                                                                               |
| `logo`                  | string  | URL string for the player logo.                                                                                 |
| `national_logo`         | string  | National team logo (if applicable).                                                                             |
| `age`                   | integer | Age of the player.                                                                                              |
| `birthday`              | integer | Timestamp of birth.                                                                                             |
| `weight`                | integer | Weight in kg (likely).                                                                                          |
| `height`                | integer | Height in cm (likely).                                                                                          |
| `country_id`            | string  | ID of the country/region.                                                                                       |
| `nationality`           | string  | Nationality string.                                                                                             |
| `market_value`          | integer | Market value.                                                                                                   |
| `market_value_currency` | string  | Currency of market value.                                                                                       |
| `contract_until`        | integer | Timestamp of contract expiration.                                                                               |
| `preferred_foot`        | integer | `1`: Left, `2`: Right, `3`: Both, `0`: Unknown.                                                                 |
| `ability`               | array   | Array of ability scores (e.g., [TypeID, Rating, Avg]). Types: 1-Save, 2-Pre-judgment, 6-Attack, 7-Defense, etc. |
| `characteristics`       | array   | Array of technical features (e.g., [[TypeID, Ranking]]). Types: 1-Unloading, 2-Penalty, 4-Long Shot, etc.       |
| `position`              | string  | Main position category (F, M, D, G).                                                                            |
| `positions`             | array   | Detailed positions (e.g., ["RW", ["ST"]]).                                                                      |
| `uid`                   | string  | Merged/Canonical ID if this is a duplicate.                                                                     |
| `deathday`              | integer | Timestamp of death (if applicable).                                                                             |
| `retire_time`           | integer | Timestamp of retirement (if applicable).                                                                        |
| `updated_at`            | integer | Unix timestamp of the last update.                                                                              |

### Example Request

**Full Sync:**

```bash
curl "https://api.thesports.com/v1/football/player/with_stat/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```

**Incremental Update:**

```bash
curl "https://api.thesports.com/v1/football/player/with_stat/list?user=YOUR_USER&secret=YOUR_SECRET&time=1769680800"
```
