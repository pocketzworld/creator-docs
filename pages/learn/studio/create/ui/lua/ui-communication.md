# UI Communication

## Introduction

Connecting **UI elements with game logic** is essential for creating interactive experiences. This guide explains **how to manage UI interactions** by using a **UI Manager script** as a bridge between the **UI and game logic**.

By the end of this guide, you will:
- Learn how to **create a UI Manager** to handle UI interactions.
- Understand how to **toggle UI visibility dynamically**.
- See a **real-world example** of updating UI elements based on game events.

## Creating a UI Communication Script

A **UI Manager** acts as an intermediary between UI elements and game logic.

### **Step 1: Create a UI Manager Script**
1. Create a new **Lua module script** in the **Scripts** folder.
2. Name it **UIManager.lua**.

<Note type="info">
You must assign the **UI GameObjects** to the **UIObjects** array in the **UIManager** script.
</Note>

### **UIManager.lua**
```lua
--!Type(Module)

-- Store references to UI GameObjects
--!SerializeField
local UIObjects : { GameObject } = {}

-- Define UI indexes for quick access
local Indexes = { WorldHUD = 1, TipJar = 2 } -- Add more UI components as needed

-- Create UI maps for easy access
local UIMap = {}
for key, index in pairs(Indexes) do
    UIMap[key] = UIObjects[index] -- Map UI names to their corresponding objects
end

local UIScriptMap = {} -- Stores UI scripts for each component

-- Table of available button actions
local actions = {}

-- Helper function: Activate or deactivate a UI object
local function ActivateObject(object: GameObject, activate: boolean)
  if not object then
    print("[ERROR] [ActivateObject] Object is nil")
    return
  end
  object:SetActive(activate)
end

-- Helper function: Toggle visibility of a specific UI component
local function ToggleUI(ui: string, visible: boolean)
  local uiComponent = UIMap[ui]
  if uiComponent then
    ActivateObject(uiComponent, visible)
  else
    print("[ToggleUI] No UI found for: " .. ui)
  end
end

-- Helper function: Toggle visibility for multiple UI components
local function ToggleUIs(uis: { string }, visible: boolean, except: string)
  for _, ui in ipairs(uis) do
    if ui ~= except then
      ToggleUI(ui, visible)
    end
  end
end

-- Define button actions
actions.ToggleWorldHUD = function()
  -- Prevent toggling if the UI is already active
  if UIObjects[Indexes.WorldHUD].activeSelf then return end

  -- Hide other UI elements
  ToggleUIs({ "WorldHUD" }, false)

  -- Get the script for WorldHUD and initialize it
  local worldHUDScript = UIScriptMap["WorldHUD"] or UIMap["WorldHUD"]:GetComponent(WorldHud)
  if worldHUDScript then
    worldHUDScript.Initialize()
  end
end

actions.Close = function()
  -- Hide the "TipJar" UI, but keep "WorldHUD" visible
  ToggleUIs({ "TipJar" }, false, "WorldHUD")
end

-- Main function to handle button presses
function ButtonPressed(btn: string)
  if actions[btn] then
    actions[btn]()
  else
    print("[ButtonPressed] No action found for button: " .. btn)
  end
end
```

## Connecting UI Manager to Game Logic

Now that we have the **UIManager**, we can require it in other scripts to interact with the UI.

### **Example: Calling Button Actions from Game Logic**
```lua
--!Type(Client)
local UIManager = require("UIManager")

-- Call the action for the "ToggleWorldHUD" button
UIManager.ButtonPressed("ToggleWorldHUD")
```
- This calls the **ToggleWorldHUD** function inside `UIManager`, making the UI appear.
- You can call **any registered button action** the same way.

## Real-World Example: Updating UI Elements

In some cases, you might want to update UI elements dynamically, such as updating the **player’s score**.

### **Step 1: Add an Update Function to UIManager**
Modify the **UIManager** script to include an `UpdateScore` function.

```lua
function UpdateScore(score: number)
  -- Get the WorldHUD script and update the score
  local worldHUDScript = UIScriptMap["WorldHUD"] or UIMap["WorldHUD"]:GetComponent(WorldHud)

  if worldHUDScript then
    worldHUDScript.UpdateScore(score)
  end
end
```

### **Step 2: Call the Function from Game Logic**

Modify the **GameLogic** script to update the score.

```lua
--!Type(Module)
local UIManager = require("UIManager")

local score = 0

function UpdateScore()
  score = score + 1
  UIManager.UpdateScore(score) -- Send the new score to UIManager
end
```
- Every time `UpdateScore()` is called, the UI **updates the player's score**.

### **Step 3: Display the Score in the UI**
Now, update the **WorldHUD** script to display the score.

```lua
--!Type(UI)

--!Bind
local scoreText : Label = nil -- UI Label for displaying the score

function UpdateScore(score: number)
  scoreText.text = score -- Set the label text to the updated score
end
```

Now, every time the game logic updates the score, it **automatically updates in the UI**.

## Conclusion

By using a **UI Manager**, you can:
- **Easily manage UI interactions** with a single script.  
- **Toggle UI elements dynamically** with helper functions.  
- **Keep UI logic separate from game logic**, making it easier to maintain.  
- **Update UI elements like scores dynamically** from game scripts.  

This approach **organizes your UI interactions** and makes your game **more modular and scalable**.