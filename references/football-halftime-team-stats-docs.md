---
name: football-halftime-team-stats-docs
description: Detailed documentation for the Football Match Team Half-time Statistics API endpoint, including authentication, request parameters, and response field descriptions for period-specific performance data.
---

# Football Match Team Half-time Statistics API Documentation

## Endpoint: Match Team Half-time Statistics

**URL:** `GET /v1/football/match/half/team_stats/list`

This endpoint returns team-level statistics specifically broken down by match periods (first half, second half, overtime) for matches where data has changed in the last 120 seconds.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name     | Type   | Required | Description |
|:-------- |:------ |:-------- |:----------- |
| `user`   | string | Yes      | Username.   |
| `secret` | string | Yes      | API Key.    |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (array): List of match objects containing period-specific team statistics.

#### Match Results Fields (`results[]`)

| Field  | Type   | Description                                                                                       |
|:------ |:------ |:------------------------------------------------------------------------------------------------- |
| `id`   | string | Unique Match ID.                                                                                  |
| `Sign` | object | Map of periods: `ft` (Full Time), `p1` (1st Half), `p2` (2nd Half), `o1` (OT 1st), `o2` (OT 2nd). |

#### Period Object Fields (`Sign.ft/p1/p2...`)

The keys within each period object are **Statistics IDs**. Each ID maps to an array `[HomeValue, AwayValue]`.

| Stat ID | Description                                                                                     |
|:------- |:----------------------------------------------------------------------------------------------- |
| *ID*    | Refer to Status Code -> Half-time Statistics for mapping IDs to metrics (e.g., goals, corners). |

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/half/team_stats/list?user=YOUR_USER&secret=YOUR_SECRET"
```
