---
name: football-match-incident-gif-docs
description: Documentation for the Football Match Incident Gif API endpoint, providing URLs to GIFs of key match events like goals and cards.
---

# Football Match Incident Gif API Documentation

## Endpoint: Match Incident Gif

**URL:** `GET /v1/football/match/highlight/detail`

Returns the URL of a GIF of incidents for a single match.
Includes: goal, yellow card, red card, card upgrade confirmed, penalty, penalty missed, own goal, penalty (penalty shoot-out), penalty missed (penalty shoot-out).

### Authentication

Required for all requests.

- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

| Name   | Type   | Required | Description |
|:------ |:------ |:-------- |:----------- |
| `uuid` | string | Yes      | Match ID.   |

### Response Structure

#### Result Fields (`results[]`)

| Field      | Type    | Description                                               |
|:---------- |:------- |:--------------------------------------------------------- |
| `type`     | integer | Incident type (see Status Codes -> Technical Statistics). |
| `time`     | integer | Time (minutes).                                           |
| `position` | integer | Team: 1-Home, 2-Away.                                     |
| `home`     | integer | Home team score/value.                                    |
| `away`     | integer | Away team score/value.                                    |
| `gif`      | string  | GIF URL.                                                  |
| `cover`    | string  | GIF cover image URL.                                      |

### Usage Recommendations

- **Frequency:** 120 times/min.
