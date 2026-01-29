---
name: football-historical-compensation-docs
description: Detailed documentation for the Football Historical Compensation API endpoint, including authentication, request parameters, and response field descriptions for historical matchups, recent form, and same-odds performance analysis.
---

# Football Historical Compensation API Documentation

## Endpoint: Historical Compensation

**URL:** `GET /v1/football/compensation/list`

This endpoint returns comprehensive statistics for matches starting within the next 30 days, specifically focusing on historical head-to-head records, recent team form, and performance in matches with identical initial odds (Same Compensation).

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type    | Required | Description                                                                                  |
|:------ |:------- |:-------- |:-------------------------------------------------------------------------------------------- |
| `page` | integer | No       | Page number (starts at 1). Default is 100 records per page. Use for full updates.            |
| `time` | integer | No       | Unix timestamp. Returns records updated at or after this time. Recommended frequency: 1 min. |
| `uuid` | string  | No       | Filter by a specific match ID.                                                               |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (array): List of match analysis objects.

#### Analysis Object Fields (`results[]`)

| Field      | Type   | Description                                          |
|:---------- |:------ |:---------------------------------------------------- |
| `id`       | string | Unique Match ID.                                     |
| `history`  | object | H2H summary: `{ home: Stats, away: Stats }`.         |
| `recent`   | object | Recent form summary: `{ home: Stats, away: Stats }`. |
| `similar`  | object | Performance in matches with similar odds.            |
| `analysis` | array  | Winning/Drawing/Losing probability per odds company. |

#### Stats Object Structure (`history`, `recent`)

- `won_count` (int): Number of wins.
- `drawn_count` (int): Number of draws.
- `lost_count` (int): Number of losses.
- `rate` (float): Win rate.

#### Similar Odds Object Fields (`similar`)

- `teams` (array): List of teams involved in similar-odds matches.
- `competitions` (array): List of competitions involved.
- `companies` (array): List of odds companies.
- `europe` (array): Detailed results for matches with same initial Euro odds.
  - `total`, `won`, `draw`, `loss` (int).
  - `odds` (array): Initial odds `[Win, Draw, Lose]`.
  - `matches` (array): List of historical match results with these odds.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/compensation/list?user=YOUR_USER&secret=YOUR_SECRET&page=1"
```
