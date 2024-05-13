# **Player and Character Events**

## **Introduction**
Player and Character Events are crucial for managing player interactions and character states in your Highrise Studio projects. In this guide, you'll learn about various events triggered when players connect, disconnect, join scenes, leave scenes, and when their characters change.

### **Player Connected and Disconnected Events**

The `game.PlayerConnected` and `game.PlayerDisconnected` events are triggered when a player connects or disconnects from the world, respectively. These events are fired on both the client and server, passing the player as a parameter.

#### Example:
```lua
-- Client
function self:ClientAwake()

    client.PlayerConnected:Connect(function(player)
        print(player.name .. " connected to the world on this client")
    end)

    client.PlayerDisconnected:Connect(function(player)
        print(player.name .. " disconnected from the world on this client")
    end)
end

-- Server
function self:ServerAwake()

    server.PlayerConnected:Connect(function(player)
        print(player.name .. " connected to the server")
    end)

    server.PlayerDisconnected:Connect(function(player)
        print(player.name .. " disconnected from the server")
    end)
end
```

### Player Joined and Left Events

The `scene.PlayerJoined` and `scene.PlayerLeft` events are triggered when a player joins or leaves a scene, respectively. These events are fired when a player's avatar enters or exits a particular scene, passing both the scene and player as parameters.

#### Example:
```lua
scene.PlayerJoined:Connect(function(scene, player)
    print(player.name .. " joined the scene")
end)

scene.PlayerLeft:Connect(function(scene, player)
    print(player.name .. " left the scene")
end)
```

### Character Changed Event

The `player.CharacterChanged` event is triggered when a player's character (visual avatar) changes, including when it is first instantiated. This event provides information about the player and their character as parameters.

#### Example:
```lua
-- Get the `player` when they join a scene
scene.PlayerJoined:Connect(function(scene, player)
    -- Connect to the player's character changed event
    player.CharacterChanged:Connect(function(player, character) 
        -- Perform actions based on player and character values
    end)
end)
```

By utilizing these player and character events effectively, you can create dynamic and engaging experiences for players in your Highrise Studio projects.
