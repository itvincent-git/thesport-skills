---
name: football-h2h-analysis-docs
description: Detailed documentation for the Football H2H Analysis API endpoint, including authentication, request parameters, and response field descriptions for historical matchups, recent results, future schedules, and goal distribution.
---

# Football H2H Analysis API Documentation

## Endpoint: H2H (Analysis)

**URL:** `GET /v1/football/match/analysis`

This endpoint returns match analysis statistics, including historical head-to-head (H2H) results, recent team form, future schedules, and goal distribution analysis.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type   | Required | Description   |
|:------ |:------ |:-------- |:------------- |
| `uuid` | string | Yes      | The Match ID. |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (object): Analysis data wrapper.

#### Result Fields (`results`)

| Field               | Type   | Description                                                                              |
|:------------------- |:------ |:---------------------------------------------------------------------------------------- |
| `info`              | array  | Core information for the queried match.                                                  |
| `history`           | object | Contains `vs` (H2H), `home` (Recent home team form), and `away` (Recent away team form). |
| `future`            | object | Contains `home` and `away` upcoming matches.                                             |
| `goal_distribution` | object | Contains `home` and `away` goal/conceded data broken down by 15-minute segments.         |

#### Match Info Array Format (`info`, `history.vs[]`, `history.home[]`, etc.)

The match info is returned as a dense array to save bandwidth.
`[MatchID, CompetitionID, StatusID, MatchTime, KickOffTime, HomeInfo, AwayInfo, OddsInfo, MiscInfo, SeasonInfo]`

**Home/Away Info Sub-Array:**
`[TeamID, LeagueRanking, RegularScore, HalfScore, RedCards, YellowCards, Corners, OvertimeScore, PenaltyScore]`

#### Goal Distribution Object (`results.goal_distribution.home/away`)

Contains `all` (total), `home` (at home), and `away` (playing away) sub-objects.
Each has `scored` and `conceded` arrays containing 6 segments (15 mins each).
Segment Format: `[Count, Percentage, StartMin, EndMin]`

### Usage Recommendations

- **Frequency:** 60 times/min.
- **Data Change:** This data changes infrequently; request primarily before match start.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/analysis?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
