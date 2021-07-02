# Echo VR API Documentation

Unofficial documentation for Echo VR's HTTP API.

## Summary

Echo Arena has an HTTP API available for querying current game state. This API
listens locally on port 6721 (`http://127.0.0.1:6721/session`). This API now requires a setting to be toggled on.

Note that if any other service is alredy bound to this (TCP) port, which often
happens on Windows, Echo will not be able to bind to it. To kill any services
using it, run `net stop HTTP` in an administrator command prompt.

This repository aims to document all the functionality of this API.

## API Endpoints

### GET /session

This returns a detailed representation of the current state of the match. The response is a JSON string, which can be parsed with any standard JSON parser.

Example response (formatted for readability):
```
{
    "client_name": "Timemaster111",
    "sessionid": "1C32B3DA-F1F6-4B17-8BAE-FD1BC59C28BD",
    "sessionip": "184.154.39.222",
    "match_type": "Echo_Arena",
    "map_name": "mpl_arena_a",
    "game_clock": 215.09978,
    "game_clock_display": "03:35.09",
    "private_match": false,
    "total_round_count": 1,
    "blue_round_score": 0,
    "orange_round_score": 0,
    "blue_points": 2,
    "orange_points": 4,
    "tournament_match": false,
    "blue_team_restart_request": 0,
    "orange_team_restart_request": 0,
    "right_shoulder_pressed": 0.0,
    "right_shoulder_pressed2": 0.0,
    "left_shoulder_pressed": 0.0,
    "left_shoulder_pressed2": 0.0,
    "game_status": "score",
    "pause": {
        "paused_state": "unpaused",
        "unpaused_team": "none",
        "paused_requested_team": "none",
        "unpaused_timer": 0.0,
        "paused_timer": 0.0
    },
    "possession": [
        1,
        0
    ],
    "last_throw": {
        "arm_speed": 0.0,
        "total_speed": 0.0,
        "off_axis_spin_deg": 0.0,
        "wrist_throw_penalty": 0.0,
        "rot_per_sec": 0.0,
        "pot_speed_from_rot": 0.0,
        "speed_from_arm": 0.0,
        "speed_from_movement": 0.0,
        "speed_from_wrist": 0.0,
        "wrist_align_to_throw_deg": 0.0,
        "throw_align_to_movement_deg": 0.0,
        "off_axis_penalty": 0.0,
        "throw_move_penalty": 0.0
    },
    "last_score": {
        "disc_speed": 0.0,
        "team": "orange",
        "goal_type": "SLAM DUNK",
        "point_amount": 2,
        "distance_thrown": 0.40054435,
        "person_scored": "Bob",
        "assist_scored": "[INVALID]"
    },
    "disc": {
        "position": [
            0.0,
            0.0,
            0.0
        ],
        "forward": [
            0.0,
            0.0,
            1.0
        ],
        "left": [
            1.0,
            0.0,
            0.0
        ],
        "up": [
            0.0,
            1.0,
            0.0
        ],
        "velocity": [
            0.0,
            0.0,
            0.0
        ],
        "bounce_count": 0
    },
    "player": {
        "vr_left": [
            0.78700006,
            0.072000004,
            0.61300004
        ],
        "vr_position": [
            -3.9650002,
            2.2310002,
            -34.506001
        ],
        "vr_forward": [
            -0.61700004,
            0.091000006,
            0.78200006
        ],
        "vr_up": [
            0.0,
            0.99300003,
            -0.116
        ]
    },
    "teams": [
        {
            "team": "BLUE TEAM",
            "possession": false,
            "stats": {
                "points": 2,
                "possession_time": 32.055771,
                "interceptions": 0,
                "blocks": 0,
                "steals": 1,
                "catches": 0,
                "passes": 0,
                "saves": 3,
                "goals": 0,
                "stuns": 6,
                "assists": 1,
                "shots_taken": 0
                },
            "players": [
                {
                    "name": "Timemaster111",
                    "playerid": 0,
                    "userid": 3561909181390317,
                    "number": 5,
                    "level": 50,
                    "ping": 48,
                    "stunned": false,
                    "invulnerable": false,
                    "possession": false,
                    "holding_left": "none",
                    "holding_right": "none",
                    "blocking": false,
                    "stats": {
                        "possession_time": 8.9302616,
                        "points": 0,
                        "saves": 1,
                        "goals": 0,
                        "stuns": 3,
                        "passes": 0,
                        "catches": 0,
                        "steals": 0,
                        "blocks": 0,
                        "interceptions": 0,
                        "assists": 0,
                        "shots_taken": 0
                    },
                    "velocity": [
                        0.48200002,
                        0.83300006,
                        -2.3240001
                    ],
                    "head": {
                        "position": [
                            -2.1360002,
                            2.098,
                            -33.876003
                        ],
                        "forward": [
                            0.14600001,
                            -0.36400002,
                            0.92000002
                        ],
                        "left": [
                            0.98400003,
                            -0.045000002,
                            -0.17400001
                        ],
                        "up": [
                            0.105,
                            0.93000007,
                            0.35200003
                        ]
                    },
                    "body": {
                        "position": [
                            -2.1360002,
                            2.098,
                            -33.876003
                        ],
                        "forward": [
                            0.296,
                            0.001,
                            0.95500004
                        ],
                        "left": [
                            0.95500004,
                            -0.0020000001,
                            -0.296
                        ],
                        "up": [
                            0.001,
                            1.0,
                            -0.001
                        ]
                    },
                    "rhand": {
                        "pos": [
                            -2.3390002,
                            1.8030001,
                            -33.733002
                        ],
                        "forward": [
                            -0.259,
                            0.74000001,
                            0.62
                        ],
                        "left": [
                            0.80900002,
                            -0.18400002,
                            0.55800003
                        ],
                        "up": [
                            0.52700001,
                            0.64700001,
                            -0.55200005
                        ]
                    },
                    "lhand": {
                        "pos": [
                            -2.0700002,
                            1.8610001,
                            -33.788002
                        ],
                        "forward": [
                            -0.44800001,
                            0.73100001,
                            0.51500005
                        ],
                        "left": [
                            0.89200002,
                            0.32200003,
                            0.317
                        ],
                        "up": [
                            0.066,
                            0.60100001,
                            -0.79600006
                        ]
                    },
                },
                {
                /* ... more players ... */
                }
            ]
        },
        {
            "team": "ORANGE TEAM",
            /* ... same as blue team ... */
        },
        {
            "team": "SPECTATORS",
            /* ... same as blue team ... */
        }
    ]
}
        
```
#### Properties

