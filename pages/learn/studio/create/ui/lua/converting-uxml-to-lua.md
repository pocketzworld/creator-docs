# Converting UXML to Lua

## Introduction

In **Highrise Studio**, **UXML** defines UI structure, while **Lua** enables dynamic creation, styling, and interaction.  

## Creating UI Elements in Lua

Instead of defining all UI elements in **UXML**, you can **create them dynamically in Lua**.

### Example: Creating a UI Button in Lua
```lua
local _button = Button.new() -- Or VisualElement.new()
_button:AddToClassList("custom-button")
```
- `UIButton.new()` creates a new button.
- `.AddToClassList()` applies a USS class.

To **add the button to an existing container**, use:
```lua
_container:Add(_button)
```

### Example: Creating a UI Label
```lua
local _label = Label.new()
_label.text = "Hello, World!"
_label:AddToClassList("custom-label")

_container:Add(_label)
```
- `Label.new()` creates a text label.
- `.text` sets the label’s content.

## Adding and Removing Classes Dynamically

USS classes can be **added and removed dynamically** in Lua.

### Example: Highlighting an Element
```lua
_label:AddToClassList("highlighted")

Timer.After(3, function()
    _label:RemoveFromClassList("highlighted")
end)
```
- The **`highlighted`** class is added.
- After **3 seconds**, the class is removed.

### Example: Toggling a Selected State
```lua
_button:RegisterPressCallback(function()
    if _button:ClassListContains("selected") then
        _button:RemoveFromClassList("selected")
    else
        _button:AddToClassList("selected")
    end
end)
```
- Clicking the button toggles the **`selected`** class.

## Connecting UI Elements Together

You can **link multiple UI elements** to interact dynamically.

### Example: Updating a Label with Button Click
```lua
--!Bind
local _button : Button = nil
--!Bind
local _label : Label = nil

_button:RegisterPressCallback(function()
    _label.text = "Button Clicked!"
end)
```
- The **button click** updates the label text.

## Creating Lists and Adding Elements Dynamically

Lists can be **populated dynamically** using Lua.

### Example: Creating a Scrollable List
```lua
--!Bind
local _listContainer : UIScrollView = nil

function CreateListItem(text)
    local _item = VisualElement.new()
    _item:AddToClassList("list-item")

    local _label = Label.new()
    _label.text = text
    _item:Add(_label)

    return _item
end

function PopulateList(items)
    for _, itemText in ipairs(items) do
        _listContainer:Add(CreateListItem(itemText))
    end
end

PopulateList({"Option 1", "Option 2", "Option 3"})
```
- `CreateListItem()` generates list items.
- `PopulateList()` dynamically adds them to a **UIScrollView**.

## Conclusion

**Lua** provides a powerful way to **create, style, and interact with UI elements** in **Highrise Studio**. By combining Lua with UXML, you can build dynamic and responsive user interfaces.