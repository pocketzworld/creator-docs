# HR+ Validation

## Introduction

HR+ is a monthly subscription service that provides players with exclusive benefits, such as Custom App Icons, More outfit slots, and more. In this guide, you'll learn how to check if a player has an active HR+ subscription in your game using the Highrise API.

## Why Use HR+ Validation?

HR+ validation allows you to provide exclusive content or features to players who have an active HR+ subscription. HR+ users play a huge role in creator engagement payouts, so you can use HR+ validation to reward these users with special perks.

## Checking HR+ Status

The `player` object in the Highrise API provides a `isSubscriber` property that you can use to check if a player has an active HR+ subscription. Here's an example of how you can use this property to check if a player has an active HR+ subscription:

```lua
-- Check if the player has an active HR+ subscription
if player.isSubscriber then
  print("Player has an active HR+ subscription")
else
  print("Player does not have an active HR+ subscription")
end
```

## Use Cases

Assuming you have a game that offers exclusive areas to HR+ subscribers, you can use it this way:

HRPlusArea.lua (Client Script)
```lua
--!Type(Client)
function self:Awake()
    -- Function to validate the player and their HR+ status
    local function IsSubscriber(character)
        return character.player ~= nil and character.player.isSubscriber
    end

    -- Assuming you have a box collider that triggers the area
    function self:OnTriggerEnter(other: Collider)
        -- Validate the player character
        local playerCharacter = other.gameObject:GetComponent(Character)
        if not playerCharacter or not playerCharacter.player then return end

        -- Check if the player has an active HR+ subscription
        if IsSubscriber(playerCharacter) then
            print("Player has an active HR+ subscription")
            -- Teleport the player to the exclusive area
        else
            print("Player does not have an active HR+ subscription")
            -- Display a message to the player
        end
    end
end
```

## Enabling HR+ in Studio

To simulate HR+ in Studio, you can use the following steps:

1. In Unity, add a new virtual player/
2. Select "Profile Settings" and choose "Highrise+ Subscriber"
3. Run the game in Studio to test the HR+ features

## Conclusion

HR+ validation is a powerful tool that allows you to provide exclusive content to HR+ subscribers. By checking the `isSubscriber` property of the `player` object, you can easily determine if a player has an active HR+ subscription and provide them with special perks in your game. This can help increase player engagement and retention, as well as boost your creator engagement payouts.