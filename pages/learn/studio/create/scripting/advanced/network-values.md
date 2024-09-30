# Network Values

## Introduction
Network values are variables that send an event when their value changes, allowing data synchronization between the client, server, and players. They can be used in either `Client/Server` or `Module` scripts.

### Value Types
- `IntValue`
- `StringValue`
- `BoolValue`
- `Vector3Value`
- `NumberValue`
- `TableValue`

All network values can now accept an optional player object as a parameter during creation. When a player is specified, only that player will receive updates for the respective value.

#### Example:
```lua
local score = IntValue.new("Score", 0, player) 
local job = StringValue.new("Job", "Unemployed", player)
local inGame = BoolValue.new("InGame", false, player)
local position = Vector3Value.new("Position", Vector3.new(0, 0, 0), player)
```

### Changing Values
On the server, you can modify a value using its `.value` property. Any changes to the value on the server will automatically be sent to all clients, or only to the specified player if one was provided.

#### Example:
```lua
function self:ServerAwake()
    updateScoreEvent:Connect(function(player)
        score.value = score.value + 1 -- Broadcast to all clients
    end)
end
```

### Player-Specific Network Values
When a network value is created with a specific player, it ensures that only that player will receive updates for that value. The value can still be accessed by the server and updated for the player as needed.

#### Example: Server-Side
```lua
function self:ServerStart()
    scene.PlayerJoined:Connect(function(scene, player)
        local playerTable = TableValue.new("PlayerData", {}, player)
        playerTable.value = { player.name }
    end)
end
```

### Client-Server Synchronization
Network values are linked between the client and server using their names. As long as the name matches, the value can be created in different places, such as the client and server, and still synchronize correctly.

### Connecting to Value Changes on the Client
On the client, you can listen to the value's `Changed` event to react when the value is updated. This event passes both the new and old values.

#### Example:
```lua
function self:ClientAwake()
    score.Changed:Connect(function(newVal, oldVal)
        print("Score changed from " .. tostring(oldVal) .. " to " .. tostring(newVal))
    end)
end
```

### Important Note
It's important to remember that the name of the value (and the player, if specified) links the value between the client and server. This allows you to create the value in different places as long as the name matches. Player-specific values help avoid sending unnecessary data to other clients, reducing network load.

## Conclusion

Using network values, you can efficiently synchronize data between clients and servers. The functionality for all network values to accept a player object allows you to optimize network usage, sending updates only to relevant players when necessary.