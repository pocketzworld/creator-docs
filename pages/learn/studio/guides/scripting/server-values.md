# **Server Values**

## **Introduction**
Server Values are server variables that send an event to the client when their value changes, enabling you to sync data between the client, server, and players.

### **Value Types**

`IntValue` `StringValue` `BoolValue` `Vector3Value` `NumberValue`

#### Example:
```lua
local myInt = IntValue.new("MyInt", 0) -- Value.new(ServerIdentifier, Default Value)
local myString = StringValue.new("MyString", "") -- Value.new(ServerIdentifier, Default Value)
local myBool = BoolValue.new("MyBool", false) -- Value.new(ServerIdentifier, Default Value)
```

### **Changing Server Values**
In the server you can set server values with the variable's `.value` property.

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

### **Connecting to value Changes on the Client**
On the client you can connect to the value's `Changed` event, gaining access to the new value and the old value.


#### Example:
```lua
function self:ClientAwake()
    --read the new server values after they are changed
    myInt.Changed:Connect(function(newVal, oldVal)
        print("the server value changed to " .. tostring(newVal))
    end)

end
```

By utilizing server values effectively, you can create dynamic and engaging experiences for players in your Highrise Studio projects.
