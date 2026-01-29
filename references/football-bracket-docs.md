---
name: football-bracket-docs
description: Documentation for the Football Tournament Bracket API endpoint, outlining the structure of knockout stages, groups, rounds, and match-up dependencies.
---

# Football Bracket API Documentation

## Endpoint: Bracket

**URL:** `GET /v1/football/bracket/season`

Returns the full knockout structure for a tournament season.

### Request Parameters

| Name   | Type   | Description              |
|:------ |:------ |:------------------------ |
| `uuid` | string | **Required**. Season ID. |

### Response Structure

Contains four main arrays: `brackets`, `groups`, `rounds`, and `match_ups`.

#### Match-Up Fields (`match_ups[]`)

Defines the connection between match nodes in the bracket.

| Field          | Type    | Description                                                                |
|:-------------- |:------- |:-------------------------------------------------------------------------- |
| `id`           | string  | Node ID.                                                                   |
| `type_id`      | integer | Rules (1: Single match, 5: Two matches away goal, 11: Two matches, etc.).  |
| `state_id`     | integer | State (1: NS, 6: Ongoing, 7: Home Won, 8: Away Won, 11: Waiting for Draw). |
| `parent_ids`   | array   | ID of the next round node (the winner moves here).                         |
| `children_ids` | array   | IDs of the nodes in the previous round that feed into this match.          |
| `match_ids`    | array   | IDs of the actual match(es) (found in Basic Match endpoints).              |
