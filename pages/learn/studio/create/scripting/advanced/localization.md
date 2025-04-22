# Localization Guide

## Introduction

Localization in Highrise allows you to create multilingual experiences for your world. This guide will show you how to properly implement localization using the actual working examples from the codebase.

## Accessing the Localization Editor

1. Open the **Localization Editor** by navigating to the **Highrise** menu and selecting **Studio > Localization Editor**.
2. The editor provides a user-friendly interface for managing all your localized strings.

## Creating New Localization Strings

### Using the Localization Editor

1. In the Localization Editor, click the **+** button in the bottom-right corner to add a new string.
2. Fill in the following fields:
   - **Key**: A unique identifier for the string (e.g., `welcomeUI_welcome_desc1`)
   - **Text**: The actual string content
   - **Placeholders**: Use `{{$1}}`, `{{$2}}`, etc. for dynamic values

<Note type="warning">
The key must be unique and cannot contain spaces or special characters. Use consistent naming conventions (e.g., `uiName_element_purpose`).
</Note>

### Manual String Creation

You can also add strings directly to the `LocalizationStrings.hrstrings` file:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<resources>
  <string name="welcomeUI_welcome_desc1">Challenge other players! Sit at a table and join the prize pool to play!</string>
  <string name="welcomeUI_welcome_desc2">Daub the numbers in time to win Free Daub Powerups! Place them Strategically to win!</string>
</resources>
```

## Adding Languages

### Supported Languages

Highrise supports the following languages and their corresponding codes:

- **en**: English
- **de**: German  
- **es**: Spanish  
- **fr**: French  
- **hi**: Hindi  
- **it**: Italian  
- **zh**: Chinese (Simplified)  
- **ja**: Japanese  
- **ko**: Korean  
- **nl**: Dutch  
- **ru**: Russian  
- **ar**: Arabic  
- **fa**: Persian  
- **pt-BR**: Portuguese (Brazilian)  
- **pt-PT**: Portuguese (European)  
- **tr**: Turkish

### Adding a New Language

1. Make a copy of `LocalizationStrings-en.stringtable`
2. Rename the file, replacing `en` with the language code (e.g., `de` for German)
3. Select the file in Unity and change the **System Language** in the Inspector to the corresponding language
4. Open the file in a text editor and replace the text for each string with the translated version

<Note type="info">
If a player's Highrise app language doesn't have a corresponding file, the English version will be used as the default.
</Note>

## Localized UI Components

### UILocalizedLabel

The most common component for displaying localized text:

```xml
<hr:UILocalizedLabel name="_desc1" key="welcomeUI_welcome_desc1" picking-mode="Ignore"/>
```

### UILocalizedButton

For buttons with localized text:

```xml
<hr:UILocalizedButton name="_nextButton" key="welcomeUI_welcome_next_button">
  <hr:UILocalizedLabel name="_nextButtonLabel" class="buttonLabel wrap"/>
</hr:UILocalizedButton>
```

### UILocalizedTextField

For input fields with localized placeholder text:

```xml
<hr:UILocalizedTextField name="_inputField" key="welcomeUI_input_placeholder"/>
```

## Implementing Localization in UI

### UXML Implementation

The proper way to implement localized text in UXML is using the `hr:UILocalizedLabel` element:

```xml
<hr:UILuaView class="welcome-popup">
  <hr:UILocalizedLabel name="_desc1" key="welcomeUI_welcome_desc1"/>
  <hr:UILocalizedLabel name="_desc2" key="welcomeUI_welcome_desc2"/>
</hr:UILuaView>
```

Key attributes:
- `name`: The identifier for the label in Lua
- `key`: The localization key from the strings file

### Lua Implementation

In Lua, you can set localized text in several ways:

1. Using the `Strings` global with `SetText`:
```lua
--!Bind
local _desc1 : UILocalizedLabel = nil

function self:ClientStart()
    _desc1:SetText(Strings.welcomeUI_welcome_desc1)
end
```

2. Using dynamic values with placeholders:
```lua
-- Example from ScoreHud.lua
game_state_label:SetText(Strings.scoreHud_waiting_players, playerTracker.GetReadyPlayerCount())
```

<Note type="info">
You don't need to use `SetText` for `hr:UILocalizedLabel` elements in UXML. The localization system automatically binds the text when the UI is loaded unless you have dynamic values to set.
</Note>

## Best Practices

### Naming Conventions

1. Use consistent prefixes for related strings:
   - `welcomeUI_` for welcome screen strings
   - `scoreHud_` for score HUD strings
   - `leaderboardUI_` for leaderboard strings

2. Use descriptive suffixes:
   - `_title` for titles
   - `_desc` for descriptions
   - `_button` for button text

### Placeholder Usage

1. Use `{{$1}}` format for placeholders:
```xml
<string name="scoreHud_waiting_players">Waiting for players: {{$1}} / 2</string>
```

2. Pass values in order:
```lua
-- Correct
label:SetText(Strings.key_name, value1, value2)

-- Incorrect
label:SetText(Strings.key_name, value2, value1)
```

## Common Patterns

### Button Text

```xml
<hr:UIButton name="_nextButton">
  <hr:UILocalizedLabel name="_nextButtonLabel" class="buttonLabel wrap" key="welcomeUI_welcome_next_button"/>
</hr:UIButton>
```

### Dynamic State Updates

```xml
<string name="scoreHud_waiting_players">Waiting for players: {{$1}} / 2</string>
<string name="scoreHud_players_ready">Players ready: {{$1}} / 2</string>
```

```lua
function UpdateGameState(state)
    if state == 1 then
        game_state_label:SetText(Strings.scoreHud_waiting_players, playerCount)
    elseif state == 2 then
        game_state_label:SetText(Strings.scoreHud_players_ready, playerCount)
    end
end
```

<Note type="warning">
The `{{$1}}` placeholder must match the order of values passed in the Lua function. Ensure that the number of placeholders matches the number of values provided.
</Note>

## Testing and Maintenance

1. Always test with different languages to ensure:
   - Text fits within UI elements
   - Placeholders are correctly positioned
   - Special characters display properly

2. Keep string files organized:
   - Group related strings together
   - Use consistent naming conventions
   - Document any special formatting requirements

3. When adding new strings:
   - Add to all language files
   - Test placeholder functionality
   - Verify UI layout with different text lengths

## Conclusion

Proper localization implementation requires attention to detail in both the UI and code. By following these patterns and best practices, you can create a robust multilingual experience for your world. Remember to test thoroughly with different languages and text lengths to ensure a consistent user experience across all supported languages.
