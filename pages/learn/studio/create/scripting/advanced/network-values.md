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
local myInt = IntValue.new("MyInt", 0) -- Value.new(ServerIdentifier, Default Value)
local myString = StringValue.new("MyString", "") -- Value.new(ServerIdentifier, Default Value)
local myBool = BoolValue.new("MyBool", false) -- Value.new(ServerIdentifier, Default Value)
```

### Changing Values
On the server you can change the value using the `.value` property.
Changing a value on the server will automatically broadcast that change to all clients.

#### Example:
```lua
function self:ServerAwake()
    --change the values when some event is fired
    someEvent:Connect(function()
        myInt.value = 5
        myString.value = "Hello World"
        myBool.value = true
    end)
end
```

### Connecting to Value Changes on the Client
On the client you can connect to the value's `Changed` event, gaining access to the new value and the old value. This works on client and server


#### Example:
```lua
function self:ClientAwake()
    --read the new network value after it is changed
    myInt.Changed:Connect(function(newVal, oldVal)
        print("the server value changed to " .. tostring(newVal))
    end)
end
```

By utilizing network value effectively, you can create dynamic and engaging experiences for players in your Highrise Studio projects.
