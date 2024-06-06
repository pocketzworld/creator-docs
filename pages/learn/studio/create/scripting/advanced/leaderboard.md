# Leaderboard

## Introduction

Leaderboards are a common feature in games that display the top scores of players, allowing them to compete with each other and track their progress. In Highrise, you can create leaderboards to showcase the achievements of players in your worlds.

## Create a Leaderboard in Your World

1. Right-click in the Hierarchy window and select `Empty Object`
2. Give the object a name (e.g., `Leaderboard`)
3. Right-click in the Project window and select `Create > Lua > UI`
4. Name the UI script (e.g., ranking`)
5. Drag and drop the UI script onto the `Leaderboard` object in the Hierarchy window
6. Set the Output to `World` in the Inspector
7. Change the scale and position of the object to fit your world

<Note type="info">
  When you create a new UI script, it will automatically generate a UXML, USS, and Lua file.
  The UXML file defines the layout of the UI elements, the USS file styles the UI elements, and the Lua file contains the logic for the UI.
</Note>

## Write Lua Script for Leaderboard

To make life easier, you can create 2 separate modules for the leaderboard: one for tracking player scores and another for communicating with the UI.

### 1. Create Player Tracker Module

The player tracker module will keep track of player scores and update the leaderboard accordingly.

1. Right-click in the Project window and select `Create > Lua > Module`
2. Name the module (e.g., `PlayerTracker`)
3. Create an empty object in the Hierarchy window and attach the `PlayerTracker` module to it
4. Write the following code inside the `PlayerTracker` module:

```lua
--!Type(Module)

-- Event for requesting top players list from server
local GetTopPlayersRequest = Event.new("GetTopPlayersRequest") 
-- Event for receiving top players list from server
local GetTopPlayersResponse = Event.new("GetTopPlayersResponse") 

local players = {} -- Table to store player scores
local topPlayers = {} -- Table to store top players

-- Function to track players when they connect to the game
function TrackPlayers(game)
  game.PlayerConnected:Connect(function(player)
    -- Initialize player info with score set to 0
    players[player.name] = {
      player = player,
      score = 0
    }
  end)
end

-- Function to get and sort top players list
GetTopPlayers = function()
  -- Sort top players list
  if topPlayers ~= nil and #topPlayers > 0 then
    table.sort(topPlayers, function(a, b)
      return a.score > b.score
    end)
  end

  return topPlayers
end

-- Function to handle client initialization
function self:ClientAwake()
  -- Track players when client initializes
  TrackPlayers(client)

  -- Request the top players from the server when the client initializes
  GetTopPlayersRequest:FireServer()

  -- Handle response from server containing top players list
  GetTopPlayersResponse:Connect(function(newTopPlayers)
    -- Override the local top players list with the updated list from the server
    topPlayers = newTopPlayers
  end)
end

-- Function to handle server initialization
function self:ServerAwake()
  -- Track players when server initializes
  TrackPlayers(server)

  -- Retrieve the top players list from storage
  Storage.GetValue("TopPlayers", function(oldList)
    if oldList == nil then oldList = {} end
    topPlayers = oldList
  end)

  -- Handle request for top players list from client
  GetTopPlayersRequest:Connect(function()
    -- Retrieve the top players list from storage
    Storage.GetValue("TopPlayers", function(oldList)
      if oldList == nil then oldList = {} end
      topPlayers = oldList

      -- Send the top players list to the client
      GetTopPlayersResponse:FireAllClients(topPlayers)
    end)
  end)
end
```

<Note type="warning">
The example above doesn't have a complete implementation of the individual player score tracking. You will need to implement the logic to update player scores based on player actions in your world. See the example below for a simple implementation.
</Note>

Assuming you have a function to update player scores based on player actions, you can update the top players list as follows:

```lua
-- Update top players list
local playerEntry = { name = player.name, score = newScore }

-- Check if the player is already in the top players list
local found = false
for i = 1, #topPlayers do 
  if topPlayers[i].name == player.name then
    topPlayers[i] = playerEntry
    found = true
    break
  end
end

-- If the player is not in the top players list, add them
if not found then
  table.insert(topPlayers, playerEntry)
end

-- Update the top players list on all clients
GetTopPlayersResponse:FireAllClients(topPlayers) 
-- Save the updated top players list to storage
Storage.SetValue("TopPlayers", topPlayers)
```

### 2. Write UXML Script for Leaderboard

```xml
<?xml version="1.0" encoding="utf-8"?>
<UXML
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="UnityEngine.UIElements"
    xmlns:hr="Highrise.UI"
    xmlns:editor="UnityEditor.UIElements"
    xsi:noNamespaceSchemaLocation="../../../../../UIElementsSchema/UIElements.xsd">

  <hr:UILuaView class="ranking">
    <VisualElement class="header">
        <Label class="title" text="Global Leaderboard" />
        <Label class="update" text="Updates every 5 seconds" />
    </VisualElement>
    <VisualElement class="content" name="_content">
      <VisualElement class="rank-list" name="_ranklist">
        <!-- Rank Items will be added here -->
      </VisualElement>
    </VisualElement>
  </hr:UILuaView>
</UXML>
```

### 3. Write USS Script for Leaderboard

```css
* {
  padding: 0;
  margin: 0;
  flex-shrink: 0;
  overflow: hidden;
}

.ranking {
  flex-grow: 1;
  display: flex;
  flex-direction: column;
  padding: 20px;
  background-color: rgba(0, 0, 0, 0.5);
  -unity-font-definition: var(--font-regular);
  height: 100%;
  width: 100%;
  border-radius: 12px;
}

.ranking .header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  align-self: center;
  color: #ac9d5b;
  text-shadow: 2px 2px 0px rgba(0, 0, 0, 0.5);
  margin-bottom: 20px;
}

