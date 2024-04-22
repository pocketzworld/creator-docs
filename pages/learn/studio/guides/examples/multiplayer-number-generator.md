# **Random Number Generator**

## **Introduction**
This guide explains how to wrtie the script for the Random Number Generator asset, which generates a random number within a specified range when a tap event is triggered:


> Create a Scripted Object:
Follow steps 1-4 in the [Multiplayer Button Example.](../pages/learn/studio/guides/examples/multiplayer-button.md)

#### Step 1: Define Variables and Imports
1. Declare the maximum number: Use the SerializeField attribute to set the maximum number to generate. This allows it to be editable in the Unity editor.
```lua
--!SerializeField
local maxNumber : number = 10
```
2. Declare variables: Define variables for the current number, tap request event, and material.
```lua
local currentNumber = IntValue.new("CurrentNumber", 0)
local tapRequest = Event.new("TapRequest")
local myMaterial = nil
```

#### Step 2: Client Awake Function
1. **Set material:** In the `ClientAwake` function, retrieve the material of the game object and assign it to the `myMaterial` variable.
```lua
myMaterial = self.gameObject:GetComponent(Renderer).material
```
2. **Connect tap event:** Connect to the tapped event in the `TapHandler` component, and fire the tap request event when tapped.3
```lua
self.gameObject:GetComponent(TapHandler).Tapped:Connect(function()
    tapRequest:FireServer()
end)
```
3. **Update visual on number change:** Connect to the changed event of the network integer value `currentNumber` and update the visual by setting the material float value.
```lua
currentNumber.Changed:Connect(function(newVal, oldVal)
    myMaterial:SetFloat("_Tile", tonumber(newVal))
end)
```
> Note: `_Tile` is a custom float in the `RandomNumberShader` that controls `Flipbook` Node's `Tile` input.

#### **Step 3: Server Awake Function**
1. **Connect tap request:** In the `ServerAwake` function, connect to the tap request event from a client.
```lua
tapRequest:Connect(function()
    currentNumber.value = math.random(1,maxNumber)
end)
```

# **Final Script**
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
#### **Summary**
By following these steps, you can create a Lua script in Highrise Studio that functions as a random number generator, updating visual feedback based on user interactions. This script can be further customized or integrated into larger projects as needed.