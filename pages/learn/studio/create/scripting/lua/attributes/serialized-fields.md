# Serialized Fields

## Introduction
Serialized Fields in Highrise Studio are [Lua variables](https://create.highrise.game/learn/studio/create/coding-fundamentals/variables-and-data-types) that can be edited in the Inspector panel. By marking a variable as a Serialized Field, you can modify its value within the Studio Editor, without needing to alter the script. This is particularly useful for attaching game objects, assigning textures, and customizing other critical elements of your game.

## What is The Preceding `--!` in Serialized Fields?
The `--!` prefix is a special directive in Lua used by the Studio Editor to recognize specific comments. Adding `--!` before a comment (e.g., `--!SerializeField`) allows the Studio Editor to expose the variable in the Inspector. This makes it easy to attach objects, textures, or other assets directly from the Studio Editor without modifying the script.

**For example:**
```lua
--!SerializeField
local playerModel: GameObject = nil
```

This makes `playerModel` editable in the Inspector, allowing you to assign a specific GameObject from the Editor.

## Why Use Serialized Fields?

Serialized Fields offer several essential advantages for Highrise Studio development:

1. **Asset Assignment:** Easily attach game objects, textures, materials, and other assets directly in the Inspector.

2. **Customization:** Customize game objects and behaviors visually in the Studio Editor without altering the script.

3. **Streamlined Setup:** Simplifies the process of linking objects, adjusting settings, and configuring properties within the Studio Editor.

By leveraging Serialized Fields, you can efficiently manage important game elements directly from the Editor, reducing the need for manual coding.

## How to Define Serialized Fields
To define a Serialized Field, use the `--!SerializeField` directive above the variable declaration in your Lua script. This allows the Studio Editor to display the variable in the Inspector for easy editing.

**Example:**
```lua
--!SerializeField
local myNumber: number = 5
```

In this example, `myNumber` is a Serialized Field with an initial value of `5`. By adding the `SerializeField` attribute before the variable declaration, you can modify `myNumber` directly in the Inspector panel.

## Key Uses for Serialized Fields

Serialized Fields are especially useful when working with the following:

1. **Attaching Game Objects:** Link models, prefabs, and other GameObjects in the Studio Editor.

2. **Assigning Textures and Materials:** Set textures, images, or materials that can be applied to objects.

3. **Customizing Gameplay Elements:** Expose variables for important gameplay settings, such as health values, movement speed, or attack power.

Here are examples of different Serialized Fields in Lua:
```lua
--!SerializeField
local playerModel: GameObject = nil
--!SerializeField
local enemyPrefab: GameObject = nil
--!SerializeField
local healthBarTexture: Texture = nil
--!SerializeField
local spawnLocation: Transform = nil
--!SerializeField
local movementSpeed: number = 10
```

Serialized Fields can also be used to serialize tables, which are treated as arrays in Highrise Studio. This allows you to pass a collection of values between the `{}` brackets, making it easy to manage lists of data directly from the Inspector.

**For example:**
```lua
--!SerializeField
local myTable: { string } = nil -- Tables are serialized as arrays
```

You can use tables to pass collections of any type, like numbers, strings, GameObjects, or even custom objects, offering great flexibility for storing and managing grouped data in your scripts.
```lua
--!SerializeField
local spawnPoints : { Transform } = nil
```

This makes Serialized Fields powerful for handling lists of game objects, settings, or assets within the Inspector, all without needing to modify code.

<Note type="info">
Note: Lua types are lowercase (e.g., number, string), while Unity-specific types are PascalCase (e.g., GameObject, Transform).
</Note>

**Example: Lua Type**
```lua
--!SerializeField
local movementSpeed: number = 10
```

**Example: Unity Type**
```lua
--!SerializeField
local enemyPrefab: GameObject = nil
```

For more Unity-supported types, refer to the `Learn > Studio > API > Classes` section in the Create Portal.

## How to Access Serialized Fields

Once defined in your script, Serialized Fields are displayed in the Inspector panel. You can easily edit or assign values such as game objects or textures by selecting the relevant game object and viewing its fields in the Inspector. These fields can be modified at any time to adjust assets, properties, and behaviors in the Editor.

## Video Preview

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/nWYiGnlCkt8" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


## Conclusion

Serialized Fields in Highrise Studio let you easily manage key elements like game objects, textures, and gameplay settings directly in the Inspector. This allows quick customization and asset adjustments without altering scripts, streamlining development and making the process more intuitive.