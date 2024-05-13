# GameObjects and Components

## Introduction

In this guide, you will learn about GameObjects and Components in Unity. GameObjects are the basic building blocks of a Unity scene. They are the objects that you see in the scene view and the objects that you interact with in the game view. Components are the building blocks of GameObjects. They are the pieces that make up a GameObject and define its behavior.

## Accessing GameObjects

The `gameObject` property allows you to interact with the GameObject that this LuaBehaviour instance (remember, accessed by `self` in [Lua](https://create.highrise.game/learn/studio/create/scripting/create/lua/overview) scripts) is attached to. This equips your Lua script with the ability to manipulate the GameObject in complex ways.

Here is an example of accessing a GameObject's properties:

```lua
local obj = self.gameObject
print(obj.name) -- Output: GameObject

local objTransform = self.transform
print(tostring(objTransform.position)) -- Output: (0.0, 0.0, 0.0)
```

In this script:

- `gameObject`: Refers to the GameObject that the Lua script is attached to.
- `name`: Returns the name of the GameObject.
- `transform`: Refers to the Transform component of the GameObject.
- `position`: Returns the position of the GameObject in the scene.

## Getting and Setting Components

Components are the building blocks of GameObjects. They define the behavior of the GameObject and allow you to interact with it in various ways. You can access and manipulate components using the `GetComponent` and `AddComponent` functions.

- `GetComponent`: Retrieves a component of the specified type from the GameObject.
- `AddComponent`: Adds a new component of the specified type to the GameObject.

```lua
-- Add the Tap Handler Component to our Self
self.gameObject:AddComponent(TapHandler)

-- Get the Tap Handler Component
local myTapHandler = self.gameObject:GetComponent(TapHandler)

-- Get your custom lua script
local myHelloWorldScript = self.gameObject:GetComponent("HelloWorldScript")
```

In this script:

- `AddComponent`: Adds a new component to the GameObject.
- `GetComponent`: Retrieves a component from the GameObject.
- `TapHandler`: Refers to the TapHandler component.
- `HelloWorldScript`: Refers to the HelloWorldScript component.

If you noticed, we used `TapHandler` and `"HelloWorldScript"` as arguments for `AddComponent` and `GetComponent`.

We did not include the `" "` when adding the `TapHandler` component because it is a built-in component. However, we included the `" "` when adding the `HelloWorldScript` component because it is a custom Lua script.

## Creating and Destroying GameObjects

You can create and destroy GameObjects using the `new` and `Destroy` functions.

- `new`: Creates a new GameObject.
- `Destroy`: Destroys the GameObject.

```lua
-- Creating a new GameObject
local newGameObject = GameObject.new("NewGameObject")
newGameObject.name = "NewGameObject" -- Set the name of the GameObject

-- Destroying a GameObject
Destroy(newGameObject)
```

In this script:

- `new`: Creates a new GameObject with the specified name.
- `name`: Sets the name of the GameObject.
- `Destroy`: Destroys the GameObject.

## Creating Prefabs

Prefabs are reusable GameObjects that you can create and instantiate in your scenes. You can create prefabs using the `Prefab` class.

1. Right click in the `Hierarchy` window.
2. Select `Create > 3D Object > Cube`.
3. Drag the `Cube` GameObject to the `Assets` window to create a prefab.
4. Delete the `Cube` GameObject from the `Hierarchy` window.

**Instantiate a Prefab:**

To instantiate a prefab, you can use the `Instantiate` function.

```lua
--!SerializeField
local myGameObjectPrefab : GameObject = nil -- Reference to the prefab

-- Create a function to spawn a new Object
function SpawnNewObject(obj)
    -- Create the Game Object
    local newObject = Object.Instantiate(obj)
    -- Create a reference to it's Transform
    local newObjectTransform = newObject.transform

    -- Manipulate it's Position Rotation and Scale
    newObjectTransform.localPosition = Vector3.new(0,0,0)
    newObjectTransform.localEulerAngles = Vector3.new(0,0,0)
    newObjectTransform.localScale = Vector3.new(1,1,1)
end

SpawnNewObject(myGameObjectPrefab)
```

After Serialization, you can drag and drop a prefab from the `Assets` window to the `myGameObjectPrefab` field in the `Inspector` window.

In this script:

- `SerializeField`: Exposes the `myGameObjectPrefab` variable in the Unity Editor. [Learn more](https://create.highrise.game/learn/studio/create/scripting/create/lua/attributes/serialized-fields).
- `Instantiate`: Creates an instance of the specified prefab.
- `localPosition`: Sets the position of the GameObject.
- `localEulerAngles`: Sets the rotation of the GameObject.
- `localScale`: Sets the scale of the GameObject.

By following these steps, you can create and manipulate GameObjects and Components in Unity to build interactive and engaging game experiences.

## Use Cases

GameObjects and Components are commonly used for the following purposes:

- **Game Logic**: Implementing core gameplay mechanics and rules.
- **Visual Effects**: Creating interactive and dynamic visual elements.
- **User Interface**: Designing menus, buttons, and other user interface elements.
- **Physics Simulations**: Handling physics interactions and collisions.
- **Audio Management**: Playing sounds and music in the game.

By utilizing GameObjects and Components effectively, you can create immersive and interactive game environments that captivate players and bring your creative vision to life.

## Do and Don't

In this table, we summarize the best practices and common pitfalls when working with GameObjects and Components:

| Do                                       | Don't                                    |
|------------------------------------------|------------------------------------------|
| Use GameObjects for building scenes and game objects. | Use GameObjects for heavy computations or complex logic. |
| Utilize Components to define the behavior of GameObjects. | Overload GameObjects with unnecessary components or scripts. |
| Create prefabs for reusable GameObjects and assets. | Instantiate prefabs for every instance of a GameObject. |
| Optimize GameObjects and Components for performance and efficiency. | Create GameObjects with excessive components or scripts. |
| Leverage GameObjects and Components to create interactive and engaging game experiences. | Rely solely on GameObjects for game logic or visual effects. |

## Conclusion

By following best practices and leveraging GameObjects and Components effectively, you can create engaging and immersive game experiences that captivate players and bring your creative vision to life. Experiment with GameObjects and Components to explore their capabilities and enhance your game development process.