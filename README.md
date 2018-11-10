# Echo VR API Documentation

Unofficial documentation for Echo VR's HTTP API.

## Summary

In short, if you execute Echo VR with the `-http` argument an http server will run during matches at `http://127.0.0.1:80/`. You can then query that server to access various information about the state of the match in progress.

This repository aims to document all the functionality of this API.

### GET /session

This returns a detailed representation of the current state of the match. The response is JSON, with an additional [null byte](https://en.wikipedia.org/wiki/Null_character) at the end that you may need to trim off before feeding it to your JSON parser.

Example response (formatted for readability):

```
{
  "sessionid": "0BD7D136-E487-11E8-9F32-F2801F1B9FD1",
  "game_clock_display": "00:45.65",
  "game_clock": 45.659531,
  "game_status": "playing",
  "possession": [1, 0],
  "teams": [
    {
      "team": "BLUE TEAM",
      "possession": false,
      "stats": {
        "points": 9,
        "possession_time": 132.18958,
        "interceptions": 0,
        "blocks": 0,
        "steals": 0,
        "catches": 0,
        "passes": 0,
        "saves": 2,
        "goals": 0,
        "stuns": 29,
        "assists": 2,
        "shots_taken": 7
      },
      "players": [
        {
          "name": "Bob",
          "playerid": 0,
          "userid": 9221405949665979,
          "possession": false,
          "position": [
            -11.089001,
            -0.70900005,
            -9.6930008
          ],
          "stats": {
            "possession_time": 78.645569,
            "points": 5,
            "saves": 1,
            "goals": 0,
            "stuns": 14,
            "passes": 0,
            "catches": 0,
            "steals": 0,
            "blocks": 0,
            "interceptions": 0,
            "assists": 1,
            "shots_taken": 5
          }
        }
        /* ...other blue players here */
      ]
    },
    {
      "team": "ORANGE TEAM",
      "possession": true,
      "stats": {
        "points": 5,
        "possession_time": 80.32605,
        "interceptions": 0,
        "blocks": 0,
        "steals": 1,
        "catches": 0,
        "passes": 0,
        "saves": 2,
        "goals": 0,
        "stuns": 12,
        "assists": 1,
        "shots_taken": 5
      },
      "players": [
        /* ...orange players here; see blue players section for example */
      ]
    }
  ]
}
```
