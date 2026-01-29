---
name: football-realtime-data-docs
description: Detailed documentation for the Football Real-time Data API endpoint, including authentication, request parameters, and response field descriptions for live scores, incidents, and statistics.
---

# Football Real-time Data API Documentation

## Endpoint: Real-time Data
**URL:** `GET /v1/football/match/detail_live`

This endpoint returns scores, match incidents, and technical statistics for matches updated in the last 120 minutes. Matches beyond 120 minutes are also returned if updated.

### Authentication
Required for all requests.
- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `user` | string | Yes | Username. |
| `secret` | string | Yes | API Key. |

### Response Structure

#### Top-Level Fields
- **code** (integer): HTTP-like status code (e.g., 200).
- **results** (array): List of real-time match data objects.

#### Match Live Data Object Fields (`results[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | string | Unique Match ID. |
| `score` | array | Live score array: `[MatchID, Status, HomeScores, AwayScores, KickOffTime, Ignored]`. <br> **Note:** See `football-match-recent-docs.md` for `HomeScores`/`AwayScores` structure (Regular, Half, Red, Yellow, Corner, OT, PK). |
| `stats` | array | Technical statistics. Array of objects: `{ type: int, home: int, away: int }`. <br> Types: Corners, Shots (on/off target), Dangerous Attacks, Possession, etc. |
| `incidents` | array | Match events. Array of objects: `{ type: int, position: int, time: int, player_name: string, ... }`. <br> Types: Goals, Cards, Substitutions, VAR, etc. |
| `tlive` | array | Text commentary/live ticker. Array of objects: `{ time: string, data: string, position: int }`. |

### Usage Recommendations
- **Frequency:** Poll every **2 seconds** for live applications.
- **Match Minutes Calculation:**
  - First half: `(current_timestamp - kickoff_timestamp) / 60 + 1`
  - Second half: `(current_timestamp - kickoff_timestamp) / 60 + 45 + 1`

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/detail_live?user=YOUR_USER&secret=YOUR_SECRET"
```
