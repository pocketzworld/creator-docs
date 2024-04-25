# **Random Number Generator**

## **Introduction**
This example breaks down how to write the script for the Random Number Generator asset, which generates a random number within a specified range when a tap event is triggered:

## Create an Interactable Random Number Generator

### 1. Set Up an Interactable Object

- Follow steps 1-4 in the [Multiplayer Button Guide](multiplayer-button.md)

### 3. Write the Lua Script

- Double-click the Lua script in the Project window to open it.
- Write the following code inside the script:
```lua
--!SerializeField
local maxNumber : number = 10

local currentNumber = IntValue.new("CurrentNumber", 0)
local tapRequest = Event.new("TapRequest")

local myMaterial = nil

function self:ClientAwake()

    --Set myMaterial to the Objects material
    myMaterial = self.gameObject:GetComponent(Renderer).material

    --Connect to the Tapped event in the TapHandler Component
    self.gameObject:GetComponent(TapHandler).Tapped:Connect(function()
        tapRequest:FireServer()
    end)

    --Connect to the Chantged Event from out Network Integer Value
    currentNumber.Changed:Connect(function(newVal, oldVal)
        --Update Visual
        myMaterial:SetFloat("_Tile", tonumber(newVal))
    end)
end

function self:ServerAwake()
    --Connect to the Tap Request from a Client
    tapRequest:Connect(function()
        --Set the Current Number to a random value
        currentNumber.value = math.random(1,maxNumber)
    end)
end
```

**Variable Declarations**:
   - `maxNumber`: A constant defining the maximum value for a random number.
   - `currentNumber`: A network-synced integer that tracks the current number.
   - `tapRequest`: A network event that triggers when the object is tapped.
   - `myMaterial`: A variable to store the material of the object (initially `nil`).

**Client-side Functionality** (`ClientAwake`):
- **Material Initialization**:
    - Retrieves and stores the material of the game object for later modification.
- **Tap Interaction**:
    - Connects to the `Tapped` event of the object to fire a `tapRequest` to the server when tapped.
- **Visual Update on Change**:
    - Listens for changes to `currentNumber` and updates the material's `_Tile` property based on the new value to alter the object's visual appearance.

**Server-side Functionality** (`ServerAwake`):
- **Handling Tap Requests**:
    - Responds to `tapRequest` events from clients by setting `currentNumber` to a random value between 1 and `maxNumber`.

>`_Tile` is a custom property from the Shader included in the Random Number Generator Asset on the Asset Store.

By following these steps, you can create a Lua script in Highrise Studio that functions as a random number generator, updating visual feedback based on user interactions. This script can be further customized or integrated into larger projects as needed.