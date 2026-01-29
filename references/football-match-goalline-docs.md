---
name: football-match-goalline-docs
description: Detailed documentation for the Football Match Goal Line API endpoint, including authentication, request parameters, and response field descriptions for goal coordinates and passing sequences.
---

# Football Match Goal Line API Documentation

## Endpoint: Match Goal Line

**URL:** `GET /v1/football/match/goal/line/detail`

This endpoint returns detailed "Goal Line" data for a single match, including the exact coordinates of the goal on the net and the passing sequence leading up to the goal.

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
- **results** (array): List of goal events.

#### Goal Object Fields (`results[]`)

| Field        | Type    | Description                                                            |
|:------------ |:------- |:---------------------------------------------------------------------- |
| `number`     | integer | Goal sequence number in the match.                                     |
| `time`       | integer | Time of goal in seconds.                                               |
| `goal_x`     | string  | Net x-coordinate (Max 9.6). Origin: Top-Left.                          |
| `goal_y`     | string  | Net y-coordinate (Max 3.8). Origin: Top-Left.                          |
| `own_goal`   | integer | `1`: Yes, `0`: No.                                                     |
| `pass`       | array   | List of players involved in the passing sequence.                      |
| `goalkeeper` | object  | The goalkeeper facing the shot: `{ belong, player_id, shirt_number }`. |

#### Pass Object Fields (`pass[]`)

| Field          | Type    | Description                                     |
|:-------------- |:------- |:----------------------------------------------- |
| `belong`       | integer | `1`: Home, `2`: Away.                           |
| `player_id`    | string  | Player ID.                                      |
| `shirt_number` | string  | Jersey number.                                  |
| `x`            | string  | Pitch x-coordinate (Max 100). Origin: Top-Left. |
| `y`            | string  | Pitch y-coordinate (Max 100). Origin: Top-Left. |
| `shooter`      | integer | `1`: This player took the shot.                 |
| `assist`       | integer | `1`: This player provided the assist.           |

### Example Request

```bash
curl "https://api.thesports.com/v1/football/match/goal/line/detail?user=YOUR_USER&secret=YOUR_SECRET&uuid=MATCH_ID"
```
