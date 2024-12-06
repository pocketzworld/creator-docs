# Leaderboard API Documentation

## Overview

Leaderboards allow you to create competitive environments for players by showcasing their scores and ranks in real-time. This API provides all the necessary methods to integrate leaderboard functionality into your game.

## API Reference

### **LeaderboardEntry**
Represents a single entry in a leaderboard.

| Property | Type   | Description                       |
|----------|--------|-----------------------------------|
| `id`     | string | Unique identifier for the entry. |
| `name`   | string | Name of the player or entry.     |
| `score`  | number | The score of the entry.          |
| `rank`   | number | The rank of the entry.           |


### **Methods**

#### `Reset`
Clears all entries in a leaderboard.

```lua
Leaderboard.Reset(leaderboardID: string, cb: (err: LeaderboardError) -> ())
```

| Parameter       | Type   | Description                        |
|------------------|--------|------------------------------------|
| `leaderboardID` | string | ID of the leaderboard to reset.    |
| `cb`            | function | Callback function with error status. |

#### `GetEntries`
Retrieves a list of entries from a leaderboard.

```lua
Leaderboard.GetEntries(leaderboardID: string, fromRank: number, limit: number, cb: (entries: {LeaderboardEntry}, err: LeaderboardError) -> ())
```

| Parameter       | Type     | Description                                  |
|------------------|----------|----------------------------------------------|
| `leaderboardID` | string   | ID of the leaderboard.                       |
| `fromRank`      | number   | Starting rank for retrieval.                 |
| `limit`         | number   | Maximum number of entries to retrieve.       |
| `cb`            | function | Callback with entries and error status.      |

#### `IncrementScore`
Increases the score of a specific entry.

```lua
Leaderboard.IncrementScore(leaderboardID: string, entryID: string, increment: number, cb: (entry: LeaderboardEntry, err: LeaderboardError) -> ())
```

#### `SetScore`
Sets the score of a specific entry.

```lua
Leaderboard.SetScore(leaderboardID: string, entryID: string, score: number, cb: (entry: LeaderboardEntry, err: LeaderboardError) -> ())
```

#### `DeleteEntry`
Removes an entry from a leaderboard.

```lua
Leaderboard.DeleteEntry(leaderboardID: string, entryID: string, cb: (err: LeaderboardError) -> ())
```

### Player-Specific Methods

#### `GetEntryForPlayer`
Fetches a leaderboard entry for a specific player.

```lua
Leaderboard.GetEntryForPlayer(leaderboardID: string, player: Player, cb: (entry: LeaderboardEntry, err: LeaderboardError) -> ())
```

| Parameter       | Type     | Description                                |
|------------------|----------|--------------------------------------------|
| `leaderboardID` | string   | ID of the leaderboard.                     |
| `player`        | Player   | The player whose entry is being retrieved. |
| `cb`            | function | Callback with the entry and error status.  |

#### `IncrementScoreForPlayer`
Increases the score of a specific player in the leaderboard.

```lua
Leaderboard.IncrementScoreForPlayer(leaderboardID: string, player: Player, increment: number, cb: (entry: LeaderboardEntry, err: LeaderboardError) -> ())
```

#### `SetScoreForPlayer`
Sets a specific score for a player in the leaderboard.

```lua
Leaderboard.SetScoreForPlayer(leaderboardID: string, player: Player, score: number, cb: (entry: LeaderboardEntry, err: LeaderboardError) -> ())
```

#### `DeleteEntryForPlayer`
Deletes a leaderboard entry for a specific player.

```lua
Leaderboard.DeleteEntryForPlayer(leaderboardID: string, player: Player, cb: (err: LeaderboardError) -> ())
```


## Testing Example

Below is an example demonstrating how to test the leaderboard functions:

```lua
local lb: Leaderboard = Leaderboard

function printEntry(entry: LeaderboardEntry)
    print("ID: " .. entry.id)
    print("Name: " .. entry.name)
    print("Score: " .. entry.score)
    print("Rank: " .. entry.rank)
end

server.PlayerConnected:Connect(function(player: Player)
    print(player.name .. " has connected!")

    -- In this example, we are setting a score for the player and retrieving the top entries.
    lb.SetScoreForPlayer("my_leaderboard", player, 150, function(entry, err)
        if err ~= 0 then
            print("Error setting score for player: " .. err)
            return
        end

        print("Set score for player:")
        printEntry(entry)

        lb.GetEntries("my_leaderboard", 1, 10, function(entries, err)
            if err ~= 0 then
                print("Error retrieving leaderboard entries: " .. err)
                return
            end

            print("Top leaderboard entries:")
            for _, entry in ipairs(entries) do
                printEntry(entry)
            end
        end)
    end)
end)

server.PlayerDisconnected:Connect(function(player: Player)
    print(player.name .. " has disconnected!")
    lb.DeleteEntryForPlayer("my_leaderboard", player, function(err)
        if err ~= 0 then
            print("Error deleting player entry: " .. err)
            return
        end
        print("Player entry deleted.")
    end)
end)
```

## Implementation Notes

- Use `Leaderboard.Reset` to clear a leaderboard during testing or at the start of a new game session.
- All methods include error handling to manage network or logic issues.
- All leaderboard methods must be called from the server context.
- Customize `playerConnected` and `playerDisconnected` callbacks to suit your game logic.

## Conclusion

Leaderboards are a powerful tool for creating competitive environments in your game. By integrating the Leaderboard API, you can provide players with a way to compete against each other and track their progress over time.