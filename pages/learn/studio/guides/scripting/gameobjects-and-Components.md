# **GameObjects and Components**

## **Introduction**
In this guide you will learn how to create and manipulate `GameObjects` and `Components` with your Lua script.
In a world, it is very common to create objects and modify or read specific components to objects.
Lua supports the same interface as that used in a Unity script.

> Note: The `gameObject` property allows you to interact with the GameObject that this LuaBehaviour instance (remember, accessed by `self` in Lua scripts) is attached to. This equips your Lua script with the ability to manipulate the GameObject in complex ways.

**gameObject and transform**
```lua
local go = self.gameObject
print("Hi! My name is " .. go.name)

local t = self.transform
print("Hi! I'm located at " .. tostring(t.position))
```

### **Examples of GameObject and GetComponent**

**Getting and Adding Components**
```lua
-- Add the Tap Handler Component to our Self
self.gameObject:AddComponent(TapHandler)

-- Get the Tap Handler Component
local myTapHandler = self.gameObject:GetComponent(TapHandler)

-- Get your custom lua script
local myHelloWorldScript = self.gameObject:GetComponent("HelloWorldScript")
```

> Note: when using GetComponent for a custom lua script (not a built in Class) you need to input a string like so: `GetComponent("MyLuaScript")`

When calling instance functions (functions that act on a specific instance of an object), `:` is used instead of `.` automatically passing `self` as the first input. 
Therefore `self.gameObject:GetComponent(TapHandler)` is the same as `self.gameObject.GetComponent(self, TapHandler)`. Getting the Taphandler on this specific Instance.

**Creating and Destroying a GameObject**
``` lua
-- Creating a new Object
local tempGO = GameObject.new()
tempGO.name = "SuperCoolGameObject"

-- Destroying an Object
Object.Destroy(tempGO)
```

### **Prefabs**

**Creating a Prefab**
- Add a new Object to the Scene, `+ > 3D Object > Cube`

![Add-Cube](/assets/learn/guides/studio/add-cube.png) 

- Drag the Cube to the `Project` window to make it a `Prefab`

![Create-Prefab](/assets/learn/guides/studio/create-prefab.png) 

- Delete the the instance from the Scene now that it is saved to our Assets.

![Delete-Instance](/assets/learn/guides/studio/delete-instance.png)

**Instantiating a Prefab**

To Instantiate a Prefab or *spawn an object*, reference the following code:
```lua
--!SerializeField
local myGameObject : GameObject = nil

--Create a function to spawn a new Object
function SpawnNewObject(obj)
    -- Create the Game Object
    local newObject = Object.Instantiate(obj)
    -- Create a reference to it's Transform
    local newObjectTransform = newObject.transform

    -- Manipulate it's Position Rotation and Scale
    newObjectTran.localPosition = Vector3.new(0,0,0)
    newObjectTran.localEulerAngles = Vector3.new(0,0,0)
    newObjectTran.localScale = Vector3.new(1,1,1)
end

SpawnNewObject(myGameObject)
```
Now set your Prefab as myGameObject and run your Script.

![Set-Prefab](/assets/learn/guides/studio/set-object.png)
