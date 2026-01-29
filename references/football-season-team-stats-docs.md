---
name: football-season-team-stats-docs
description: Detailed documentation for the Football Season Team Statistics (Newest Season) API endpoint, including authentication, request parameters, and response field descriptions for team performance metrics.
---

# Football Season Team Statistics API Documentation

## Endpoint: Season Team Statistics (Newest Season)

**URL:** `GET /v1/football/season/recent/team/stat`

This endpoint returns detailed team statistics for the current/newest season.

### Authentication

Required for all requests.

- **user** (string): Your API username.
- **secret** (string): Your API secret key.

### Request Parameters

| Name   | Type   | Required | Description    |
|:------ |:------ |:-------- |:-------------- |
| `uuid` | string | Yes      | The Season ID. |

### Response Structure

#### Top-Level Fields

- **code** (integer): HTTP status code.
- **results** (array): List of team season statistics objects.

#### Team Statistics Object Fields (`results[]`)

| Field                 | Type    | Description                         |
|:--------------------- |:------- |:----------------------------------- |
| `team`                | object  | Team details: `{ id, name, logo }`. |
| `matches`             | integer | Total matches played.               |
| `goals`               | integer | Total goals scored.                 |
| `penalty`             | integer | Penalty goals.                      |
| `assists`             | integer | Total assists.                      |
| `red_cards`           | integer | Total red cards.                    |
| `yellow_cards`        | integer | Total yellow cards.                 |
| `shots`               | integer | Total shots.                        |
| `shots_on_target`     | integer | Shots on target.                    |
| `dribble`             | integer | Dribble attempts.                   |
| `dribble_succ`        | integer | Successful dribbles.                |
| `clearances`          | integer | Clearances.                         |
| `blocked_shots`       | integer | Blocked shots.                      |
| `tackles`             | integer | Tackles.                            |
| `passes`              | integer | Total passes.                       |
| `passes_accuracy`     | integer | Successful passes.                  |
| `key_passes`          | integer | Key passes.                         |
| `crosses`             | integer | Total crosses.                      |
| `crosses_accuracy`    | integer | Successful crosses.                 |
| `long_balls`          | integer | Total long balls.                   |
| `long_balls_accuracy` | integer | Successful long balls.              |
| `duels`               | integer | Total duels.                        |
| `duels_won`           | integer | Duels won.                          |
| `fouls`               | integer | Fouls committed.                    |
| `was_fouled`          | integer | Times fouled.                       |
| `goals_against`       | integer | Goals conceded.                     |
| `interceptions`       | integer | Interceptions.                      |
| `offsides`            | integer | Offsides.                           |
| `yellow2red_cards`    | integer | Second yellow leading to red.       |
| `corner_kicks`        | integer | Total corners.                      |
| `ball_possession`     | integer | Average ball possession.            |
| `freekicks`           | integer | Free kicks.                         |
| `freekick_goals`      | integer | Free kick goals.                    |
| `hit_woodwork`        | integer | Times hit post/bar.                 |
| `fastbreaks`          | integer | Fast breaks.                        |
| `fastbreak_shots`     | integer | Shots from fast breaks.             |
| `fastbreak_goals`     | integer | Goals from fast breaks.             |
| `poss_losts`          | integer | Times possession lost.              |
| `saves`               | integer | Saves made.                         |
| `penalty_conceded`    | integer | Penalties conceded.                 |
| `updated_at`          | integer | Unix timestamp of last update.      |

### Usage Recommendations

- **Frequency:** 120 times/min.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/season/recent/team/stat?user=YOUR_USER&secret=YOUR_SECRET&uuid=SEASON_ID"
```
