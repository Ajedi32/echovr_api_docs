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
<pre>
{
    <a href="#client_name">"client_name"</a>: "Timemaster111",
    <a href="#sessionid">"sessionid"</a>: "1C32B3DA-F1F6-4B17-8BAE-FD1BC59C28BD",
    <a href="#sessionip">"sessionip"</a>: "184.154.39.222",
    <a href="#match_type">"match_type"</a>: "Echo_Arena",
    <a href="#map_name">"map_name"</a>: "mpl_arena_a",
    <a href="#game_clock">"game_clock"</a>: 215.09978,
    <a href="#game_clock_display">"game_clock_display"</a>: "03:35.09",
    <a href="#private_match">"private_match"</a>: false,
    <a href="#total_round_count">"total_round_count"</a>: 1,
    <a href="#blue_round_score">"blue_round_score"</a>: 0,
    <a href="#orange_round_score">"orange_round_score"</a>: 0,
    <a href="#blue_points">"blue_points"</a>: 2,
    <a href="#orange_points">"orange_points"</a>: 4,
    <a href="#tournament_match">"tournament_match"</a>: false,
    <a href="#blue_team_restart_request">"blue_team_restart_request"</a>: 0,
    <a href="#orange_team_restart_request">"orange_team_restart_request"</a>: 0,
    <a href="#right_shoulder_pressed">"right_shoulder_pressed"</a>: 0.0,
    <a href="#right_shoulder_pressed2">"right_shoulder_pressed2"</a>: 0.0,
    <a href="#left_shoulder_pressed">"left_shoulder_pressed"</a>: 0.0,
    <a href="#left_shoulder_pressed2">"left_shoulder_pressed2"</a>: 0.0,
    <a href="#game_status">"game_status"</a>: "score",
    <a href="#pause">"pause"</a>: {
        <a href="#pausepaused_state">"paused_state"</a>: "unpaused",
        <a href="#pauseunpaused_team">"unpaused_team"</a>: "none",
        <a href="#pausepaused_requested_team">"paused_requested_team"</a>: "none",
        <a href="#pauseunpaused_timer">"unpaused_timer"</a>: 0.0,
        <a href="#pausepaused_timer">"paused_timer"</a>: 0.0
    },
    <a href="#possession">"possession"</a>: [
        1,
        0
    ],
    <a href="#last_throw">"last_throw"</a>: {
        <a href="#last_throwarm_speed">"arm_speed"</a>: 0.0,
        <a href="#last_throwtotal_speed">"total_speed"</a>: 0.0,
        <a href="#last_throwoff_axis_spin_deg">"off_axis_spin_deg"</a>: 0.0,
        <a href="#last_throwwrist_throw_penalty">"wrist_throw_penalty"</a>: 0.0,
        <a href="#last_throwrot_per_sec">"rot_per_sec"</a>: 0.0,
        <a href="#last_throwpot_speed_from_rot">"pot_speed_from_rot"</a>: 0.0,
        <a href="#last_throwspeed_from_arm">"speed_from_arm"</a>: 0.0,
        <a href="#last_throwspeed_from_movement">"speed_from_movement"</a>: 0.0,
        <a href="#last_throwspeed_from_wrist">"speed_from_wrist"</a>: 0.0,
        <a href="#last_throwwrist_align_to_throw_deg">"wrist_align_to_throw_deg"</a>: 0.0,
        <a href="#last_throwthrow_align_to_movement_deg">"throw_align_to_movement_deg"</a>: 0.0,
        <a href="#last_throwoff_axis_penalty">"off_axis_penalty"</a>: 0.0,
        <a href="#last_throwthrow_move_penalty">"throw_move_penalty"</a>: 0.0
    },
    <a href="#last_score">"last_score"</a>: {
        <a href="#last_scoredisc_speed">"disc_speed"</a>: 0.0,
        <a href="#last_scoreteam">"team"</a>: "orange",
        <a href="#last_scoregoal_type">"goal_type"</a>: "SLAM DUNK",
        <a href="#last_scorepoint_amount">"point_amount"</a>: 2,
        <a href="#last_scoredistance_thrown">"distance_thrown"</a>: 0.40054435,
        <a href="#last_scoreperson_scored">"person_scored"</a>: "Bob",
        <a href="#last_scoreassist_scored">"assist_scored"</a>: "[INVALID]"
    },
    <a href="#disc">"disc"</a>: {
        <a href="#discposition">"position"</a>: [
            0.0,
            0.0,
            0.0
        ],
        <a href="#discforward">"forward"</a>: [
            0.0,
            0.0,
            1.0
        ],
        <a href="#discleft">"left"</a>: [
            1.0,
            0.0,
            0.0
        ],
        <a href="#discup">"up"</a>: [
            0.0,
            1.0,
            0.0
        ],
        <a href="#discvelocity">"velocity"</a>: [
            0.0,
            0.0,
            0.0
        ],
        <a href="#discbounce_count">"bounce_count"</a>: 0
    },
    <a href="#player">"player"</a>: {
        <a href="#playervr_left">"vr_left"</a>: [
            0.78700006,
            0.072000004,
            0.61300004
        ],
        <a href="#playervr_position">"vr_position"</a>: [
            -3.9650002,
            2.2310002,
            -34.506001
        ],
        <a href="#playervr_forward">"vr_forward"</a>: [
            -0.61700004,
            0.091000006,
            0.78200006
        ],
        <a href="#playervr_up">"vr_up"</a>: [
            0.0,
            0.99300003,
            -0.116
        ]
    },
    <a href="#teams">"teams"</a>: [
        {
            <a href="#teamsteam">"team"</a>: "BLUE TEAM",
            <a href="#teamspossession">"possession"</a>: false,
            <a href="#teamsstats">"stats"</a>: {
                <a href="#teamsstatspoints">"points"</a>: 2,
                <a href="#teamsstatspossession_time">"possession_time"</a>: 32.055771,
                <a href="#teamsstatsinterceptions">"interceptions"</a>: 0,
                <a href="#teamsstatsblocks">"blocks"</a>: 0,
                <a href="#teamsstatssteals">"steals"</a>: 1,
                <a href="#teamsstatscatches">"catches"</a>: 0,
                <a href="#teamsstatspasses">"passes"</a>: 0,
                <a href="#teamsstatssaves">"saves"</a>: 3,
                <a href="#teamsstatsgoals">"goals"</a>: 0,
                <a href="#teamsstatsstuns">"stuns"</a>: 6,
                <a href="#teamsstatsassists">"assists"</a>: 1,
                <a href="#teamsstatsshots_taken">"shots_taken"</a>: 0
                },
            <a href="#teamsplayers">"players"</a>: [
                {
                    <a href="#teamsplayersname">"name"</a>: "Timemaster111",
                    <a href="#teamsplayersplayerid">"playerid"</a>: 0,
                    <a href="#teamsplayersuserid">"userid"</a>: 3561909181390317,
                    <a href="#teamsplayersnumber">"number"</a>: 5,
                    <a href="#teamsplayerslevel">"level"</a>: 50,
                    <a href="#teamsplayersping">"ping"</a>: 48,
                    <a href="#teamsplayersstunned">"stunned"</a>: false,
                    <a href="#teamsplayersinvulnerable">"invulnerable"</a>: false,
                    <a href="#teamsplayerspossession">"possession"</a>: false,
                    <a href="#teamsplayersholding_left">"holding_left"</a>: "none",
                    <a href="#teamsplayersholding_right">"holding_right"</a>: "none",
                    <a href="#teamsplayersblocking">"blocking"</a>: false,
                    <a href="#teamsplayersstats">"stats"</a>: {
                        <a href="#teamsstatspossession_time">"possession_time"</a>: 8.9302616,
                        <a href="#teamsstatspoints">"points"</a>: 0,
                        <a href="#teamsstatssaves">"saves"</a>: 1,
                        <a href="#teamsstatsgoals">"goals"</a>: 0,
                        <a href="#teamsstatsstuns">"stuns"</a>: 3,
                        <a href="#teamsstatspasses">"passes"</a>: 0,
                        <a href="#teamsstatscatches">"catches"</a>: 0,
                        <a href="#teamsstatssteals">"steals"</a>: 0,
                        <a href="#teamsstatsblocks">"blocks"</a>: 0,
                        <a href="#teamsstatsinterceptions">"interceptions"</a>: 0,
                        <a href="#teamsstatsassists">"assists"</a>: 0,
                        <a href="#teamsstatsshots_taken">"shots_taken"</a>: 0
                    },
                    <a href="#teamsplayersvelocity">"velocity"</a>: [
                        0.48200002,
                        0.83300006,
                        -2.3240001
                    ],
                    <a href="#teamsplayershead">"head"</a>: {
                        <a href="#teamsplayersheadposition">"position"</a>: [
                            -2.1360002,
                            2.098,
                            -33.876003
                        ],
                        <a href="#teamsplayersheadforward">"forward"</a>: [
                            0.14600001,
                            -0.36400002,
                            0.92000002
                        ],
                        <a href="#teamsplayersheadleft">"left"</a>: [
                            0.98400003,
                            -0.045000002,
                            -0.17400001
                        ],
                        <a href="#teamsplayershead"></a>"up": [
                            0.105,
                            0.93000007,
                            0.35200003
                        ]
                    },
                    <a href="#teamsplayersbody">"body"</a>: {
                        <a href="#teamsplayersbodyposition">"position"</a>: [
                            -2.1360002,
                            2.098,
                            -33.876003
                        ],
                        <a href="#teamsplayersbodyforward">"forward"</a>: [
                            0.296,
                            0.001,
                            0.95500004
                        ],
                        <a href="#teamsplayersbodyleft">"left"</a>: [
                            0.95500004,
                            -0.0020000001,
                            -0.296
                        ],
                        <a href="#teamsplayersbodyup">"up"</a>: [
                            0.001,
                            1.0,
                            -0.001
                        ]
                    },
                    <a href="#teamsplayersrhand">"rhand"</a>: {
                        <a href="#teamsplayersrhandpos">"pos"</a>: [
                            -2.3390002,
                            1.8030001,
                            -33.733002
                        ],
                        <a href="#teamsplayersrhandforward">"forward"</a>: [
                            -0.259,
                            0.74000001,
                            0.62
                        ],
                        <a href="#teamsplayersrhandleft">"left"</a>: [
                            0.80900002,
                            -0.18400002,
                            0.55800003
                        ],
                        <a href="#teamsplayersrhandup">"up"</a>: [
                            0.52700001,
                            0.64700001,
                            -0.55200005
                        ]
                    },
                    <a href="#teamsplayerslhand">"lhand"</a>: {
                        <a href="#teamsplayerslhandpos">"pos": [
                            -2.0700002,
                            1.8610001,
                            -33.788002
                        ],
                        <a href="#teamsplayerslhandforward">"forward"</a>: [
                            -0.44800001,
                            0.73100001,
                            0.51500005
                        ],
                        <a href="#teamsplayerslhandleft">"left"</a>: [
                            0.89200002,
                            0.32200003,
                            0.317
                        ],
                        <a href="#teamsplayerslhandup">"up"</a>: [
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
            <a href="#teams">"team"</a>: "ORANGE TEAM",
            /* ... same as blue team ... */
        },
        {
            <a href="#teams">"team"</a>: "SPECTATORS",
            /* ... same as blue team ... */
        }
    ]
}
        
</pre>
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
* `"Echo_Combat"`
* `"Echo_Combat_Private"`
* `"Social_2.0"`
* `"INVALID GAMETYPE"`
* Combat

#### `map_name`
Name of the map being played.

Possible values:
* `"mpl_arena_a"` - Standard Echo Arena map
* `"mpl_lobby_b2"` - Lobby
* * `mpl_combat_dyson` - Combat maps
* `mpl_combat_combustion`
* `mpl_combat_fission`
* `mpl_combat_gauss`
* `"INVALID LEVEL"`

#### `game_clock`
Current game time in seconds.

#### `game_clock_display`
Current game time as shown in game.

#### `private_match`
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
Touch controller input

#### `right_shoulder_pressed2`
Touch controller input

#### `left_shoulder_pressed`
Touch controller input

#### `left_shoulder_pressed2`
Touch controller input

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
* `"unpaused"`
* `"unpausing"`
* `"paused"`
* `"paused_requested"`

#### `pause.unpaused_team`
Team that unpaused the game.

Possible values:
* `"orange"`
* `"blue"`
* `"none"`

#### `pause.paused_requested_team`
Team that pressed the pause button.

Possible values:
* `"orange"`
* `"blue"`
* `"none"`

#### `pause.unpaused_timer`
Time until gameplay will resume.

#### `pause.paused_timer`
Time since game was paused.

#### `possession`
Team and player currently in possession of the disc.

`possession[0]` is the team in possession and `possession[1]` is the player in that team. 

#### `last_throw`
Info about the last throw made in game by the client user.

#### `last_throw.arm_speed`
Speed of the arm during the last throw.

#### `last_throw.total_speed`
Combination of all speed factors that went into the disc.

#### `last_throw.off_axis_spin_deg`


#### `last_throw.wrist_throw_penalty`

#### `last_throw.rot_per_sec`

#### `last_throw.pot_speed_from_rot`

#### `last_throw.speed_from_arm`

#### `last_throw.speed_from_movement`

#### `last_throw.speed_from_wrist`

#### `last_throw.wrist_align_to_throw_deg`

#### `last_throw.throw_align_to_movement_deg`

#### `last_throw.off_axis_penalty`

#### `last_throw.throw_move_penalty`

#### `last_score`
Last score made in the game.

#### `last_score.disc_speed`
Speed of the disc when it went into the goal.

#### `last_score.team`
Team that scored the last goal.

Possible values (TBC):
* `"blue"`
* `"orange"`

#### `last_score.goal_type`
A human-readable explanation of the type of goal scored. This is "[NO GOAL]" by default when no goal has been scored.

Possible values:

* `"[NO GOAL]"`
* `"SLAM DUNK"`
* `"INSIDE SHOT"`
* `"LONG SHOT"`
* `"BOUNCE SHOT"`
* `"LONG BOUNCE SHOT"`

#### `last_score.point_amount`
The number of points scored (2 or 3). This is 0 by default when no goal has been scored.

#### `last_score.distance_thrown`
The distance the goal was scored from. This is 0 by default when no goal has been scored.

#### `last_score.person_scored`
The username of the player who scored the goal. This is `"[INVALID]"` by default when no goal has been scored since you first joined the match.

#### `last_score.assist_scored`
The username of the player who assisted the goal. This is `"[INVALID]"` by default when no goal has been scored since you first joined the match, or when a goal was scored, but no player was credited with the assist.

#### `disc`
An object representing the current state of the disk.

#### `disc.position`
An array representing the disk's position within the arena.

#### `disc.forward`
The direction that the disc is facing.

#### `disc.left`
The direction that the left side of the disc is facing.

#### `disc.up`
The direction that the top of the disc is facing.

#### `disc.velocity`
An array representing the disk's velocity.

#### `disc.bounce_count`
The number of times the disk has bounced. (TODO: Since the last time someone grabbed it? Do headbutts count as bounces?)

#### `player`
An object representing the current state of the local VR player. This is used for positions of the player within their playspace.

#### `player.vr_left`
The direction that the left side of the player's head is facing within their playspace.

#### `player.vr_position`
An array representing the player's position within their playspace.

#### `player.vr_forward`
The direction that the player's head is facing within their playspace.

#### `player.vr_up`
The direction that the top side of the player's head is facing within their playspace.

#### `teams`
An array of objects containing data used to instantiate the game's two teams. The first element in the array is always the blue team, while the second is always the orange team and the third is always the spectators.

#### `teams[].team`
A human-readable team name. Usually either "ORANGE TEAM" or "BLUE TEAM", but if all the players on a team have the same team name (set by pressing F11 while in a match or the lobby) it will be that instead.

#### `teams[].possession`
Indicated whethe this team currently has possession of the disk.

#### `teams[].stats`
An object containing data used to instantiate the team's current stats.

#### `teams[].stats.points`
Points scored by the subject.

#### `teams[].stats.possession_time`
Time in seconds that the subject possessed the disk.

#### `teams[].stats.interceptions`
Number of times the subject intercepted a pass by the opposing team

API always returns zero for teams

#### `teams[].stats.blocks`
Number of times the subject blocked a punch

API always returns zero for teams

#### `teams[].stats.steals`
Number of times the subject stole the disk from the opposing team

#### `teams[].stats.catches`
Number of times the subject successfully caught a pass by a team member

#### `teams[].stats.passes`
Number of times the subject successfully completed a pass

API always returns zero for teams

#### `teams[].stats.saves`
Number of opposing team goals prevented by the subject.

#### `teams[].stats.goals`
Number of goals scored by the subject.

API always returns zero for teams

#### `teams[].stats.stuns`
Number of times the subject has stunned the opposing team.

#### `teams[].stats.assists`
Number of goals assisted by the subject.

#### `teams[].stats.shots_taken`
Number of times the subject attempted a shot on goal

#### `teams[].players`
An array of objects containing data used to instantiate the team's players.

#### `teams[].players[].name`
The username of the player.

#### `teams[].players[].playerid`
A number representing ID of the player within the current game session.

#### `teams[].players[].userid`
A unique number identifying the player across all game sessions.

#### `teams[].players[].number`
The number a player chose for themselves in the customization room.

Defaults to `0`

#### `teams[].players[].level`
A number (1-50) representing the player's experience "level". New accounts start as level 1, and will usually reach level 50 after a few hundred games in public matchmaking.

Note that there a rare bug where this number may be 0 in the UI in some cases; it's possible this bug may also affect the API (though this has yet to be verified).

#### `teams[].players[].ping`
Current ping (network latency to server) of this player.

#### `teams[].players[].stunned`
Whether the player is currently stunned.

#### `teams[].players[].invulnerable`
Whether or not the player is currently immune to stuns. Players will be in this state for 3 seconds after they are stunned.

#### `teams[].players[].possession`
Indicates whether this player currently has possession of the disk.

#### `teams[].players[].holding_left`
The item or object the player is holding in their left hand.

Possible values:
* `"disc"`
* player id (`"0"`, `"1"`)
* `"geo"`

#### `teams[].players[].holding_right`
The item or object the player is holding in their right hand.

Possible values:
* `"disc"`
* player id (`"0"`, `"1"`)
* `"geo"`

#### `teams[].players[].blocking`
Whether the player is currently blocking (and will therefore deflect stuns).

#### `teams[].players[].stats`
An object containing data used to instantiate the player's current stats. See [`teams[].stats`](#teamsstats) for a list of available stats.

#### `teams[].players[].velocity`
The current velocity (speed and direction of movement) of the player.

#### `teams[].players[].head`
An object containing position and rotation of the head of the player

#### `teams[].players[].head.position`
The position of the player's head in the arena.

#### `teams[].players[].head.forward`
The direction that the player's head is facing.

#### `teams[].players[].head.left`
The direction that the left side of the player's head is facing.

#### `teams[].players[].head.up`
The direction that the top side of the player's head is facing.

#### `teams[].players[].body`
An object containing position and rotation of the body of the player

#### `teams[].players[].body.position`
The position of the player's body in the arena.

#### `teams[].players[].body.forward`
The direction that the player's body is facing.

#### `teams[].players[].body.left`
The direction that the left side of the player's body is facing.

#### `teams[].players[].body.up`
The direction that the top side of the player's body is facing.

#### `teams[].players[].rhand`
An object containing position and rotation data for the right hand.

#### `teams[].players[].rhand.pos`
The position of the player's right hand within the arena.

#### `teams[].players[].rhand.forward`
The direction that the player's right hand is facing.

#### `teams[].players[].rhand.left`
The direction that the left side of the player's right hand is facing.

#### `teams[].players[].rhand.up`
The direction that the top side of the player's right hand is facing.

#### `teams[].players[].lhand`
An object containing position and rotation data for the left hand.

#### `teams[].players[].lhand.pos`
The position of the player's left hand within the arena.

#### `teams[].players[].lhand.forward`
The direction that the player's left hand is facing.

#### `teams[].players[].lhand.left`
The direction that the left side of the player's left hand is facing.

#### `teams[].players[].lhand.up`
The direction that the top side of the player's left hand is facing.

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
Requests list for additions to the API
* sample request

### Issues
Issues list for the API
* sample issue

### Quirks
List of things that don't do quite what you expect but still work
* something like team name isn't always orange or blue

### TODO
Things that need doing in the wiki
* shoulder_pressed values and description
* restart request is int?
* fill in last throw values
* last_score.team value confirmation
* add in stuff like `[position](#position-1)`
* Keep updating
