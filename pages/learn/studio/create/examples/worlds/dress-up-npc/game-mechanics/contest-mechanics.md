# Contest Mechanics

This document provides a comprehensive overview of the contest mechanics implemented in the game, detailing how contests are created, managed, and presented to players.

## Overview

The contest system is designed to facilitate competitive gameplay, where players can participate in themed events, submit entries, and vote on others. It supports:
- Contest creation and management with flexible templates.
- Player outfit submissions and reward distribution.
- Voting systems for player engagement.
- Ranking and leaderboard features.

## Core Concepts

### 1. **Contest Templates**

Contest templates define the structure and rules of contests. They include parameters such as duration, ticket cost, and rewards.

#### Attributes
- **ID** (`_id`): Unique identifier for the contest.
- **Possible Styles** (`_possibleStyles`): A list of styles associated with the contest.
- **Display Data** (`_displayData`): Visual information used in the UI.
- **Duration** (`_duration`): Length of the contest in seconds.
- **Ticket Cost** (`_ticketCost`): Cost to enter the contest.
- **Top Player Count** (`_topPlayerCount`): Number of top players eligible for special rewards.
- **Participation Reward** (`_participationReward`): Rewards for all participants.
- **Top Rewards List** (`_topRewardsList`): Rewards for top players.

#### Key Functions
- `GetId`: Retrieves the contest ID.
- `GetRandomStyle`: Returns a random style from the possible styles.
- `GetReward`: Determines the reward based on a player’s rank.

### 2. **Contest Manager**

The `ContestManager.lua` handles contest lifecycle management, including creation, voting, and result computation.

#### Responsibilities
- Initializing new contests.
- Managing player submissions.
- Handling voting and score calculations.
- Distributing rewards to participants.

#### Key Functions
- `StartContest`: Creates a new contest based on a specified template.
- `SubmitOutfitForContest`: Handles player submissions for contests.
- `RequestPlacementForContest`: Retrieves placement data for a contest.
- `CastVote`: Records votes for submitted outfits.
- `GetOutfitScore`: Calculates the score of an outfit based on votes.

### 3. **UI Components**

#### Contest UI
The main interface for players to view ongoing contests, submit outfits, and access voting and results.

#### Voting UI
Allows players to vote on submitted outfits. Features include:
- Star ratings for visualizing scores.
- Special effects to enhance engagement during voting.

#### Results UI
Displays final rankings and rewards after a contest concludes.

## Workflow

1. **Contest Initialization**
   - `StartContest` initializes a new contest based on a selected template.
   - Contests are assigned a unique ID and end time.

2. **Player Submission**
   - Players submit outfits using `SubmitOutfitForContest`.
   - Outfits are validated and stored, and the submission fee is deducted.

3. **Voting**
   - Players vote on outfits via the Voting UI.
   - Votes are recorded, and scores are updated using `CastVote`.

4. **Results and Rewards**
   - At the contest’s conclusion, `RequestPlacementForContest` computes rankings.
   - Rewards are distributed based on rankings.

## Example Implementation

### Example Contest Template
```lua
local contestTemplate = {
  _id = "contest_001",
  _possibleStyles = {"Elegant", "Casual", "Fantasy"},
  _duration = 300,
  _ticketCost = 5,
  _topPlayerCount = 10,
  _participationReward = participationLoot,
  _topRewardsList = {topReward1, topReward2},
}
```

### Starting a Contest
```lua
ContestManager.StartContest(contestTemplate)
```

### Submitting an Outfit
```lua
ContestManager.SubmitOutfitForContest(contestId, outfitData, nil, function(code)
  if code == 0 then
    print("Submission successful!")
  else
    print("Submission failed with error code:", code)
  end
end)
```

### Casting a Vote
```lua
ContestManager.CastVote(contestData, votedPlayerId, opposingPlayerId)
```

## Key Events

### `ContestStartedEvent`
Triggered when a new contest begins, notifying players and updating the UI.

### `ContestEndedEvent`
Triggered at the end of a contest, finalizing rankings and rewards.

### `ContestOutfitAddResponseEvent`
Provides feedback on player outfit submissions.

### `ContestVotingBlockResponseEvent`
Delivers voting blocks for players to engage in the voting process.