The response is a JSON object, with the following properties:

#### `client_name`
The username of the signed-in user.

#### `sessionid`
A 128-bit string-encoded GUID of the session.

#### `sessionip`
IP address to the current server

#### `match_type`
Represents the type of match being played.

Possible values:

* `"Echo_Arena_Private"`
* `"Echo_Arena"`
* `"Social_2.0"`
* `"INVALID GAMETYPE"`
* Combat

#### `map_name`
Name of the map being played.

Possible values:
* `"mpl_arena_a"` - Standard Echo Arena map
* `"mpl_lobby_b2"` - Lobby
* `"INVALID LEVEL"`
* Combat maps

#### `game_clock`
Current game time in seconds.

#### `game_clock_display`
Current game time as shown in game.

#### `private match`
Whether the current session is a private lobby.

#### `total_round_count`
Total number of rounds to be played in the match.

#### `blue_round_score`
Total number of rounds that blue has won.

#### `orange_round_score`
Total number of rounds that orange has won.

#### `blue_points`
Number of points blue has scored this round.

#### `orange_points`
Number of points orange has scored this round.

#### `tournament_match`
TBC

#### `blue_team_restart_request`
Whether or not the blue team is requesting a restart.

#### `orange_team_restart_request`
Whether or not the orange team is requesting a restart.

#### `right_shoulder_pressed`
No clue

#### `right_shoulder_pressed2`
No clue

