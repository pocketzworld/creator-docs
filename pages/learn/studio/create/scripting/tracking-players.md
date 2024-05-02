# **Tracking Players with a Lua Module**

## **Introduction**
In game development, tracking player data and responding to player events like joining, leaving, or changing characters is crucial for creating engaging multiplayer experiences. This guide introduces a Lua script that helps manage player information within a game environment.

## Create a Player Tracking Module

### 1. Initialize Player Tracking

To start, create a table called `players` that will store information about each player as they join the game.

```lua
players = {}
```
- This line sets up an empty table named `players` to keep track of player data.

### 2. Implement Player Tracking Function

Next, define a function named `TrackPlayers` to handle player-related events such as when a player joins, changes their character, or disconnects from the game.

```lua
local function TrackPlayers(game, characterCallback)
    -- Event: Player Joins
    scene.PlayerJoined:Connect(function(scene, player)
        -- Add the player to the 'players' table with initial data
        players[player] = {
            player = player,
            score = IntValue.new("score" .. tostring(player.id), 0)
        }

        -- Event: Character Changed
        player.CharacterChanged:Connect(function(player, character)
            local playerinfo = players[player]
            -- Check if the character is instantiated
            if character == nil then
                return  -- If no character, exit the function
            end

            -- Call the provided callback function with player info
            if characterCallback then
                characterCallback(playerinfo)
            end
        end)
    end)

    -- Event: Player Disconnects
    game.PlayerDisconnected:Connect(function(player)
        -- Remove the player from the 'players' table upon disconnect
        players[player] = nil
    end)
end
```
- This function sets up event listeners to respond when a player joins (`PlayerJoined`), changes their character (`CharacterChanged`), or disconnects from the game (`PlayerDisconnected`).

### 3. Client-Side Initialization

Configure client-side behavior and define a callback function (`OnCharacterInstantiate`) to handle character-related events.

```lua
function self:ClientAwake()
    -- Callback Function for Character Instantiation
    function OnCharacterInstantiate(playerinfo)
        local player = playerinfo.player
        local character = player.character

        -- Listen for changes to the player's score
        playerinfo.score.Changed:Connect(function(newVal, oldVal)
            print(player.name .. ": " .. tostring(newVal))  -- Print the new score value
        end)
    end

    -- Start tracking players on the client side
    TrackPlayers(client, OnCharacterInstantiate)
end
```
- This section sets up a callback function (`OnCharacterInstantiate`) that listens for changes to a player's score and prints the updated value to the console.

### 4. Server-Side Initialization

Initialize player tracking on the server side, which focuses on managing player data without specific client-related behavior.

```lua
function self:ServerAwake()
    -- Start tracking players on the server side
    TrackPlayers(server)

    -- Increase a players Score by 1
    function addPointToPlayer(player)
        local newScore = players[player].score.value + 1
        players[player].score.value = newScore
    end
end
```
- `TrackPlayers(server)` initiates player tracking on the server to handle player events like joining and disconnecting.
- `addPointToPlayer(player)` Increases the given player's Network Value `score` by 1. This is to be called after connecting to an `Event` fired from the `client` depending on gameplay.

## **Complete Module Script:**

```lua
players = {} -- a table variable to store current players  and info

local function TrackPlayers(game, characterCallback)
    scene.PlayerJoined:Connect(function(scene, player) -- When a player joins a scene add them to the players table
        players[player] = {
            player = player,
            score = IntValue.new("score" .. tostring(player.id), 0) --Score is a Network integer with an ID built of the player's ID to ensure uniqueness
        }
        -- Each player is a `Key` in the table, with the values `player` and `score`

        player.CharacterChanged:Connect(function(player, character) 
            local playerinfo = players[player] -- After the player's character is instantiated store their info from the player table (`player`,`score`)
            if (character == nil) then
                return --If no character instantiated return
            end 

            if characterCallback then -- If there is a character callback provided call it with a reference to the player info
                characterCallback(playerinfo)
            end
        end)
    end)

    game.PlayerDisconnected:Connect(function(player) -- Remove player from the current table if they disconnect
        players[player] = nil
    end)
end

--[[
    Client
]]
function self:ClientAwake()

    -- Create OnCharacterInstantiate as the callback for the Tracking function, to acces the playerinfo on client for each player that joins
    function OnCharacterInstantiate(playerinfo)
        local player = playerinfo.player
        local character = player.character

        --The function to run everytime someones score changes
        playerinfo.score.Changed:Connect(function(newVal, oldVal)
            print(player.name .. ": " .. tostring(newVal))
        end)
    end

    -- Track players on Client with a callback
    TrackPlayers(client, OnCharacterInstantiate)
end

--[[
    Server
]]
function self:ServerAwake()
    -- Track players on the server, with no callback
    TrackPlayers(server)

    -- Increase a players Score by 1
    function addPointToPlayer(player)
        local newScore = players[player].score.value + 1
        players[player].score.value = newScore
    end
end
```

## **Conclusion**

This Lua script provides a structured approach to tracking players in a game environment. It manages player data efficiently and responds to player-related events using event listeners and callback functions. Use this script as a foundation to enhance multiplayer game functionalities in Lua.