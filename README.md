# Echo VR API Documentation

Unofficial documentation for Echo VR's HTTP API.

## Summary

In short, if you execute Echo VR with the `-http` argument an http server will run during matches at `http://127.0.0.1:80/`. You can then query that server to access various information about the state of the match in progress.

This repository aims to document all the functionality of this API.

### GET /session

This returns a detailed representation of the current state of the match. The response is JSON, with an additional [null byte](https://en.wikipedia.org/wiki/Null_character) at the end that you may need to trim off before feeding it to your JSON parser.

Example response (formatted for readability):

<pre>
{
  <a href="#sessionid">"sessionid"</a>: "0BD7D136-E487-11E8-9F32-F2801F1B9FD1",
  <a href="#game_clock_display">"game_clock_display"</a>: "00:45.65",
  <a href="#game_clock">"game_clock"</a>: 45.659531,
  <a href="#game_status">"game_status"</a>: "playing",
  <a href="#possession">"possession"</a>: [1, 0],
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
          <a href="#teamsplayerspossession">"possession"</a>: false,
          <a href="#teamsplayersposition">"position"</a>: [
            -11.089001,
            -0.70900005,
            -9.6930008
          ],
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
      "stats": {
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
Indicates whether this team currently has possession of the disk.

##### `teams[].stats`
An object containing data used to instantiate the team's current stats.

##### `teams[].stats.possession_time`
Time in seconds that the subject possessed the disk.

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

##### `teams[].players[].possession`
Indicates whether this player currently has possession of the disk.

##### `teams[].players[].position`
The current position of the player within the arena

##### `teams[].players[].stats`
An object containing data used to instantiate the player's current stats. See [`teams[].stats`](#teamsstats) for a list of available stats.
