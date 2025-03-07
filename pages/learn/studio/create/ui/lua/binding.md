# Bindings in Highrise Studio UI

## Introduction

**Bindings** allow Lua scripts to reference and interact with **UI elements** from UXML. They are essential for updating UI dynamically, handling interactions, and modifying properties.

## Binding Syntax

To bind a UI element from **UXML to Lua**, use the `--!Bind` keyword.

### Example: Binding a Button and Label
```xml
<!-- UXML -->
<Button name="_button" />
    <Label name="_label" text="Button not clicked" />
</Button>
```
```lua
--!Bind
local _button : Button = nil
--!Bind
local _label : Label = nil

_button:RegisterPressCallback(function()
    _label.text = "Button Clicked!"
end)
```
- The `--!Bind` keyword links `_button` and `_label` to elements in UXML.
- When the button is pressed, the label text updates dynamically.

## Naming and Referencing UI Elements

Bindings **must match** the corresponding **UXML element type**.

| UXML Element         | Binding Type   |
|----------------------|---------------|
| `<hr:UILabel />`    | `UILabel`      |
| `<hr:UIButton />`   | `UIButton`     |
| `<hr:UIScrollView />` | `UIScrollView` |
| `<VisualElement />` | `VisualElement` |
| `<Image />`         | `Image`        |

### Example: Binding a UIScrollView
```lua
--!Bind
local _playerList : UIScrollView = nil
```
- `_playerList` now references the **UIScrollView** in UXML.
- You can modify or add elements dynamically.

## Unique Names for Bindings

- **Each bound UI element must have a unique name.**  
- If two elements share the same binding name, the script **may not function correctly**.
- Names should be **clear and descriptive**.

✔ **Good Example**
```lua
--!Bind
local _chatWindow : VisualElement = nil
```
❌ **Bad Example**
```lua
--!Bind
local _element : VisualElement = nil
--!Bind
local _element : VisualElement = nil  -- Duplicate name
```

## Using VS Code Studio Tools for Bindings

**Installing the Highrise Studio Tools extension in VS Code** makes working with bindings easier.

### Benefits:
- Displays **available UI methods** for each element.
- Provides **auto-completion** for UI properties and functions.
- Helps avoid **binding errors** by showing valid element types.

To install:
1. Open **VS Code**.
2. Go to **Extensions** (`Ctrl+Shift+X`).
3. Search for **"Highrise Studio Tools"** and install it.

<Note type="info">
After installing, hover over a bound element in Lua to see its available methods.
</Note>

## Conclusion

Bindings are crucial for **interacting with UI elements** in Highrise Studio. By following the correct syntax and naming conventions, you can create dynamic and responsive UIs in your Lua scripts.