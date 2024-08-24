# Client Server Communication

In Highrise Studio, you can establish communication between the client and server sides using events. Events enable firing and connecting to events on both the client and server sides. You can trigger an event on the client side and have it handled on the server side, or vice versa.

## Acceptable Data Types

Events can accept any [data type](https://create.highrise.game/learn/studio/create/coding-fundamentals/variables-and-data-types) as an argument, including tables, strings, numbers, and more. When firing an event, you can pass any data you want to the connected functions.

<Note>
When firing to client only, the first argument of the event will always be the player object.
So, when connecting to an event that is fired to client only, the first argument of the connected function should be the player object.
</Note>

Here's an example:

**Example.lua**
```lua
local myEvent = Event.new("MyEvent")

function self:ClientAwake()
  local localPlayer = client.localPlayer
  -- Fire the event on the server side
  myEvent:Connect(function(message)
    -- Print the player's name and the message received from the server
    print(localPlayer.name .. ", server says: " .. message) -- Output: Player1 says: Hello from server!
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
- **FireClient:** Fires the event on the client side. You can pass any data as arguments to the connected functions.
- **FireAllClients:** Fires the event on all clients. You can pass any data as arguments to the connected functions.

## Example Use Cases

In this example use case, we'll create a simple score system where the server keeps track of the player's score and updates it when the player collects a coin.

**ScoreSystem.lua**
```lua
local GetMyScoreRequest = Event.new("GetMyScoreRequest")
local GetMyScoreResponse = Event.new("GetMyScoreResponse")
local UpdateMyScoreRequest = Event.new("UpdateMyScoreRequest")

local players = {} -- Store players

-- Function to track players and initialize their scores
function TrackPlayers(game)
  game.PlayerConnected:Connect(function(player)
      -- Initialize player info with score set to 0
      players[player.name] = {
        player = player,
        score = 0
      }
  end)
end

-- Function to add score to a specific player
AddScore = function(target, scoreToAdd)
  local player = client.localPlayer
  -- Ensure the target player matches the local player
  if player ~= target then return end

  -- Retrieve player info
  local playerInfo = players[player.name]

  -- Calculate new score
  local newScore = playerInfo.score + scoreToAdd

  -- Update the player's in the client storage
  playerInfo.score = newScore

  -- Send the score update request to the server
  UpdateMyScoreRequest:FireServer(scoreToAdd)
end

-- Function to handle client initialization
function self:ClientAwake()
  -- Track players on the client side
  TrackPlayers(client)

  -- Request the player's score from the server
  GetMyScoreRequest:FireServer()

  -- Listen for the response from the server
  GetMyScoreResponse:Connect(function(player, score)
    local playerInfo = players[player.name]
    playerInfo.score = score

    print("My score is: " .. playerInfo.score)
  end)
end

-- Function to handle server initialization
function self:ServerAwake()
  -- Track players on the server side
  TrackPlayers(server)

  -- Listen for score requests from clients
  GetMyScoreRequest:Connect(function(player)
    -- Retrieve the player's score from the storage, assuming you have a storage system
    Storage.GetPlayerValue(player, "score", function(score)
      -- Check if the score is nil (player not found in storage)
      if score == nil then score = 0 end

      -- Update the player's score in the local storage
      players[player.name] = score

      -- Send the player's score back to the client
      GetMyScoreResponse:FireClient(score)
    end)
  end)

  -- Listen for score update requests from clients
  UpdateMyScoreRequest:Connect(function(player, scoreToAdd)
    -- Retrieve the player's info
    local playerInfo = players[player.name]

    -- Update the player's score
    playerInfo.score = playerInfo.score + scoreToAdd

    -- Update the score in the storage, assuming you have a storage system
    Storage.IncrementPlayerValue(player, "score", scoreToAdd)

    -- Print the updated score
    print(player.name .. " collected a coin! New score: " .. playerInfo.score)
  end)
end
```

In this example, the server keeps track of the player's score and updates it when the player collects a coin. The client requests the player's score from the server, and the server responds with the player's score. When the player collects a coin, the client sends a score update request to the server, which updates the player's score and stores it in the storage system.

<Note type="warning">
In the example above, we assume the script type is a `Module` script. Which allow us to use the `AddScore` function in different scripts.
</Note>

Assuming you have a script that handles the coin collection, let's say `CoinCollector` that has `OnTriggerEnter` function to detect when the player collects a coin. You can call the `AddScore` function from the `CoinCollector` script to update the player's score when a coin is collected.

**CoinCollector.lua**
```lua
-- Require the module script that contains the AddScore function, in this case, the ScoreSystem module script
local ScoreSystem = require("ScoreSystem")

-- Function to handle trigger enter event
function self:OnTriggerEnter(other : Collider)
  -- Get the character component of the collider's game object
  local playerCharacter = other.gameObject:GetComponent(Character)

  -- If there is no character component, return
  if playerCharacter == nil then return end

  -- Retrieve the player associated with the character
  local player = playerCharacter.player

  -- Check if the local player triggered the checkpoint
  if client.localPlayer == player then
    -- Call the AddScore function to update the player's score
    ScoreSystem.AddScore(player, 10) -- Add 10 points to the player's score
  end
end
```

In this example, the `CoinCollector` script detects when the player collects a coin and calls the `AddScore` function from the `ScoreSystem` module script to update the player's score by 10 points.

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