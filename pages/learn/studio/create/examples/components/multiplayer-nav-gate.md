# Multiplayer Nav Mesh Gate

## **Introduction**
This example demonstrates how to create Nav Mesh Gates that run code on the client and server for multiplayer functionality.

## Create an Interactable Nav Mesh Gate

### 1. Set Up an Interactable Object

- Follow steps 1-4 in the [Multiplayer Button Guide](multiplayer-button)

### 2. Create a Nav Mesh Obstacle

- In the Hierarchy window, as a child of the interactable button, create a new 3D object, such as a cube, to act as your Dynamic `Nav Mesh Obstacle`.
- Add a Nav Mesh Obstacle component to the child object.
  - Set the `Carve` option to `true`.
  - Set the `Shape`, `Center`, and `Size` of the obstacle component.

### 3. Write the Lua Script

- Double-click the Lua script in the Project window to open it.
- Write the following code inside the script:

```lua
--!SerializeField
local Obstacle : GameObject = nil 
-- The Child Object with the Obstacle Component

local toggleGateRequest = Event.new("ToggleGateRequest")
local gateState = BoolValue.new("GateState", true)

function self:ClientAwake()

    -- Locally Enable and Disbale the Obstacle
    function SetGate(state)
        local isActive = state
        Obstacle:SetActive(isActive)
    end

    -- Fire the Event to Server when Tapped
    local TapHandler = self.gameObject:GetComponent(TapHandler)
    TapHandler.Tapped:Connect(function()
        toggleGateRequest:FireServer()
    end)

    -- Connect to the Gate's State Changed Event
    if gateState.value then SetGate(gateState.value) end
    gateState.Changed:Connect(function(newVal, oldVale)
        -- Gate Changed
        SetGate(newVal)
    end)
end

function self:ServerAwake()
    -- Connect to the Event from the Client and Toggle the Network Boolean
    toggleGateRequest:Connect(function()
        gateState.value = not gateState.value
    end)
end
```
**Variable Declarations**:
- `Obstacle`: Represents the gate object.
- `toggleGateRequest`: Event triggered to toggle the gate.
- `gateState`: Tracks the gate's current state on the network.

**Client-side Functionality** (`ClientAwake`):
- Defines `SetGate` to toggle the gate's visibility.
- Listens for taps on the gate and sends a request to toggle it.
- Updates the gate's visibility when its state changes.

**Server-side Functionality** (`ServerAwake`):
- Listens for toggle requests from the clients and toggles the gate's state on the network accordingly.


By following these steps, you can create an interactable door in Studio using the Lua API.