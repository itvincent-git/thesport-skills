---
name: football-season-player-stats-all-docs
description: Documentation for the Football Season Player Statistics (All Season) API endpoint, providing detailed statistical data for players across historical seasons.
---

# Football Season Player Statistics (All Season) API Documentation

## Endpoint: Season player statistics(all season)

**URL:** `GET /v1/football/season/player/stat`

Return to the season player statistics details.
Request times: 120 times/min.

### Authentication

Required for all requests.

- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name   | Type   | Required | Description |
|:------ |:------ |:-------- |:----------- |
| `uuid` | string | Yes      | Season ID.  |

### Response Structure

(Same as "Season player statistics(newest season)" `results[]` item structure).

#### Result Fields (`results[]`)

- `player` (object): Player info.
- `team` (object): Team info.
- `matches`, `court`, `first`, `goals`, `penalty`, `assists`, `minutes_played`, `red_cards`, `yellow_cards`, `shots`, `shots_on_target`, `dribble`, `dribble_succ`, `clearances`, `blocked_shots`, `interceptions`, `tackles`, `passes`, `passes_accuracy`, `key_passes`, `crosses`, `crosses_accuracy`, `long_balls`, `long_balls_accuracy`, `duels`, `duels_won`, `dispossessed`, `fouls`, `was_fouled`, `offsides`, `yellow2red_cards`, `saves`, `punches`, `runs_out`, `runs_out_succ`, `good_high_claim`, `rating`, `freekicks`, `freekick_goals`, `hit_woodwork`, `fastbreaks`, `fastbreak_shots`, `fastbreak_goals`, `poss_losts`, `big_chance_created`, `big_chance_missed`.
- `updated_at` (integer): Update time.
