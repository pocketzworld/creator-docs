# Network Values

## Introduction
Network values are variables that send an event to the client when their value changes, enabling you to sync data between the client, server, and players. They need to be in either a `Client/Server` or `Module` script.

### Value Types
- `IntValue`
- `StringValue`
- `BoolValue`
- `Vector3Value`
- `NumberValue`

#### Example:
```lua
local score = IntValue.new("Score", 0) -- Value.new(ServerIdentifier, Default Value)
local job = StringValue.new("Job", "Unemployed") -- Value.new(ServerIdentifier, Default Value)
local inGame = BoolValue.new("InGame", false) -- Value.new(ServerIdentifier, Default Value)
local position = Vector3Value.new("Position", Vector3.new(0, 0, 0)) -- Value.new(ServerIdentifier, Default Value)
```

### Changing Values
On the server you can change the value using the `.value` property.
Changing a value on the server will automatically broadcast that change to all clients.

#### Example:
```lua
function self:ServerAwake()
    -- Assuming you have event for updating score
    updateScoreEvent:Connect(function(player)
        -- Increase the player's score by 1
        score.value = score.value + 1 -- This will be broadcasted to all clients
    end)
end
```

### Connecting to Value Changes on the Client
On the client you can connect to the value's `Changed` event, gaining access to the new value and the old value. This works on client and server

<Note type="warning">
When dealing with network values, it is important to remember that when listening to the `Changed` event, the `newVal` will always come first, followed by the `oldVal`. 
</Note>

#### Example:
```lua
function self:ClientAwake()
    --read the new network value after it is changed
    score.Changed:Connect(function(newVal, oldVal)
        print("Score changed from " .. tostring(oldVal) .. " to " .. tostring(newVal))
    end)
end
```

## Conclusion

By utilizing network value effectively, you can create dynamic and engaging experiences for players in your Highrise Studio projects.