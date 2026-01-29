---
name: football-player-match-stats-docs
description: Detailed documentation for the Football Match Player Statistics API endpoint, including authentication, request parameters, and response field descriptions for goals, assists, passes, and defensive stats.
---

# Football Match Player Statistics API Documentation

## Endpoint: Match Player Statistics
**URL:** `GET /v1/football/match/player_stats/list`

This endpoint returns player-specific statistics for matches where data has changed in the last 120 seconds. It provides a full update of the match's player stats.

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
- **code** (integer): HTTP status code.
- **results** (array): List of match objects containing player statistics.

#### Match Results Fields (`results[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `id` | string | Unique Match ID. |
| `player_stats` | array | List of player statistics objects. |

#### Player Statistics Fields (`player_stats[]`)

| Field | Type | Description |
| :--- | :--- | :--- |
| `player_id` | string | Player ID. |
| `team_id` | string | Team ID. |
| `first` | integer | `1`: Starter, `0`: No. |
| `minutes_played` | integer | Total minutes played. |
| `goals` | integer | Goals scored. |
| `penalty` | integer | Penalty goals. |
| `assists` | integer | Assists. |
| `red_cards` | integer | Red cards. |
| `yellow_cards` | integer | Yellow cards. |
| `shots` | integer | Total shots. |
| `shots_on_target` | integer | Shots on target. |
| `dribble` | integer | Dribble attempts. |
| `dribble_succ` | integer | Successful dribbles. |
| `clearances` | integer | Clearances made. |
| `blocked_shots` | integer | Shots blocked. |
| `interceptions` | integer | Interceptions. |
| `tackles` | integer | Tackles made. |
| `passes` | integer | Total passes. |
| `passes_accuracy` | integer | Successful passes. |
| `key_passes` | integer | Key passes. |
| `crosses` | integer | Total crosses. |
| `crosses_accuracy` | integer | Successful crosses. |
| `long_balls` | integer | Total long balls. |
| `long_balls_accuracy`| integer | Successful long balls. |
| `duels` | integer | Total duels. |
| `duels_won` | integer | Duels won. |
| `dispossessed` | integer | Times lost possession. |
| `fouls` | integer | Fouls committed. |
| `was_fouled` | integer | Times fouled. |
| `offsides` | integer | Offsides. |
| `yellow2red_cards` | integer | Second yellow leading to red. |
| `saves` | integer | Saves made (Goalkeeper). |
| `punches` | integer | Punches made (Goalkeeper). |
| `runs_out` | integer | Goalkeeper exits from line. |
| `runs_out_succ` | integer | Successful goalkeeper exits. |
| `good_high_claim` | integer | Successful high ball catches. |
| `rating` | float | Match rating (out of 10). |
| `freekicks` | integer | Free kicks taken. |
| `freekick_goals` | integer | Free kick goals. |
| `hit_woodwork` | integer | Times hit post/bar. |
| `fastbreaks` | integer | Fast break instances. |
| `fastbreak_shots` | integer | Shots from fast breaks. |
| `fastbreak_goals` | integer | Goals from fast breaks. |
| `poss_losts` | integer | Times ball possession lost. |
| `aerial_won` | integer | Aerial duels won. |
| `aerial_lost` | integer | Aerial duels lost. |
| `duel_won` | integer | Ground duels won. |
| `duel_lost` | integer | Ground duels lost. |

### Usage Recommendations
- **Frequency:** Poll every **1 minute**.

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/player_stats/list?user=YOUR_USER&secret=YOUR_SECRET"
```
