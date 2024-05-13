# Client and Server Scripts

Client and Server scripts are a special type of script that can run on both the client and server sides of the game. This dual functionality allows them to share code and communicate with each other, enabling seamless interactions between the two environments.

## Overview

Client and Server scripts are designed to operate on both the client and server sides of the game. They are particularly useful for implementing shared functionality that requires communication between the client and server. By running on both sides, these scripts can synchronize game state, exchange data, and coordinate actions between players and the game world.

## Use Cases

Client and Server scripts are commonly used for the following purposes:

- **Shared Logic**: Implementing game logic that needs to be consistent across all clients and the server.
- **Data Synchronization**: Keeping player data, inventory, and other game state synchronized between the client and server.
- **Remote Events**: Triggering events on the server from the client or vice versa.
- **Player Interactions**: Handling player interactions that require coordination between the client and server.

## Events and Connections

When writing a `Client/Server` script, you gain access to new versions of the main event functions: `Awake`, `Start`, `Update`, and `FixedUpdate`. These functions can be prefixed with `Client` or `Server` to specify whether they should run on the client or server side. For example, `ClientUpdate` will only run on the client side, while `ServerUpdate` will only run on the server side.

- `ClientAwake()`, `ServerAwake()`
- `ClientStart()`, `ServerStart()`
- `ClientUpdate()`, `ServerUpdate()`
- `ClientFixedUpdate()`, `ServerFixedUpdate()`

[Variables](https://create.highrise.game/learn/studio/create/scripting/lua/features/variables) and [functions](https://create.highrise.game/learn/studio/create/scripting/lua/features/functions) defined outside of these functions will be shared between the client and server sides.

For example, you can define a function in a `Client/Server` script that is accessible from both the client and server sides:

```lua
local playerName = "Player1"

function self:ClientAwake()
  playerName = "ClientPlayer"
  print(playerName) -- Output: ClientPlayer
end

function self:ServerAwake()
  print(playerName) -- Output: Player1
end
```

However, variables defined inside a function are local to that function and will not be shared between the client and server sides:

```lua
function self:ClientAwake()
  local playerHealth = 100
  print(playerHealth) -- Output: 100
end

function self:ServerAwake()
  print(playerHealth) -- Output: nil
end
```

## Connecting Client and Server

To establish communication between the client and server sides, you can use events. Events enable firing and connecting to events on both the client and server sides. You can trigger an event on the client side and have it handled on the server side, or vice versa.

```lua
-- Create two custom events: one for client requests and one for server responses
local myRequest = Event.new("MyRequest")
local myResponse = Event.new("MyResponse")

-- Client-side function called when the client initializes
function self:ClientAwake()
  -- Prepare data to send to the server
  local data = { message = "Hello from client!" }
  -- Fire the "MyRequest" event on the server side and pass the data
  myRequest:FireServer(data)

  -- Listen for responses from the server
  myResponse:Connect(function(arg)
    -- Print the message received from the server
    print(arg.message) -- Output: Hello from server!
  end)
end

-- Server-side function called when the server initializes
function self:ServerAwake()
  -- Listen for requests from clients
  myRequest:Connect(function(player, data)
    -- Print the message received from the client
    print(data.message) -- Output: Hello from client!
    -- Send a response back to the client
    myResponse:FireClient(player, { message = "Hello from server!" })
  end)
end
```

By using events and shared variables, you can create powerful interactions between the client and server sides of your game. This enables you to implement complex game mechanics, synchronize game state, and provide seamless multiplayer experiences for your players.