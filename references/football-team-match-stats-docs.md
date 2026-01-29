---
name: football-team-match-stats-docs
description: Detailed documentation for the Football Match Team Statistics API endpoint, including authentication, request parameters, and response field descriptions for team-level performance metrics.
---

# Football Match Team Statistics API Documentation

## Endpoint: Match Team Statistics

**URL:** `GET /v1/football/match/team_stats/list`

This endpoint returns team-level statistics for matches where data has changed in the last 120 seconds.

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
- **results** (array): List of match objects containing team statistics.

#### Match Results Fields (`results[]`)

| Field   | Type   | Description                                                   |
|:------- |:------ |:------------------------------------------------------------- |
| `id`    | string | Unique Match ID.                                              |
| `stats` | array  | List of team statistics objects (usually two: home and away). |

#### Team Statistics Fields (`stats[]`)

| Field                 | Type    | Description                   |
|:--------------------- |:------- |:----------------------------- |
| `team_id`             | string  | Team ID.                      |
| `goals`               | integer | Total goals.                  |
| `penalty`             | integer | Penalty goals.                |
| `assists`             | integer | Assists.                      |
| `red_cards`           | integer | Red cards.                    |
| `yellow_cards`        | integer | Yellow cards.                 |
| `shots`               | integer | Total shots.                  |
| `shots_on_target`     | integer | Shots on target.              |
| `dribble`             | integer | Dribble attempts.             |
| `dribble_succ`        | integer | Successful dribbles.          |
| `clearances`          | integer | Clearances.                   |
| `blocked_shots`       | integer | Blocked shots.                |
| `interceptions`       | integer | Interceptions.                |
| `tackles`             | integer | Tackles.                      |
| `passes`              | integer | Total passes.                 |
| `passes_accuracy`     | integer | Successful passes.            |
| `key_passes`          | integer | Key passes.                   |
| `crosses`             | integer | Total crosses.                |
| `crosses_accuracy`    | integer | Successful crosses.           |
| `long_balls`          | integer | Total long balls.             |
| `long_balls_accuracy` | integer | Successful long balls.        |
| `duels`               | integer | Total duels.                  |
| `duels_won`           | integer | Duels won.                    |
| `fouls`               | integer | Fouls committed.              |
| `was_fouled`          | integer | Times fouled.                 |
| `goals_against`       | integer | Goals conceded.               |
| `offsides`            | integer | Offsides.                     |
| `yellow2red_cards`    | integer | Second yellow leading to red. |
| `corner_kicks`        | integer | Total corners.                |
| `ball_possession`     | integer | Ball possession percentage.   |
| `freekicks`           | integer | Free kicks.                   |
| `freekick_goals`      | integer | Free kick goals.              |
| `hit_woodwork`        | integer | Times hit post/bar.           |
| `fastbreaks`          | integer | Fast breaks.                  |
| `fastbreak_shots`     | integer | Shots from fast breaks.       |
| `fastbreak_goals`     | integer | Goals from fast breaks.       |
| `poss_losts`          | integer | Times possession lost.        |
| `aerial_won`          | integer | Aerial duels won.             |
| `aerial_lost`         | integer | Aerial duels lost.            |
| `duel_won`            | integer | Ground duels won.             |
| `duel_lost`           | integer | Ground duels lost.            |

### Usage Recommendations

- **Frequency:** Poll every **1 minute**.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/team_stats/list?user=YOUR_USER&secret=YOUR_SECRET"
```
