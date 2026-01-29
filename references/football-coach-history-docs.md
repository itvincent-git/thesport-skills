---
name: football-coach-history-docs
description: Documentation for the Coach Coaching Resume API endpoint, tracking the career history, win/loss records, and performance metrics (PPM, Goals per match) of football coaches.
---

# Coach Coaching History API Documentation

## Endpoint: Coach coaching resume

**URL:** `GET /v1/football/coach/history/list`

### History Item Fields (`results[].history[]`)

| Field            | Type    | Description                              |
|:---------------- |:------- |:---------------------------------------- |
| `team`           | object  | Club/National team info.                 |
| `position`       | integer | 1: Head Coach, 2: Assistant, 3: Interim. |
| `joined`         | integer | Start date.                              |
| `contract_until` | integer | End date / Expiration.                   |
| `matches`        | integer | Total matches coached.                   |
| `win/draw/lose`  | integer | Match record.                            |
| `ppm`            | string  | Points Per Match.                        |
| `goal_ppt`       | string  | Goals scored per match.                  |
