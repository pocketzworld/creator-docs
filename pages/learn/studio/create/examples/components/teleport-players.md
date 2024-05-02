# **Teleport Players**

## **Introduction**
This guide explains how to set up a teleportation trigger in Highrise Studio. Teleportation triggers are essential for games that need dynamic player movement across different areas of the map instantaneously. By following these instructions, you can enable characters to teleport to a designated point upon entering a specified trigger area.

## Create a Trigger based Teleporter

### 1. Create Trigger and Respawn Point
- **Create an Empty Object:**
   - In your scene, create an empty object to act as a container for the trigger and the respawn point.
   
- **Add a Trigger Collider:**
   - Add a child object to your empty container and attach a collider component to it. Set this collider to "Is Trigger" to enable it to detect other colliders without causing physical interactions.

- **Define the Respawn Point:**
   - Add another child object to serve as the respawn point. This will be the location where characters are teleported to. Ensure it is properly positioned where you want players to respawn.

### 2. Writing and Understanding the Lua Script

- Attach a Lua script to your trigger object and use the following script, which coordinates the teleportation process between the server and client:

### **Teleport Trigger Lua Script**
```lua
--!SerializeField
local RespawnPoint : Transform = nil  -- The position to teleport characters to

local triggerRequest = Event.new("TriggerRequest")  -- Client to server request
local triggerEvent = Event.new("TriggerEvent")      -- Server to client notification

function self:ClientAwake()
    function self:OnTriggerEnter(other : Collider)
        local playerCharacter = other.gameObject:GetComponent(Character)
        if playerCharacter == nil then return end  -- Exit if no Character component
    
        local player = playerCharacter.player
        if client.localPlayer == player then
            triggerRequest:FireServer(RespawnPoint.position)  -- Request teleport from server
        end
    end

    triggerEvent:Connect(function(player)
        player.character:Teleport(RespawnPoint.position)  -- Execute teleport on the client side
    end)
end

function self:ServerAwake()
    triggerRequest:Connect(function(player, position)
        player.character.transform.position = position
        triggerEvent:FireAllClients(player)
    end)
end
```

**Variable Declarations**:
   - `RespawnPoint`: Reference to the Transform that acts as the respawn point.
   - `triggerRequest`: Event to request teleportation.
   - `triggerEvent`: Event to notify clients of teleportation.

**Client-side Logic** (`ClientAwake`):
  - The script first checks if the object entering the trigger has a Character component.
  - It confirms if the character is controlled by the local player. If so, it sends a teleport request to the server using `triggerRequest:FireServer()`, specifying the respawn position.
  - It listens for the `triggerEvent` from the server to locally teleport the character using `character:Teleport()`.

**Server-side Logic** (`ServerAwake`):
  - Upon receiving a teleport request (`triggerRequest`), the server directly modifies the character's position using `transform.position`. This approach ensures that the position change is authoritative and consistent across all clients.
  - The server then broadcasts the teleport event to all clients with `triggerEvent:FireAllClients()`, instructing them to update their local state.

### 3: Testing and Adjustments

- **Test the Trigger:**
  - Run your scene and have a character enter the trigger area. Observe if the teleportation works correctly by checking the character’s new position.
  
- **Troubleshoot Issues:**
  - If the teleportation does not occur, verify that the `RespawnPoint` is correctly linked in the script properties, the collider is properly set to trigger, and there are no errors in the console.

## **Conclusion**

By implementing the described setup and script, you have created a functional teleport trigger in Highrise Studio that can be tailored for various game development needs. This guide ensures you maintain proper control over player positioning, which is critical for game integrity and player experience.