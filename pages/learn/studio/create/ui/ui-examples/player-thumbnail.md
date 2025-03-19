# Player Thumbnail Example

## Introduction

Player thumbnails are **small images representing players in a game**. They are commonly used in **leaderboards, chat, and social features** to help players identify each other.

This guide covers how to:
- **Create a player thumbnail** using `UIUserThumbnail` in UXML.
- **Style it with USS**.
- **Handle interactions dynamically using Lua**.

## Creating a Player Thumbnail

In this example, we define a **player thumbnail** in UXML, apply styles in USS, and interact with it in Lua.

### **ThumbnailExample.uxml**
```xml
<?xml version="1.0" encoding="utf-8"?>
<UXML
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns="UnityEngine.UIElements"
    xmlns:hr="Highrise.UI"
    xmlns:editor="UnityEditor.UIElements"
    xsi:noNamespaceSchemaLocation="../../UIElementsSchema/UIElements.xsd"
>

  <hr:UILuaView class="thumbnail-example">
    <VisualElement class="container">
      <hr:UIUserThumbnail class="player-thumbnail" name="_playerThumbnail" online-indicator="false"/>
      <Label class="player-name" name="_playerName" text="Player Name"/>
    </VisualElement>
  </hr:UILuaView>

</UXML>
```
- **`UILuaView`** wraps the UI component.
- **`VisualElement`** (class: `container`) holds the thumbnail and player name.
- **`UIUserThumbnail`** (name: `_playerThumbnail`) is the player thumbnail.
- **`Label`** (name: `_playerName`) displays the player's name.

## Styling the Player Thumbnail

### **ThumbnailExample.uss**
```css
.thumbnail-example {
  display: flex;              /* Uses flexbox for layout */
  position: absolute;         /* Positions element absolutely within its parent */
  
  width: 100%;               /* Takes up full width of parent container */
  height: 100%;              /* Takes up full height of parent container */

  justify-content: center;   /* Centers children horizontally */
  align-items: center;       /* Centers children vertically */

  align-self: center;        /* Centers the entire element within its parent */
}

.container {
  display: flex;             /* Uses flexbox for layout */

  width: 150px;             /* Sets fixed width of 400 pixels */
  height: 150px;            /* Sets fixed height of 100 pixels */

  justify-content: center;  /* Centers children horizontally */
  align-items: center;      /* Centers children vertically */

  flex-direction: column;   /* Arranges children in a vertical row */
  background-color: #333;   /* Sets dark gray background color */

  border-radius: 10px;      /* Rounds corners with 10px radius */
  padding: 10px;            /* Adds 10px internal spacing */

  font-size: 20px;          /* Sets text size to 20 pixels */
  color: white;             /* Sets text color to white */

  -unity-font-definition: var(--font-bold);  /* Uses predefined bold font variable */
  -unity-text-align: middle-center;   /* Aligns text to the center */
}

/* Must call out the specific class to style the thumbnail */
.container .player-thumbnail {
  width: 70px; /* Sets thumbnail width */
  height: 70px; /* Sets thumbnail height */
}

/* built-in classes */
.player-thumbnail .user-thumbnail__image-container {
  /* For extra styling of the thumbnail image */
}
```
- **`.container`** defines the **thumbnail wrapper** with a background, padding, and rounded corners.
- **`.player-thumbnail`** sets the **size of the player thumbnail**.
- **`.user-thumbnail__image-container`** allows further styling of the thumbnail image.

## Handling Interactions in Lua

### **ThumbnailExample.lua**
```lua
--!Type(UI)

--!Bind
local _playerThumbnail : UIUserThumbnail = nil
--!Bind
local _playerName : Label = nil

-- Initialize the player thumbnail
function Initialize()
  _playerThumbnail:Load(client.localPlayer) -- Load local player image
  _playerName.text = client.localPlayer.name -- Set player name
end

-- Dynamically create a player thumbnail
function CreateThumbnail(player_id: string)
  local newThumbnail = UIUserThumbnail.new()
  newThumbnail:AddToClassList("player-thumbnail")
  newThumbnail:Load(player_id)
  newThumbnail.showOnlineIndicator = false -- Hide/Show online indicator
  return newThumbnail
end

-- Run initialization when UI is enabled
function self:OnEnable()
  Initialize()
end
```
- **`Initialize()`** loads the local player's thumbnail and name.
- **`CreateThumbnail(player_id)`** generates a new player thumbnail dynamically.

### **Visual Example**
![Player Thumbnail Example](/assets/learn/guides/studio/UI/ui-examples/player-thumbnail-example.png)

## Conclusion

This guide covered:
- **Creating a player thumbnail** using `UIUserThumbnail`.  
- **Styling it with USS** for a clean UI.  
- **Handling interactions dynamically in Lua**.  

Now you can **create and customize player thumbnails** in your game UI!