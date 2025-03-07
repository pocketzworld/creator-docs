# Overview of Lua in Highrise Studio UI

## Introduction

In **Highrise Studio**, **Lua** is used to bring UI elements to life by:
- Handling **button interactions**.
- Modifying and updating **UXML elements** dynamically.
- Changing **styles and visibility**.
- Creating and managing **custom UI components**.

This guide provides an overview of how Lua is integrated with **UXML and USS** to build functional and interactive UI elements.

## How Lua Works with UI

<Note type="info">
The UI Lua file is a client side script and cannot access server side scripts or data.
</Note>

Lua allows interaction with **UI elements** through:
- **Binding UI components** from UXML.
- **Creating UI elements dynamically**.
- **Registering user interactions** (e.g., button clicks).
- **Modifying styles and visibility** in real time.

### Example: Binding UI Components

To modify a UI element in Lua, it must be **bound** using the `--!Bind` keyword.

```lua
--!Bind
local _button : VisualElements = nil
--!Bind
local _label : Label = nil

_button:RegisterPressCallback(function()
    _label.text = "Button Clicked!"
end)
```
- `_button` and `_label` are linked to UXML elements.
- When the button is clicked, the label text updates dynamically.

## Creating UI Elements in Lua

Instead of pre-defining UI elements in UXML, Lua can **create and manage UI components dynamically**.

### Example: Creating a Player Card
```lua
function CreatePlayerCard(playerName: string, playerId: string)
    local _player_element = VisualElement.new()
    _player_element:AddToClassList("player-element")

    local _player_name = Label.new()
    _player_name.text = playerName
    _player_element:Add(_player_name)

    return _player_element
end
```
- This function **creates a new UI element** (`VisualElement`) for a player.
- A `Label` is added to display the player’s name.

To **add this UI to the scene**, use:
```lua
--!Bind
local _playerlistContainer : UIScrollView = nil -- Container for player cards

local playerCard = CreatePlayerCard("Alice", "12345")
_playerlistContainer:Add(playerCard)
```
This will insert the player card into a **UIScrollView container**.

## Handling UI Interactions

Lua provides **callback functions** to handle user interactions.

### Example: Registering a Button Click
```lua
_button:RegisterPressCallback(function()
    print("Button Pressed!")
end)
```
This runs a function whenever the button is clicked.

### Example: Closing a UI Window
```lua
_closeButton:RegisterPressCallback(function()
    self.gameObject:SetActive(false)
end)
```
This **hides the UI** when the close button is pressed.

## Modifying Styles and Layouts in Lua

Lua can also change **USS classes dynamically**.

### Example: Adding and Removing a Class
```lua
local _element = VisualElement.new()
_element:AddToClassList("highlighted")

Timer.After(2, function()
    _element:RemoveFromClassList("highlighted")
end)
```
- The UI element gets the `highlighted` class.
- After **2 seconds**, the class is removed.

## Using Timers and Delayed Execution

Lua allows you to delay actions using `Timer.After()`.

### Example: Delaying UI Initialization
```lua
Timer.After(1, function()
    InitializeUI()
end)
```
This ensures that UI components **load properly** before running certain scripts.

## Conclusion

**Lua** in **Highrise Studio** is a powerful tool for creating interactive and dynamic UI elements. By binding UI components, handling interactions, and modifying styles, you can build **rich and responsive user interfaces**.