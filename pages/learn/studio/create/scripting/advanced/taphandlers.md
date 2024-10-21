# Tap Handlers

## Introduction
In this guide, you will learn how to utilize TapHandlers in Lua scripting to trigger actions when an object is tapped by the user.

### What is a TapHandler?
A TapHandler is a built-in component that allows you to connect to an event triggered when a collider is tapped by a user in your Highrise world.

### Understanding TapHandler Properties:
The TapHandler component includes three properties:

1. **Check Distance:**
   - When enabled, the player character needs to be within a certain distance to interact with the object.
   
2. **Distance:**
   - Specifies the maximum distance from the object at which it can be tapped if "Check Distance" is enabled.
   
3. **Walk to:**
   - When enabled, the player character automatically attempts to walk to the object. Once the character reaches the specified distance, the Tapped event is triggered.

> **Note:** A TapHandler requires a collider to be tapped.

### Accessing TapHandler in Lua Script:
To access the TapHandler component in Lua script and connect to the Tapped event, use the `GetComponent` method on the object containing the TapHandler. Here's a code snippet demonstrating how to achieve this:

```lua
function self:Awake()
    self.gameObject:GetComponent(TapHandler).Tapped:Connect(function() 
        -- Code to execute when the object is tapped
    end)
end
```

> Click here to get the TapHandler Class API:
> [Tap Handler API](https://create.highrise.game/learn/studio-api/api/classes/TapHandler)