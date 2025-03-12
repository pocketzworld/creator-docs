# Trigger Events

## Introduction
Triggers are essential components in game development that enable interactions between GameObjects in your Highrise world. In this guide, you will learn how to utilize triggers effectively to create dynamic and interactive experiences.

### What is a Trigger?

A Trigger is a collider added to your GameObject with the "Trigger" option enabled. Unlike regular colliders, triggers do not physically interact with other colliders; instead, they detect when other colliders enter, stay within, or exit their boundaries.

<Note type="warning">
For a trigger to work, at least one of the GameObjects interacting with it must have a Rigidbody component attached.
</Note>

### Trigger Events:

Triggers fire three main events when interactions occur:

1. **OnTriggerEnter:** Triggered when a collider enters the trigger.
2. **OnTriggerStay:** Triggered while a collider stays within the trigger.
3. **OnTriggerExit:** Triggered when a collider exits the trigger.

<Note type="warning">
If the player isn't detecting the trigger, make sure the GameObject layer is set to "CharacterTrigger" for the player to interact with it.
</Note>

<Note type="info">
The trigger or the collider interacting with it must have a Rigidbody component attached. However, the Rigidbody can be set to kinematic to disable physics simulation.
</Note>

### Examples:

**Object Entering and Exiting a Trigger:**

```lua
function self:OnTriggerEnter(other : Collider)
    local enteringGameObject = other.gameObject
    print(enteringGameObject.name .. " has entered the trigger")
end

function self:OnTriggerExit(other : Collider)
    local exitingGameObject = other.gameObject
    print(exitingGameObject.name .. " has left the trigger")
end
```

**Local Player Entering and Exiting a Trigger:**

```lua
    -- Connect to the OnTriggerEnter event
    function self:OnTriggerEnter(other : Collider)
        -- Get the Character component of the entering GameObject
        local playerCharacter = other.gameObject:GetComponent(Character)
        -- Exit the function if the GameObject doesn't have a Character component
        if playerCharacter == nil then return end

        -- Get the player from the Character component
        local player = playerCharacter.player

        -- Check if the entering player is the local player
        if client.localPlayer == player then
            print(player.name .. " Entered the Trigger") -- Print the player's name
        end
    end

    -- Connect to the OnTriggerExit event
    function self:OnTriggerExit(other : Collider)
        -- Get the Character component of the exiting GameObject
        local playerCharacter = other.gameObject:GetComponent(Character)
        -- Exit the function if the GameObject doesn't have a Character component
        if playerCharacter == nil then return end

        -- Get the player from the Character component
        local player = playerCharacter.player
        -- Check if the exiting player is the local player
        if client.localPlayer == player then
            print(player.name .. " Exited the Trigger") -- Print the player's name
        end
    end
```

## Conclusion

Triggers are powerful tools that enable you to create interactive and dynamic gameplay experiences in your Highrise world. By utilizing trigger events effectively, you can create engaging interactions between GameObjects and enhance the overall player experience.
