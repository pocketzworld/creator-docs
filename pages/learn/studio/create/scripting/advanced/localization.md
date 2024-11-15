# Localization

## Introduction

Localization is the process of adapting your world to different languages and regions. By localizing your world, you can reach a wider audience and provide a more inclusive experience for players around the world. This guide will show you how to add localized text to your world and use it in your UIs.

## Adding Localizable Text

### Accessing the Localization Editor

1. Open the **Localization Editor** by navigating to the **Highrise** menu and selecting **Studio > Localization Editor**.
2. Press the **+** button in the bottom-right corner of the window to add a new string.

### Creating a new Localization String

<Note type="warning">
The key must be unique and cannot contain spaces or special characters.
</Note>

- **Key:** The key is how yhou will reference the string in Lua or UXML files.
- **Rich Text Tags:** The text supports rich text tags. For a list of supported tags, refer to [Unity's documentation](https://docs.unity3d.com/2022.3/Documentation/Manual/UIE-supported-tags.html). Buttons for common tags (Bold, Italic, and Color) are available. Highlight text and click a button to apply the tag.
- **Placeholders:** You can add placeholders to the strings for dynamic values(e.g., player names or currency).
  1. Place the cursor in the text where you want the placeholder. 
  2. Right-click and select **Add Parameter**, then choose the parameter slot number.

### Saving Strings

When you save a string for the first time, the following files are created in the `Assets/Localization` folder:
  - `LocalizationDatabase.asset`
  - `LocalizationStrings.hrstrings`
  - `LocalizationStyles.stringstylesheet`
  - `LocalizationStrings-en.stringtable`

The `LocalizationDatabase.asset` will be automatically added to the **Localization Databas** slot in World Settings.

## Adding Languages

### Steps to Add a Language

1. Make a copy of `LocalizationStrings-en.stringtable`.
2. Rename the file, replacing `en` with the language code (e.g., `de` for German).
3. Select the file in Unity and change the **System Language** in the Inspector to the corresponding language.
4. Open the file in a text editor and replace the text for each string with the translated version.

### Supported Languages and Codes

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

### Default Language
If a player's Highrise app language does not have a corresponding file, the English version will be used as the default.

## Using Localized Text in Your World

### Using Localized Text in UI

The following classes are available for localized text in UIs:
- `UILocalizedLabel`
- `UILocalizedButton`
- `UILocalizedTextField`

#### Example: Using `UILocalizedLabel` in UXML
```xml
<hr:UILuaView class="my-hud">
    <hr:UILocalizedLabel name="_testLabel" key="test"/>
</hr:UILuaView>
```

#### Example: Setting Text in Lua
```lua
--!Type(UI)

--!Bind
local _testLabel : UILocalizedLabel = nil

function self:ClientStart()
    -- Using Strings global
    _testLabel:SetText(Strings.test)
    
    -- Using Localization.TryGetString
    local found, text = Localization.TryGetString("test")
    _testLabel:SetText(text)
end
```

### Filling Placeholders
To insert placeholders into localized text, you can:
1. Pass parameters to `SetText`.
2. Use `LocalizedString.Format` to get a string for non-UI purposes.

#### Examples:
```lua
-- Format with player's name
local helloString = Strings.hello_player:Format(client.localPlayer.name)

-- Set text with dynamic values
_testLabel:SetText(Strings.your_coins, currentCoins)
```

### Helper Functions for Placeholders
- **`LocalizedValue.Numeric`**: Adjust the number of decimal places for numbers.
- **Date and Time Formatting**:  
  - `DayAndMonth`, `TimeAgo`, `TimeIn`: Format `os.time()` values.
- **Duration Formatting**:  
  - `TimeSpan`, `TimeLeft`, `HoursMinutesSeconds`: Convert seconds into readable formats.

## Conclusion

By localizing your world, you can provide a more inclusive experience for players around the world. Remember to test your strings in different languages to ensure they display correctly and make sense in context.