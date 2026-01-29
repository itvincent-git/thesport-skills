---
name: football-season-player-stats-docs
description: Detailed documentation for the Football Season Player Statistics (Newest Season) API endpoint, including authentication, request parameters, and response field descriptions for player performance metrics across different teams.
---

# Football Season Player Statistics API Documentation

## Endpoint: Season Player Statistics (Newest Season)

**URL:** `GET /v1/football/season/recent/player/stat`

This endpoint returns detailed player statistics for the current/newest season. **Note:** Players who transfer may have multiple entries for different teams.

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
- **results** (array): List of player season statistics objects.

#### Player Statistics Object Fields (`results[]`)

| Field                 | Type    | Description                                                              |
|:--------------------- |:------- |:------------------------------------------------------------------------ |
| `player`              | object  | Player details: `{ id, name, logo, position, country_id, nationality }`. |
| `team`                | object  | Team details: `{ id, name, logo }`.                                      |
| `matches`             | integer | Total matches played.                                                    |
| `court`               | integer | Total appearances (including subs?).                                     |
| `first`               | integer | Number of starts.                                                        |
| `goals`               | integer | Goals scored.                                                            |
| `penalty`             | integer | Penalty goals.                                                           |
| `assists`             | integer | Assists.                                                                 |
| `minutes_played`      | integer | Total minutes played.                                                    |
| `red_cards`           | integer | Red cards.                                                               |
| `yellow_cards`        | integer | Yellow cards.                                                            |
| `shots`               | integer | Total shots.                                                             |
| `shots_on_target`     | integer | Shots on target.                                                         |
| `dribble`             | integer | Dribble attempts.                                                        |
| `dribble_succ`        | integer | Successful dribbles.                                                     |
| `clearances`          | integer | Clearances.                                                              |
| `blocked_shots`       | integer | Blocked shots.                                                           |
| `interceptions`       | integer | Interceptions.                                                           |
| `tackles`             | integer | Tackles.                                                                 |
| `passes`              | integer | Total passes.                                                            |
| `passes_accuracy`     | integer | Successful passes.                                                       |
| `key_passes`          | integer | Key passes.                                                              |
| `crosses`             | integer | Total crosses.                                                           |
| `crosses_accuracy`    | integer | Successful crosses.                                                      |
| `long_balls`          | integer | Total long balls.                                                        |
| `long_balls_accuracy` | integer | Successful long balls.                                                   |
| `duels`               | integer | Total duels.                                                             |
| `duels_won`           | integer | Duels won.                                                               |
| `dispossessed`        | integer | Times lost possession.                                                   |
| `fouls`               | integer | Fouls committed.                                                         |
| `was_fouled`          | integer | Times fouled.                                                            |
| `offsides`            | integer | Offsides.                                                                |
| `yellow2red_cards`    | integer | Second yellow leading to red.                                            |
| `saves`               | integer | Saves made.                                                              |
| `punches`             | integer | Punches made.                                                            |
| `runs_out`            | integer | GK runs out.                                                             |
| `runs_out_succ`       | integer | GK runs out success.                                                     |
| `good_high_claim`     | integer | High ball claims.                                                        |
| `rating`              | integer | Average rating (scaled by 100, e.g. 750 = 7.5).                          |
| `freekicks`           | integer | Free kicks taken.                                                        |
| `freekick_goals`      | integer | Free kick goals.                                                         |
| `hit_woodwork`        | integer | Hit woodwork.                                                            |
| `fastbreaks`          | integer | Fast breaks involved.                                                    |
| `fastbreak_shots`     | integer | Shots from fast breaks.                                                  |
| `fastbreak_goals`     | integer | Goals from fast breaks.                                                  |
| `poss_losts`          | integer | Possession lost.                                                         |
| `aerial_won`          | integer | Aerial duels won.                                                        |
| `aerial_lost`         | integer | Aerial duels lost.                                                       |
| `duel_won`            | integer | Ground duels won.                                                        |
| `duel_lost`           | integer | Ground duels lost.                                                       |
| `big_chance_created`  | integer | Big chances created.                                                     |
| `big_chance_missed`   | integer | Big chances missed.                                                      |
| `updated_at`          | integer | Unix timestamp of last update.                                           |

### Usage Recommendations

- **Frequency:** 120 times/min.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/season/recent/player/stat?user=YOUR_USER&secret=YOUR_SECRET&uuid=SEASON_ID"
```
