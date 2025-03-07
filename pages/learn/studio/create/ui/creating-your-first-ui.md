# Beginner's Guide to Creating UI in Highrise Studio

## Introduction

This guide will walk you through creating a simple UI in **Highrise Studio** using **UXML for structure**, **USS for styling**, and **Lua for interactivity**. The example will feature a button that increments a counter when clicked.

## Step 1: Generate UI Components

1. **Create a new UI component**  
   - In Unity’s **Project window**, go to `Create > Lua > UI`.
   - This generates three files:
     - **Lua script** (logic)
     - **UXML file** (layout)
     - **USS file** (styling)
   - A **UI Visual Tree Factory** is also created in the root of your assets.

<Note type="warning">
Your project must have a **UI Tree** to display UI. This is included when you create a UI component.
</Note>

## Step 2: Set Up the UI in the Scene

1. **Create an empty GameObject**  
   - Right-click the **Hierarchy window** → `Create Empty`.
   - Rename it (e.g., `MyUI`).
2. **Attach the UI Lua script**  
   - Drag the Lua script onto the GameObject.
3. **Choose a UI Output Mode**  
   - The script’s **Output** property defines where the UI appears:
     - **World** – UI attaches to a 3D object (not interactive).
     - **Above Chat** – UI floats above the chat box.
     - **HUD** – UI is fixed on the screen.
4. **Set the output mode** to the desired display setting.

<Note type="info">
**Important:** The **World mode** does not support buttons or input fields. Use **Above Chat** or **HUD** for interactive elements.
</Note>

## Step 3: Define UI Layout (UXML)

Now, let's create a UI with a **label** and a **button**.

### Example (UXML)
```xml
<hr:UILuaView class="mini-game">
    <hr:UILabel class="mini-game__counter" name="_counterLabel" picking-mode="Ignore" />
    <VisualElement class="mini-game__buttons">
        <hr:UIButton class="secondary-button" name="_Button">
            <Label text="Click me!" />
        </hr:UIButton>
    </VisualElement>
</hr:UILuaView>
```
- `UILuaView` is the root container for the UI.
- `_counterLabel` displays the count.
- `_Button` is the interactive button.
- `picking-mode="Ignore"` ensures the label does not intercept input.

## Step 4: Style UI Components (USS)

### Example (USS)
```css
.mini-game {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    height: 100%;
    -unity-font-definition: var(--font-regular);
}

.mini-game__counter {
    font-size: 70px;
    color: white;
    text-shadow: 2px 2px 0px rgba(0, 0, 0, 0.5);
    margin-bottom: 20px;
}

.mini-game__buttons {
    display: flex;
    justify-content: center;
}

.secondary-button:hover {
    background-color: rgba(0, 255, 0, 0.4);
}
```
- The `.mini-game` class centers the UI elements.
- `.mini-game__counter` styles the label with large, readable text.
- `.mini-game__buttons` ensures the button is properly aligned.
- The `:hover` effect changes the button color when hovered.

## Step 5: Add Interactivity with Lua

Now, let's make the button functional by binding it in the Lua script.

### Example (Lua)
```lua
--!Type(UI)

--!Bind
local _counterLabel : UILabel = nil
--!Bind
local _Button : UIButton = nil

local counter = 0 -- Initialize the counter

_Button:RegisterPressCallback(function()
    counter = counter + 1
    _counterLabel:SetPrelocalizedText(tostring(counter)) -- Update label text
end)
```
- `_counterLabel` binds to the label in UXML.
- `_Button` binds to the button.
- Clicking the button **increments the counter** and updates the label.

<Note type="info">
Ensure variable names in Lua **match** the UXML element names.
</Note>

## Step 6: Test Your UI

1. Click the **Play** button in Unity.
2. Check that the UI appears correctly.
3. Click the button to confirm the counter updates.

## Conclusion

Congratulations! You’ve successfully created a simple UI in **Highrise Studio** using UXML, USS, and Lua. This example demonstrates the basic workflow for creating UI components, styling them, and adding interactivity.