.header .title {
  font-size: 75px;
}

.header .update {
  font-size: 40px;
}

.ranking .content {
  display: flex;
  align-items: center;
  width: 100%;
  height: 100%;
  padding: 20px;
  text-shadow: 2px 2px 0px rgba(255, 255, 255, 0.5);
}

.content .rank-list {
  width: 100%;
  font-size: 35px;
}

.content .rank-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  padding: 10px;
  margin-bottom: 15px;
  border-radius: 10px;
  color: #ac9d5b;
  background-color: rgba(0, 0, 0, 0.1);
}

.rank-item .name-label {
  flex-grow: 1;
  margin-left: 20px;
}

.first {
  font-size: 60px;
}

.second {
  font-size: 50px;
}

.third {
  font-size: 40px;
}
```

### 4. Update Lua Script for Leaderboard

In our Lua script, we will create a function to update the leaderboard UI with the top players list. The leaderboard will display top 8 players based on their scores and it will update every 5 seconds.

<Note type="warning">
In the example below, the players table and score are hardcoded for demonstration purposes. You should replace this with the actual player data and scores from the player tracker module.
</Note>

```lua
--!Type(UI)

--!Bind
local _content : VisualElement = nil
--!Bind
local _ranklist : VisualElement = nil

-- Require the PlayerTracker module
local playerTracker = require("PlayerTracker")

-- Function to update the leaderboard UI with the top players list
function UpdateLeaderboard(players)
  _ranklist:Clear() -- Clear the current leaderboard

   if not players or #players == 0 then return end -- Return if there are no players

   local count = #players -- Get the number of players
   if count > 8 then count = 8 end -- Display only the top 8 players

   for i = 1, count do
    -- Create a rank item for each player
    local _rankItem = VisualElement.new()
    _rankItem:AddToClassList("rank-item")

    local entry = players[i] -- Get the player entry

    local name = entry.name -- Get the player name
    local score = entry.score -- Get the player score

    -- Create a label for the player rank
    local _rankLabel = UILabel.new()
    _rankLabel:SetPrelocalizedText("#" .. i)
    _rankLabel:AddToClassList("rank-label")

    -- Create a label for the player name
    local _nameLabel = UILabel.new()
    _nameLabel:SetPrelocalizedText(name)
    _nameLabel:AddToClassList("name-label")

    -- Create a label for the player score
    local _scoreLabel = UILabel.new()
    _scoreLabel:SetPrelocalizedText(tostring(score))
    _scoreLabel:AddToClassList("score-label")


    -- Add the labels to the rank item
    _rankItem:Add(_rankLabel)
    _rankItem:Add(_nameLabel)
    _rankItem:Add(_scoreLabel)

    -- Add the placement class based on the rank
     if i == 1 then
      _rankItem:AddToClassList("first")
    elseif i == 2 then
      _rankItem:AddToClassList("second")
    elseif i == 3 then
      _rankItem:AddToClassList("third")
    end

    -- Add the rank item to the rank list
    _ranklist:Add(_rankItem)

   end
end

local cooldown = 5 -- Update every 5 seconds
local timer = 0 -- Timer to keep track of the time

local players = {
  { name = "Player1", score = 100 },
  { name = "Player2", score = 90 },
  { name = "Player3", score = 80 },
  { name = "Player4", score = 70 },
  { name = "Player5", score = 60 },
  { name = "Player6", score = 50 },
  { name = "Player7", score = 40 },
  { name = "Player8", score = 30 }
}

-- Function to update the leaderboard
function self:ClientUpdate()
  timer = timer + Time.deltaTime -- Increment the timer
  if timer >= cooldown then
    -- Generate random scores for demonstration purposes
    for i = 1, #players do
      players[i].score = math.random(1, 100)
    end

    -- Sort the players table based on scores
    table.sort(players, function(a, b)
      return a.score > b.score
    end)

    -- Update the leaderboard UI with the top players list
    UpdateLeaderboard(players)

    timer = 0 -- Reset the timer
  end
end
```

### Test Your Leaderboard

Now that you have created the player tracker module and the leaderboard UI, you can test your leaderboard by running your world in Unity. The leaderboard will be updated every 5 seconds with the top 8 players based on their scores.

## Conclusion

Leaderboards are a great way to engage players and encourage competition in your worlds. By implementing a leaderboard system, you can showcase the achievements of players and create a sense of accomplishment for those who reach the top. Experiment with different leaderboard designs and features to enhance the player experience and keep them coming back for more!