---
name: football-odds-live-docs
description: Documentation for the Football Real-time Odds API endpoint, providing live odds data changes within the last 60 seconds for Asian, Euro, Size, and Corner markets.
---

# Football Real-time Odds API Documentation

## Endpoint: Real-time odds

**URL:** `GET /v1/football/odds/live`

Returns real-time changing odds data. Only returns odds data changed in the last 60 seconds.
Suggested request frequency: 3 seconds/time.

### Authentication

Required for all requests.

- **user** (string): API username.
- **secret** (string): API secret.

### Request Parameters

None beyond authentication.

### Response Structure

#### Result Fields (`results`)

A map where keys are **Company IDs** (see Status Codes -> Odds Company ID).

#### Company Odds Data (`results.{company_id}`)

Contains arrays for different odds types:

- **asia**: Asian Handicap
- **eu**: European 1x2
- **bs**: Over/Under (Size ball)
- **cr**: Corners

Each type is an array of odds records.

#### Odds Record Format (Array)

| Index | Type   | Description                           |
|:----- |:------ |:------------------------------------- |
| 0     | string | Match ID.                             |
| 1     | string | Odds Type ("asia", "eu", "bs", "cr"). |
| 2     | array  | **Odds Values** (see below).          |
| 3     | string | Score/Corner Ratio (Home-Away).       |

#### Odds Values Array (Index 2)

Varies by type but generally follows:

- **Index 0**: Change time (integer).
- **Index 1**: Match time (string).
- **Index 2**: Home Win / Over (float).
- **Index 3**: Draw / Handicap (float).
- **Index 4**: Away Win / Under (float).
- **Index 5**: Match Status (integer).
- **Index 6**: Closed? (0-No, 1-Yes).
