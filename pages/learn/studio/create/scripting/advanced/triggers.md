# Triggers

## **Introduction**
Triggers are essential components in game development that enable interactions between GameObjects in your Highrise world. In this guide, you will learn how to utilize triggers effectively to create dynamic and interactive experiences.

### **What is a Trigger?**

A Trigger is a collider added to your GameObject with the "Trigger" option enabled. Unlike regular colliders, triggers do not physically interact with other colliders; instead, they detect when other colliders enter, stay within, or exit their boundaries.

### Trigger Events:

Triggers fire three main events when interactions occur:

1. **OnTriggerEnter:** Triggered when a collider enters the trigger.
2. **OnTriggerStay:** Triggered while a collider stays within the trigger.
3. **OnTriggerExit:** Triggered when a collider exits the trigger.

>The trigger or the collider interacting with it must have a Rigidbody component attached. However, the Rigidbody can be set to kinematic to disable physics simulation.

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

<Note type="warning">
If the player isn't detecting the trigger, make sure the GameObject layer is set to "CharacterTrigger" for the player to interact with it.
</Note>

```lua
    function self:OnTriggerEnter(other : Collider)
        local playerCharacter = other.gameObject:GetComponent(Character)
        if playerCharacter == nil then return end  -- Break if no Character component

        local player = playerCharacter.player
        if client.localPlayer == player then
            print(player.name .. " Entered")
        end
    end

    function self:OnTriggerExit(other : Collider)
        local playerCharacter = other.gameObject:GetComponent(Character)
        if playerCharacter == nil then return end  -- Break if no Character component

        local player = playerCharacter.player
        if client.localPlayer == player then
            print(player.name .. " Exited")
        end
    end
```

