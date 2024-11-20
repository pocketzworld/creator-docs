# Changing Characters' Outfits

## Introduction

Highrise Studio allows you to change the outfits of the characters in your world. This feature is useful for creating different looks or equipping characters with different items.

## Steps

### Step 1: Create a New Outfit

1. Right-click in the **Project** panel then `Create > Highrise > Outfit > Player Outfit`.
2. Give your outfit a name (e.g. "FisherOutfit").
3. Double click on the outfit to open it in the **Outfit Editor**.
4. Select the items you want to add to the outfit from the list.
5. CTRL + S to save the outfit.

### Step 2: Create Script to Store Outfit

<Note type="warning">
This module script is optional but recommended to easily manage your items and outfits. You can also store the outfit directly in the script that equips the outfit.
</Note>

1. Right-click in the **Project** panel then `Create > Lua > Module`.
2. Give your script a name (e.g. "ItemsMetaData").
3. Double click on the script to open it in the **Script Editor**.
4. Add the following code to the script:

```lua
--!Type(Module)

--!SerializeField
local Outfits : {CharacterOutfit} = nil

-- Add your items here (e.g. fishing pole)
Items = {
  ["fishing_pole_basic"] = {
    Name = "Fishing Pole",
    Outfit = Outfits[1] or nil
    -- Other properties here
  }
}
```

5. Save the script by pressing CTRL + S.

### Step 3: Write a Script to Equip Outfit

1. Right-click in the **Project** panel then `Create > Lua > Client`.
2. Give your script a name (e.g. "EquipOutfit").
3. Double click on the script to open it in the **Script Editor**.
4. Add the following code to the script:

```lua
--!type(Client)

-- Require the OutfitsMetaData module
local ItemsMetaData = require("ItemsMetaData")

-- Listen to the Start event
function self:Start()
  -- Get the player outfit from the ItemsMetaData
  local outfit = ItemsMetaData.Items["fishing_pole_basic"]
  if not outfit then return end

  -- Double check that the outfit exists
  if not outfit.Outfit or outfit.Outfit == nil then
    print("No outfit found for fishing_pole_basic")
    return
  end

  -- Get the player's character
  local character = client.localPlayer.character
  if not character then return end

  -- Add the outfit to the player
  character:AddOutfit(outfit.Outfit)
  print("Outfit added to player")

  -- Demonstrate how to remove the outfit after 10 seconds
  Timer.After(10, function()
    character:RemoveOutfit(outfit.Outfit)
    print("Outfit removed from player")
  end)
end
```

5. Save the script by pressing CTRL + S.

### Step 4: Run the Script

To run the scripts you must register them in the scene.

1. Right-click on the **Hierarchy** panel then `CreateEmpty`.
2. Give your object a name (e.g. "EquipOutfit").
3. Drag the `EquipOutfit` script to the object.
4. Repeat the same steps for the `ItemsMetaData` script.

Once you have added the scripts to the scene, you can now select the **ItemsMetaData** object and assign the outfit you created in the **Outfit** field in the inspector.

1. Select the `ItemsMetaData` object in the **Hierarchy** panel.
2. In the inspector panel under the **Outfits** field, click "+" to add a new element.
3. Drag the outfit you created in the **Project** panel to the new element.

Now you can run the scene and see the character equipped with the new outfit.

## Conclusion

You have successfully changed the outfit of a character in your world. This feature allows you to create different looks for your characters or equip them with different items.