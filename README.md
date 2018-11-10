# Echo VR API Documentation

Unofficial documentation for Echo VR's HTTP API.

## Summary

In short, if you execute Echo VR with the `-http` argument an http server will run during matches at `http://127.0.0.1:80/`. You can then query that server to access various information about the state of the match in progress.

This repository aims to document all the functionality of this API.

### GET /session

This returns a detailed representation of the current state of the match. The response is JSON, with an additional [null byte](https://en.wikipedia.org/wiki/Null_character) at the end that you may need to trim off before feeding it to your JSON parser.

Example response (formatted for readability):

```javascript
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

#### Details

The response is a JSON object, with the following properties:

##### `sessionid`
A 128-bit string-encoded GUID.

##### `game_clock_display`
A human-readable representation of the current game clock time.

##### `game_clock`
The current game clock time, in seconds.

##### `game_status`
The current game's status.

Possible values:

- `"pre_match"`
- `"round_start"`
- `"playing"`
- `"score"`
- `"round_over"`
- `"round_start"`
- `"post_match"`
- `"pre_sudden_death"`
- `"sudden_death"`
- `"post_sudden_death"`

##### `possession`
An arry of two integers representing which team currently possesses the disk.

TODO: Unclear exactly how this data is encoded.

##### `teams`

An array of objects containing data used to instantiate the game's two teams. (See below for details.)

##### `teams[].team`
A human-readable team name. Usually either "ORANGE TEAM" or "BLUE TEAM", but that's subject to change, and may be different during LAN tournaments (though I've not yet confirmed this).

##### `teams[].possession`
Indicates whether this team currently has posession of the disk.

##### `teams[].stats`
An object containing data used to instantiate the team's current stats.

##### `teams[].stats.possession_time`
Time in seconds that the subject posessed the disk.

##### `teams[].stats.points`
Points scored by the subject.

##### `teams[].stats.assists`
Number of goals assisted by the subject.

##### `teams[].stats.saves`
Number of opposing team goals prevented by the subject.

##### `teams[].stats.stuns`
Number of times the subject has stunned the opposing team.

##### `teams[].stats.goals`
Number of goals scored by the subject.

TODO: API always returns zero for teams?

##### `teams[].stats.passes`
Number of times the subject successfully completed a pass

TODO: API always returns zero for teams?

##### `teams[].stats.catches`
Number of times the subject succssfully caught a pass by a team member

##### `teams[].stats.steals`
Number of times the subject stole the disk from the opposing team

##### `teams[].stats.blocks`
Number of times the subject blocked a punch

TODO: API always returns zero for teams?

##### `teams[].stats.interceptions`
Number of times the subject intercepted a pass by the opposing team

TODO: API always returns zero for teams?

##### `teams[].stats.shots_taken`
Number of times the subject attempted a shot on goal

##### `teams[].players`
An array of objects containing data used to instantiate the team's players.

##### `teams[].players[].name`
The username of the player.

##### `teams[].players[].playerid`
A number representing ID of the player within the current game session.

##### `teams[].players[].userid`
A unique number identifying the player across all game sessions.

##### `teams[].players[].possession`
Indicates whether this player currently has posession of the disk.

##### `teams[].players[].position`
The current position of the player within the arena

##### `teams[].players[].stats`
An object containing data used to instantiate the player's current stats. See [`teams[].stats`](#teamsstats) for a list of available stats.
