---
name: football-season-team-stats-all-docs
description: Documentation for the Football Season Team Statistics (All Season) API endpoint, providing detailed statistical data for teams across historical seasons.
---

# Football Season Team Statistics (All Season) API Documentation

## Endpoint: Season team statistics(all season)
**URL:** `GET /v1/football/season/team/stat`

Return to the season team statistics details.
Request times: 120 times/min.

### Authentication
Required for all requests.
- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name | Type | Required | Description |
| :--- | :--- | :--- | :--- |
| `uuid` | string | Yes | Season ID. |

### Response Structure
(Same as "Season team statistics(newest season)" `results[]` item structure).

#### Result Fields (`results[]`)
- `team` (object): Team info.
- `matches`, `goals`, `penalty`, `assists`, `red_cards`, `yellow_cards`, `shots`, `shots_on_target`, `dribble`, `dribble_succ`, `clearances`, `blocked_shots`, `tackles`, `passes`, `passes_accuracy`, `key_passes`, `crosses`, `crosses_accuracy`, `long_balls`, `long_balls_accuracy`, `duels`, `duels_won`, `fouls`, `was_fouled`, `goals_against`, `interceptions`, `offsides`, `yellow2red_cards`, `corner_kicks`, `ball_possession`, `freekicks`, `freekick_goals`, `hit_woodwork`, `fastbreaks`, `fastbreak_shots`, `fastbreak_goals`, `poss_losts`, `saves`, `penalty_conceded`.
- `updated_at` (integer): Update time.
