# API Documentation

## For Witch Runner

## Endpoints

## 1. Health Check

### GET /

Checks if the server and database are running.

Response:

200 OK

```json
{
  "message": "Server is running and database is connected!"
}
```

503 Service Unavailable
```json
{
  "error": "Database not connected yet"
}
```
## 2. Fetch Leaderboard

### GET /players

Retrieves all players from the leaderboard, ranked by their points.

Response:

200 OK
```json
{
  "code": 0,
  "message": "Players Fetched Successfully",
  "players": [
    {
      "user_name": "John",
      "points": 120,
      "players_rank": 1
    }
  ]
}
```

401 Unauthorized
```json
{
  "code": 1,
  "message": "Could not fetch the data",
  "error": "error_message"
}
```

## 3. Add or Update Player

### POST /player

Adds a new player or updates their score if they already exist.

Request Body:
```json
{
  "user_name": "John",
  "sfID": "SF12345",
  "points": 150
}
```

Response:

200 OK (Score updated)
```json
{
  "code": 0,
  "message": "Score updated successfully"
}
```

```json
{
  "code": 0,
  "message": "Player added successfully"
}
```

```json
{
  "message": "Invalid input data"
}
```

## 4. Fetch Single Player

### GET /player

Fetches details of a single player by their sfID.

Query Parameters:

sfID (required): The unique ID of the player.

Response:

200 OK
```json
{
  "code": 0,
  "message": "Player's details fetched successfully",
  "player": {
    "user_name": "John",
    "points": 150
  }
}
```

400 Bad Request
```json
{
  "code": 1,
  "message": "sfID is required"
}
```

401 Unauthorized
```json
{
  "code": 5,
  "message": "Could not fetch the data",
  "error": "error_message"
}
```

## 5. Fetch Smash the Cans Leaderboard

### GET /cans/players

Retrieves the leaderboard for the "Smash the Cans" game, ranked by points_m.

Response:

200 OK
```json
{
  "code": 0,
  "message": "Players Fetched Successfully",
  "players": [
    {
      "user_name": "Jane",
      "points_m": 200,
      "players_rank": 1
    }
  ]
}
```

401 Unauthorized
```json
{
  "code": 1,
  "message": "Could not fetch the data",
  "error": "error_message"
}
```

## 6. Add or Update Smash the Cans Player

### POST /cans/player

Adds a new player or updates their score in the "Smash the Cans" leaderboard.

Request Body:
```json
{
  "user_name": "Jane",
  "sfID": "SF98765",
  "points_m": 250
}
```

Response:

200 OK (Score updated)
```json
{
  "code": 0,
  "message": "Score updated successfully"
}
```

200 OK (New player added)
```json
{
  "code": 0,
  "message": "Player added successfully"
}
```

400 Bad Request
```json
{
  "message": "Invalid input data"
}
```

## 7. Fetch Single Smash the Cans Player

### GET /cans/player

Fetches details of a single "Smash the Cans" player by their sfID.

Query Parameters:

sfID (required): The unique ID of the player.

Response:

200 OK
```json
{
  "code": 0,
  "message": "Player's details fetched successfully",
  "player": {
    "user_name": "Jane",
    "points_m": 250
  }
}
```

400 Bad Request
```json
{
  "code": 1,
  "message": "sfID is required"
}
```

401 Unauthorized
```json
{
  "code": 5,
  "message": "Could not fetch the data",
  "error": "error_message"
}
```