#### `left_shoulder_pressed`
No clue

#### `left_shoulder_pressed2`
No clue

#### `game_status`
The current game's status.

Possible values:

* `"pre_match"`
* `"round_start"`
* `"playing"`
* `"score"`
* `"round_over"`
* `"round_start"`
* `"post_match"`
* `"pre_sudden_death"`
* `"sudden_death"`
* `"post_sudden_death"`

#### `pause`
Details about whether the game is currently paused.

#### `pause.paused_state`
Current pause state of the match.

Possible values:
* `unpaused`
* `unpausing`
* `paused`
* `paused_requested`

#### `pause.unpaused_team`
TBC

Possible values:
* `orange`
* `blue`
* `none`

#### `pause.paused_requested_team`
Team that pressed the pause button.

Possible values:
* `orange`
* `blue`
* `none`

#### `pause.unpaused_timer`
Time until gameplay will resume.

#### `pause.paused_timer`
Time since game was paused.

#### `possession`
Team and player currently in possession of the disc. subvalues TBC

#### `last_throw`
Info about the last throw made in game.

#### `last_throw.arm_speed`
Speed of the arm during the last throw.


## Concepts
Throughout the API there are a number of concepts that get reused in multiple places. These concepts are documented in this section.

### Vectors
Position, direction, and velocity are represented within the API as an array of [3D vector coordinates in Cartesian space](https://en.wikipedia.org/wiki/Euclidean_vector#In_Cartesian_space). That's a fancy way of saying the array contains three numbers, each representing a distance/speed in either the left-right (`x`), up-down (`y`), or forward-back (`z`) directions. These directions are arranged as `[x, y, z]` in the arrays returned by the API.

Distance is measured in meters, and speed in meters per second. So, for example, a vector coordinate `[0, 1, 0]` could represent either a distance of 1 meter in the "up" direction, or a speed of 1 meter/second in the "up" direction.

For vectors that contain a mix of several directions, you can calculate the total distance or speed (r) using a 3-dimensional version of the [Pythagorean theorem](https://en.wikipedia.org/wiki/Pythagorean_theorem): r<sup>2</sup> = x<sup>2</sup> + y<sup>2</sup> + z<sup>2</sup>

In Echo Arena, distances are measured from the center of the Arena, where the disk spawns (at `[0, 0, 0]`). Positive `z` is in the direction of the orange side of the arena, negative `z` is in the direction of the blue side of the arena. If you're on the blue side of the arena facing the orange team's goal, positive `x` would be towards your left, and negative `x` would be to your right (with left/right reversed for a player on the orange team's side of the arena facing the blue team's side). Positive `y` is "up" (relative to a player's orientation when they spawn) and negative `y` is "down".

So, for example, a player located at [10.0, -5.0, -15.0] would be, from the perspective of someone sitting on the blue team's goal facing the orange team's goal, 10 meters to the left of the center of the arena, on the blue team's side, near the floor.

The Arena is 80m long (counting from orange to blue launch tube exits), 30m wide (counting from the widest point of the side walls) and 20m tall (counting from the tallest part of the arena, in the trenches).

### Possession
The API defines "possession" a little more broadly than you might expect (depending on what other sports you may be familiar with that use this term). Not only do players/teams that are currently holding the disk have possession, but teams also maintain possession for 7 seconds after releasing the disk as well, unless the disk is recovered by the opposing team. If the disk is glowing with the color of a specific team, the game considers that team as having "possession".

### Session
A "session" is what users typically think of as the "server" you're playing on. When you join a new match, a new session is created, and the session will remain active until all players leave. Sessions IDs are unique, and have no correspondence to the actual, physical or virtual server hardware that's hosting the game.

## Community parts
This section is for community suggestions and common issues

### Requests
* sample request

### Issues
* sample issue

### Quirks
* something like team name isn't always orange or blue

### TODO
* Combat
* shoulder_pressed
* restart request is int?
* check last_throw is local or not
* find values of possession
* pause values
* Keep updating
