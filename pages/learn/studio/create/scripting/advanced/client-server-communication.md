# Client Server Communication

In Highrise Studio, you can establish communication between the client and server sides using events and/or [network values](https://create.highrise.game/learn/studio/create/scripting/advanced/network-values). Events enable firing and connecting to events on both the client and server sides. You can trigger an event on the client side and have it handled on the server side, or vice versa.

## Acceptable Data Types

Events can accept any [data type](https://create.highrise.game/learn/studio/create/coding-fundamentals/variables-and-data-types) as an argument, including tables, strings, numbers, and more. When firing an event, you can pass any data you want to the connected functions.

<Note>
When a client fires an event to the server with `FireServer`, the function connected on the server receives the player who sent it as its first argument, followed by the arguments the client passed.
When the server fires an event to one client with `FireClient`, its first argument is the player to send it to. The function connected on that client receives only the arguments after the player.
</Note>

Here's an example:

**Example.lua**
```lua
local myEvent = Event.new("MyEvent")

function self:ClientAwake()
  local localPlayer = client.localPlayer
  -- Listen for the event from the server
  myEvent:Connect(function(message)
    -- Print the player's name and the message received from the server
    print(localPlayer.name .. ", server says: " .. message) -- Output: Player1, server says: Hello from server!
  end)
end

function self:ServerAwake()
  -- Listen for the event on the server side
  scene.PlayerJoined:Connect(function(scene, player)
    local message = "Hello from server!"
    -- Fire the event on the client side and pass the message
    myEvent:FireClient(player, message) -- When firing to an individual client, you must pass a userdata object
  end)
end
```

In this example, the server listens for the `PlayerJoined` event and fires the `myEvent` event on the client side with the message "Hello from server!". The client receives the message and prints it along with the player's name.

## Connection Methods

You can use the following methods to connect to events on the client and server sides:

- **Connect:** Connects a function to the event. The function will be called whenever the event is fired.
- **FireServer:** Fires the event on the server side. You can pass any data as arguments to the connected functions.
- **FireClient:** Fires the event on one player's client. Pass the player first, then any data as arguments to the connected functions.
- **FireAllClients:** Fires the event on all clients. You can pass any data as arguments to the connected functions.

## Example Use Cases

In this example use case, we'll create a simple score system where the server keeps track of the player's score and updates it when the player collects a coin.

A player can modify their client and fire any event with any arguments, so the server must never take a client's word for something that matters, like how many points it earned. Here the client only says which coin it touched. The server checks that the player could have collected that coin, and decides what it's worth.

**ScoreSystem.lua**
```lua
--!Type(Module)

local GetMyScoreRequest = Event.new("GetMyScoreRequest")
local CollectCoinRequest = Event.new("CollectCoinRequest")
local ScoreChanged = Event.new("ScoreChanged")

local COIN_POINTS = 10 -- What a coin is worth; only the server uses it
local MAX_COLLECT_DISTANCE = 3 -- How close a player's character must be to a coin to collect it

local collectedCoins = {} -- On the server: for each player's name, the coins they have collected

-- Function for client scripts to call when the local player touches a coin
CollectCoin = function(coin : GameObject)
  CollectCoinRequest:FireServer(coin.name)
end

-- Function to handle client initialization
function self:ClientAwake()
  -- Listen for the player's score from the server
  ScoreChanged:Connect(function(score)
    print("My score is: " .. score)
  end)

  -- Request the player's score from the server
  GetMyScoreRequest:FireServer()
end

-- Function to send a player their score from storage
local function SendScore(player)
  Storage.GetPlayerValue(player, "score", function(score)
    ScoreChanged:FireClient(player, score or 0)
  end)
end

-- Function to handle server initialization
function self:ServerAwake()
  server.PlayerConnected:Connect(function(player)
    collectedCoins[player.name] = {}
  end)
  server.PlayerDisconnected:Connect(function(player)
    collectedCoins[player.name] = nil
  end)

  -- Listen for score requests from clients
  GetMyScoreRequest:Connect(SendScore)

  -- Listen for coin collections from clients, and check each one before awarding points
  CollectCoinRequest:Connect(function(player, coinName)
    local collected = collectedCoins[player.name]
    -- Ignore anything but the name of a coin this player hasn't collected yet
    if type(coinName) ~= "string" or collected == nil or collected[coinName] then return end

    -- Ignore a coin that doesn't exist or that the player's character is too far away to touch
    local coin = GameObject.Find(coinName)
    if coin == nil or player.character == nil then return end
    if Vector3.Distance(player.character.transform.position, coin.transform.position) > MAX_COLLECT_DISTANCE then return end

    collected[coinName] = true
    Storage.IncrementPlayerValue(player, "score", COIN_POINTS, function()
      SendScore(player)
    end)
    print(player.name .. " collected " .. coinName)
  end)
end
```

In this example, the server keeps each player's score in storage and sends it to the player's client when the client asks for it and whenever it changes. When the player touches a coin, the client sends the coin's name to the server. The server ignores the request unless the coin exists, the player is close enough to it, and the player hasn't already collected it; then it adds the coin's points. Give each coin a unique name, since the server finds the coin by its name.

<Note type="warning">
In the example above, the script type is a `Module` script, which allows us to use the `CollectCoin` function in different scripts.
</Note>

Assuming you have a script that handles the coin collection, let's say `CoinCollector` that has `OnTriggerEnter` function to detect when the player collects a coin. You can call the `CollectCoin` function from the `CoinCollector` script when the local player touches the coin.

**CoinCollector.lua**
```lua
--!Type(Client)

-- Require the module script that contains the CollectCoin function, in this case, the ScoreSystem module script
local ScoreSystem = require("ScoreSystem")

-- Function to handle trigger enter event
function self:OnTriggerEnter(other : Collider)
  -- Get the character component of the collider's game object
  local playerCharacter = other.gameObject:GetComponent(Character)

  -- If there is no character component, return
  if playerCharacter == nil then return end

  -- Check if the local player touched the coin
  if client.localPlayer == playerCharacter.player then
    -- Tell the server which coin was touched; the server decides whether it counts
    ScoreSystem.CollectCoin(self.gameObject)
  end
end
```

In this example, the `CoinCollector` script detects when the local player touches a coin and calls the `CollectCoin` function from the `ScoreSystem` module script, which asks the server to award the coin's points.

By utilizing events effectively, you can create dynamic and engaging experiences for players in your Highrise Studio projects.

<Note>
Events can also be called from a `Module` script. This allows you to create a centralized script that handles events and can be accessed by other scripts in your project.
</Note>

Assuming you have a `EventsFactory` module script that creates and exports events, you can use the events in other scripts by requiring the `EventsFactory` module script.

**EventsFactory.lua**
```lua
MyEvent = Event.new("MyEvent")
```

**ClientScript.lua**
```lua
local EventsFactory = require("EventsFactory")

function self:Awake()
  -- Connect to the event
  MyEvent:Connect(function()
    print("My event fired!")
  end)
end
```


## Conclusion

Events are a powerful tool for establishing communication between the client and server sides of your game. By using events, you can create complex game mechanics, synchronize game state, and provide seamless multiplayer experiences for your players. Experiment with different event types and data structures to enhance the interactivity and engagement of your Highrise Studio projects.