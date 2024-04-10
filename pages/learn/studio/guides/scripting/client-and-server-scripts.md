# **Client and Server Interaction**

## **Introduction**
In this guide, you will explore the intricacies of managing client and server logic using Lua scripts in Highrise Studio. Lua scripts come in four types: Client, Server, Client/Server, and Module. Understanding these script types and their functionalities is crucial for developing robust and interactive experiences in your Highrise world.

### Types of Lua Scripts:

1. **Client Scripts:**
   - Client scripts execute independently on the user's client, operating without reliance on the server or other users. They handle client-side interactions and logic.

2. **Server Scripts:**
   - Server scripts exclusively run on the server. They manage server-side logic, ensuring data integrity and handling core game mechanics.

3. **Client/Server Scripts:**
   - These scripts run on both the client and the server. They facilitate communication and synchronization between the client and server components of your Highrise world.

### Scripting Events and Connections:

When writing a client/server script, you gain access to new versions of the main event functions: `Awake`, `Start`, `Update`, and `FixedUpdate`. These functions can be prefixed with `Client` or `Server` to differentiate their execution context:

- `ClientAwake()`, `ServerAwake()`
- `ClientStart()`, `ServerStart()`
- `ClientUpdate()`, `ServerUpdate()`

Variables and functions defined outside of these functions in a client/server script are accessible by both the client and the server, but they are defined individually. For example:

```lua
local myVariable = "Old String"

function self:ClientAwake()
    myVariable = "New String"
    print(myVariable) -- Prints "New String" on the client
end

function self:ServerAwake()
    print(myVariable) -- Prints "Old String" on the server
end
```

However, variables defined inside a function are only accessible within that function's scope:

```lua
function self:ClientAwake()
    local myVariable = "New String"
    print(myVariable) -- Prints "New String" on the client
end

function self:ServerAwake()
    print(myVariable) -- Prints nil on the server
end
```

### Connecting Client and Server:

To establish communication between the client and server, you can use events. Events enable firing and connecting to events on both the client and server, allowing for parameter passing. Here's an example:

```lua
local myRequest = Event.new("MyRequest")
local myEvent = Event.new("MyEvent")

function self:ClientAwake()
    local myVar = "Hello World"
    myRequest:FireServer(myVar) -- Fire event to the server with parameter myVar

    myEvent:Connect(function(arg) -- Connect to event fired by the server and read parameter sent with it
        print(arg) -- Prints "Hello World"
    end)
end

function self:ServerAwake()
    myRequest:Connect(function(player, arg) -- First parameter in an event fired by a client is the player who fired the event, followed by custom parameters
        myEvent:FireAllClients(arg) -- Fire myEvent to all clients with parameter arg
    end)
end
```

By understanding these concepts and leveraging Lua scripting effectively, you can create dynamic and interactive experiences in your Highrise world that seamlessly integrate client and server interactions.
