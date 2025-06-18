
# Network Values

## Introduction

Network Values are synchronized variables used to share data between the client and server. They trigger an event whenever their value changes. These are essential for keeping player data, game states, or positions in sync across the network.

They can be created in either `Client/Server` or `Module` scripts.

### Available Network Value Types:

- **IntValue** – Stores integers (e.g., score, level)
- **StringValue** – Stores strings (e.g., job, nickname)
- **BoolValue** – Stores true/false (e.g., isReady, inGame)
- **Vector3Value** – Stores position (e.g., Vector3 coordinates)
- **NumberValue** – Stores decimal numbers (e.g., speed, time)
- **TableValue** – Stores tables/dictionaries (e.g., player stats)

All network values optionally accept a **player** parameter. If provided, only that player will receive updates for that value. Otherwise, it syncs globally.

## Creating a Network Value

Each value type is created using `.new()`. The syntax is consistent across types:

```lua
local value = TypeValue.new("Name", initialValue, player)
```

### Parameters:
- **Name**: A unique identifier string.
- **InitialValue**: The starting value.
- **Player** *(optional)*: A player instance for player-specific synchronization.

## Example of Creating Each Type:

```lua
local score = IntValue.new("Score", 0, player)                     -- Integer
local job = StringValue.new("Job", "Unemployed", player)           -- String
local isReady = BoolValue.new("IsReady", false, player)            -- Boolean
local position = Vector3Value.new("Position", Vector3(0,0,0), player) -- Vector3
local speed = NumberValue.new("Speed", 1.5, player)                -- Decimal
local stats = TableValue.new("Stats", {kills=0, deaths=0}, player) -- Table
```

## Changing Values

To change the value on the server, use the `.value` property. Updates automatically propagate to the corresponding clients or the specific player if assigned.

<Note type="warning">
When changing values, ensure you are doing so on the server side to maintain synchronization.
</Note>

```lua
score.value = score.value + 1
job.value = "Builder"
position.value = Vector3.new(10, 5, 0)
```

## Listening for Changes

On the **client**, you can listen for changes using the `Changed` event. This event returns both the **new value** and the **old value**.

```lua
function self:ClientAwake()
    score.Changed:Connect(function(newVal, oldVal)
        print("Score changed from " .. oldVal .. " to " .. newVal)
    end)
end
```

## Player-Specific Network Values

When a value is created with a player as the third argument, **only that player** will receive updates for it.

```lua
function self:ServerStart()
    scene.PlayerJoined:Connect(function(scene, player)
        local personalData = TableValue.new("PlayerData", {}, player)
        personalData.value = {name = player.name, level = 1}
    end)
end
```

## Synchronization Rules

- **Name-based linking:** Values are matched between server and client by their name and optional player object.
- If a value is created on both server and client with the same name, they will sync automatically.
- If the player parameter is set, only that player sees the updates.

## Complete Example:

```lua
--!Type(Module)

local IncrementScoreRequest = Event.new("IncrementScoreRequest")
local players = {}

function TrackPlayers(game)
    game.PlayerConnected:Connect(function(player)
        players[player] = {
            player = player,
            score = IntValue.new("Score", 0, player),
            job = StringValue.new("Job", "Unemployed", player),
            isReady = BoolValue.new("IsReady", false, player),
            position = Vector3Value.new("Position", Vector3(0,0,0), player),
            stats = TableValue.new("Stats", {kills=0, deaths=0}, player),
        }
    end)

    game.PlayerDisconnected:Connect(function(player)
        players[player] = nil
    end)
end

function self:ClientAwake()
    local player = client.localPlayer
    local playerInfo = players[player]

    if playerInfo then
        playerInfo.score.Changed:Connect(function(newVal, oldVal)
            print("Score changed from " .. oldVal .. " to " .. newVal)
        end)
    end
end

function self:ServerStart()
    TrackPlayers(server)

    IncrementScoreRequest:Connect(function(player, amount)
        local playerInfo = players[player]
        if playerInfo then
            playerInfo.score.value = playerInfo.score.value + amount
        end
    end)
end
```

## Conclusion

Network Values are a powerful and simple way to sync data between the client and server. Whether it's player-specific data like scores, positions, or global data like game states, Network Values handle synchronization automatically and efficiently.
