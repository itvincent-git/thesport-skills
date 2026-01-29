---
name: football-team-injury-docs
description: Documentation for the Football Team Injury API endpoint, providing full and incremental updates for player injuries, suspensions, and questionable status.
---

# Football Team Injury API Documentation

## Endpoint: Team Injury

**URL:** `GET /v1/football/team/injury/list`

Provides data on player injuries and availability for teams. Supports full sync (pagination) and incremental updates (timestamp).

### Authentication

Required for all requests.

- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name   | Type    | Description                                                              |
|:------ |:------- |:------------------------------------------------------------------------ |
| `page` | integer | Page number for full sync (starting from 1).                             |
| `time` | integer | Unix timestamp for incremental updates (returns records >= update time). |
| `uuid` | string  | Query a specific record by ID.                                           |

### Response Structure

#### Result Fields (`results[]`)

| Field        | Type    | Description                     |
|:------------ |:------- |:------------------------------- |
| `id`         | string  | Team ID.                        |
| `team`       | object  | Basic team info (`id`, `name`). |
| `injury`     | array   | List of injury records.         |
| `updated_at` | integer | Last update timestamp.          |

#### Injury Record Fields (`results[].injury[]`)

| Field            | Type    | Description                                            |
|:---------------- |:------- |:------------------------------------------------------ |
| `player_id`      | string  | Player ID.                                             |
| `competition_id` | string  | Competition affected.                                  |
| `type`           | integer | 0: Unknown, 1: Injured, 2: Suspended, 3: Questionable. |
| `reason`         | string  | Cause of injury/absence.                               |
| `start_time`     | integer | Estimated start time of injury.                        |
| `end_time`       | integer | Estimated end time.                                    |
| `missed_matches` | integer | Number of matches missed.                              |

### Sync Recommendation

- **Incremental:** Recommended every 1 minute using the `time` parameter.
