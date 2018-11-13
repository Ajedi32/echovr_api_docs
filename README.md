# Echo VR API Documentation

Unofficial documentation for Echo VR's HTTP API.

## Summary

In short, if you execute Echo VR with the `-http` argument an http server will run during matches at `http://127.0.0.1:80/`. You can then query that server to access various information about the state of the match in progress.

This repository aims to document all the functionality of this API.

## API Endpoints

### GET /session

This returns a detailed representation of the current state of the match. The response is JSON, with an additional [null byte](https://en.wikipedia.org/wiki/Null_character) at the end that you may need to trim off before feeding it to your JSON parser.

Example response (formatted for readability):

<pre>
{
  <a href="#client_name">"client_name"</a>: "ajedi32",
  <a href="#sessionid">"sessionid"</a>: "0BD7D136-E487-11E8-9F32-F2801F1B9FD1",
  <a href="#match_type">"match_type"</a>: "Echo_Arena_Private",
  <a href="#map_name">"map_name"</a>: "mpl_arena_a",
  <a href="#private_match">"private_match"</a>: true,
  <a href="#tournament_match">"tournament_match"</a>: false,
  <a href="#game_clock_display">"game_clock_display"</a>: "00:45.65",
  <a href="#game_clock">"game_clock"</a>: 45.659531,
  <a href="#game_status">"game_status"</a>: "playing",
  <a href="#possession">"possession"</a>: [1, 0],
  <a href="#blue_points">"blue_points"</a>: 9,
  <a href="#orange_points">"orange_points"</a>: 5,
  <a href="#disc">"disc"</a>: {
    <a href="#discposition">"position"</a>: [0, 0, 0],
    <a href="#discvelocity">"velocity"</a>: [0, 0, 0],
    <a href="#discbounce_count">"bounce_count"</a>: 0
  },
  // TODO: Make this consistent with the other stats in the example.
  <a href="#last_score">"last_score"</a>: {
    <a href="#last_scoredisc_speed">"disc_speed"</a>: 0,
    <a href="#last_scoreteam">"team"</a>: "blue",
    <a href="#last_scoregoal_type">"goal_type"</a>: "[NO GOAL]",
    <a href="#last_scorepoint_amount">"point_amount"</a>: 0,
    <a href="#last_scoredistance_thrown">"distance_thrown"</a>: 0,
    <a href="#last_scoreperson_scored">"person_scored"</a>: "[INVALID]",
    <a href="#last_scoreassist_scored">"assist_scored"</a>: "[INVALID]"
  },
  <a href="#teams">"teams"</a>: [
    {
      <a href="#teamsteam">"team"</a>: "BLUE TEAM",
      <a href="#teamspossession">"possession"</a>: false,
      <a href="#teamsstats">"stats"</a>: {
        <a href="#teamsstatspoints">"points"</a>: 9,
        <a href="#teamsstatspossession_time">"possession_time"</a>: 132.18958,
        <a href="#teamsstatsinterceptions">"interceptions"</a>: 0,
        <a href="#teamsstatsblocks">"blocks"</a>: 0,
        <a href="#teamsstatssteals">"steals"</a>: 0,
        <a href="#teamsstatscatches">"catches"</a>: 0,
        <a href="#teamsstatspasses">"passes"</a>: 0,
        <a href="#teamsstatssaves">"saves"</a>: 2,
        <a href="#teamsstatsgoals">"goals"</a>: 0,
        <a href="#teamsstatsstuns">"stuns"</a>: 29,
        <a href="#teamsstatsassists">"assists"</a>: 2,
        <a href="#teamsstatsshots_taken">"shots_taken"</a>: 7
      },
      <a href="teamsplayers">"players"</a>: [
        {
          <a href="#teamsplayersname">"name"</a>: "Bob",
          <a href="#teamsplayersplayerid">"playerid"</a>: 0,
          <a href="#teamsplayersuserid">"userid"</a>: 9221405949665979,
          <a href="#teamsplayerslevel">"level"</a>: 16,
          <a href="#teamsplayersnumber">"number"</a>: 88,
          <a href="#teamsplayerspossession">"possession"</a>: false,
          <a href="#teamsplayersstunned">"stunned"</a>: false,
          <a href="#teamsplayersblocking">"blocking"</a>: false,
          <a href="#teamsplayersinvulnerable">"invulnerable"</a>: false,
          <a href="#teamsplayersposition">"position"</a>: [0.001, -2.2710001, 78.183006],
          <a href="#teamsplayersvelocity">"velocity"</a>: [0, 0, 0],
          <a href="#teamsplayerslhand">"lhand"</a>: [0.13800001, -2.3000002, 78.131004],
          <a href="#teamsplayersrhand">"rhand"</a>: [0.21600001, -2.3150001, 78.168007],
          <a href="#teamsplayersforward">"forward"</a>: [0, 0.25800002, -0.96600002],
          <a href="#teamsplayersleft">"left"</a>: [-1, 0.014, 0.0040000002],
          <a href="#teamsplayersup">"up"</a>: [0.014, 0.96600002, 0.25800002],
          <a href="#teamsplayersstats">"stats"</a>: {
            <a href="#teamsstatspoints">"points"</a>: 5,
            <a href="#teamsstatspossession_time">"possession_time"</a>: 78.645569,
            <a href="#teamsstatsinterceptions">"interceptions"</a>: 0,
            <a href="#teamsstatsblocks">"blocks"</a>: 0,
            <a href="#teamsstatssteals">"steals"</a>: 0,
            <a href="#teamsstatscatches">"catches"</a>: 0,
            <a href="#teamsstatspasses">"passes"</a>: 0,
            <a href="#teamsstatssaves">"saves"</a>: 1,
            <a href="#teamsstatsgoals">"goals"</a>: 0,
            <a href="#teamsstatsstuns">"stuns"</a>: 14,
            <a href="#teamsstatsassists">"assists"</a>: 1,
            <a href="#teamsstatsshots_taken">"shots_taken"</a>: 5
          }
        }
        /* ...other blue players here */
      ]
    },
    {
      <a href="#teamsteam">"team"</a>: "ORANGE TEAM",
      <a href="#teamspossession">"possession"</a>: true,
      <a href="#teamsstats">"stats"</a>: {
        <a href="#teamsstatspoints">"points"</a>: 5,
        <a href="#teamsstatspossession_time">"possession_time"</a>: 80.32605,
        <a href="#teamsstatsinterceptions">"interceptions"</a>: 0,
        <a href="#teamsstatsblocks">"blocks"</a>: 0,
        <a href="#teamsstatssteals">"steals"</a>: 1,
        <a href="#teamsstatscatches">"catches"</a>: 0,
        <a href="#teamsstatspasses">"passes"</a>: 0,
        <a href="#teamsstatssaves">"saves"</a>: 2,
        <a href="#teamsstatsgoals">"goals"</a>: 0,
        <a href="#teamsstatsstuns">"stuns"</a>: 12,
        <a href="#teamsstatsassists">"assists"</a>: 1,
        <a href="#teamsstatsshots_taken">"shots_taken"</a>: 5
      },
      <a href="teamsplayers">"players"</a>: [
        /* ...orange players here; see blue players section for example */
      ]
    }
  ]
}
</pre>

#### Properties

The response is a JSON object, with the following properties:

##### `client_name`
The username of the currently signed-in user.

##### `sessionid`
A 128-bit string-encoded GUID.

##### `match_type`
Represents the type of match being played.

Possible values:

- `"Echo_Arena_Private"`
- TODO: What else?

##### `map_name`
Represents the current "map" (environment) the user is playing in.

- `"mpl_arena_a"` - Standard Echo Arena map
- TODO: What else?

##### `private_match`
Whether the current session is a private match.

##### `tournament_match`
Whether the current session is being used for an official tournament orchestrated in collaboration with the Echo Arena developers. This is [for possible future integration with ESL and other organized tournaments](https://discordapp.com/channels/326412222119149578/506931756675497986/510566303367430145).

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
An array of two integers representing which team currently [possesses](#possession-1) the disk.

TODO: Unclear exactly how this data is encoded.

##### `blue_points`
The current score of the blue team. This differs from [`teams[].stats.points`](#teamsstatspoints) in that it includes points scored as self goals.

##### `orange_points`
The current score of the orange team. This differs from [`teams[].stats.points`](#teamsstatspoints) in that it includes points scored as self goals.

##### `disc`
An object representing the current state of the disk.

##### `disc.position`
An array representing the disk's [position](#vectors) within the area.

##### `disc.velocity`
An array representing the disk's [velocity](#vectors).

##### `disc.bounce_count`
The number of times the disk has bounced. (TODO: Since the last time someone grabbed it? Do headbutts count as bounces?)

##### `last_score`
An object containing facts and statistics related to the last goal that that was scored in-game. (This is roughly the same information displayed on the Shield after a goal.)

Note that in some cases (such as when the disk is slapped into the goal) bugs may result in this information being inaccurate.

##### `last_score.disc_speed`
The speed of the disk in meters/second when it impacted the goal. This is `0` by default when no goal has been scored.

##### `last_score.team`
The team that scored. This is `"blue"` by default when no goal has been scored. Note that in the case of self goals, this value will still represent the team receiving points for the goal, not the team of the player who actually scored the goal. (TODO: This is probably accurate, but check to make sure.)

Possible values:

- `"blue"`
- `"orange"`

##### `last_score.goal_type`
A human-readable explanation of the type of goal scored. This is `"[NO GOAL]"` by default when no goal has been scored.

Possible values:

- `"[NO GOAL]"`
- `"BOUNCE SHOT"`???
- TODO: What else?

##### `last_score.point_amount`
The number of points scored (2 or 3). This is `0` by default when no goal has been scored.

##### `last_score.distance_thrown`
The distance the goal was scored from. This is `0` by default when no goal has been scored.

##### `last_score.person_scored`
The username of the player who scored the goal. This is `"[INVALID]"` by default when no goal has been scored. (TODO: Is "[INVALID]" a potentially valid player name?)

##### `last_score.assist_scored`
The username of the player who assisted the goal. This is `"[INVALID]"` by default when no goal has been scored. (TODO: What about when a goal was scored with no assist?)

##### `teams`

An array of objects containing data used to instantiate the game's two teams. The first element in the array is always the blue team, while the second is always the orange team.

##### `teams[].team`
A human-readable team name. Usually either "ORANGE TEAM" or "BLUE TEAM", but if all the players on a team have the same team name (set by pressing F11 while in a match or the lobby) it will be that instead.

##### `teams[].possession`
Indicates whether this team currently has [possession](#possession-1) of the disk.

##### `teams[].stats`
An object containing data used to instantiate the team's current stats.

##### `teams[].stats.possession_time`
Time in seconds that the subject [possessed](#possession-1) the disk.

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
Number of times the subject successfully caught a pass by a team member

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

##### `teams[].players[].level`
A number (1-50) representing the player's experience "level". New accounts start as level 1, and will usually reach level 50 after a few hundred games in public matchmaking.

Note that there a rare bug where this number may be 0 in the UI in some cases; it's possible this bug may also affect the API (though this has yet to be verified).

##### `teams[].players[].number`
The number a player chose for themselves in the customization room.

##### `teams[].players[].possession`
Indicates whether this player currently has [possession](#possession-1) of the disk.

##### `teams[].players[].stunned`
Whether the player is currently stunned.

##### `teams[].players[].blocking`
Whether the player is currently blocking (and will therefore deflect stuns).

##### `teams[].players[].invulnerable`
Whether or not the player is currently immune to stuns. Players will be in this state for several (TODO: how many?) seconds after they are stunned.

##### `teams[].players[].position`
The current [position](#vectors) of the player within the arena

##### `teams[].players[].velocity`
The current [velocity](#vectors) (speed and direction of movement) of the player.

##### `teams[].players[].lhand`
The [position](#vectors) of the player's left hand within the Arena.

##### `teams[].players[].rhand`
The [position](#vectors) of the player's right hand within the Arena.

##### `teams[].players[].forward`
The [direction](#vectors) that the player's head is facing.

##### `teams[].players[].left`
The [direction](#vectors) that the left side of the player's head is facing.

##### `teams[].players[].up`
The [direction](#vectors) that the top side of the player's head is facing.

##### `teams[].players[].stats`
An object containing data used to instantiate the player's current stats. See [`teams[].stats`](#teamsstats) for a list of available stats.

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
The API defines "possession" a little more broadly than you might expect (depending on what other sports you may be familiar with that use this term). Not only do players/teams that are currently holding the disk have possession, but teams also maintain possession for several (TODO: how many?) seconds after releasing the disk as well, unless the disk is recovered by the opposing team. If the disk is glowing with the color of a specific team, the game considers that team as having "possession".

### Session
A "session" is what users typically think of as the "server" you're playing on. When you join a new match, a new session is created, and the session will remain active until all players leave. Sessions IDs are unique, and have no correspondence to the actual, physical or virtual server hardware that's hosting the game.
