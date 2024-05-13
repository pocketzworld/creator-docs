# Serialized Fields

## Introduction
In Highrise Studio, Serialized Fields are [Lua variables](https://create.highrise.game/learn/studio/create/coding-fundamentals/variables-and-data-types) that are visible and editable in the Inspector. By marking a variable as a Serialized Field, you can modify its value directly in the Studio Editor without changing the script code. This feature is useful for tweaking values, testing different configurations, and adjusting properties during runtime.

## What is The Preceding `--!` in Serialized Fields?
The `--!` prefix is a special directive in Lua that indicates a comment recognized by the Studio Editor. By adding `--!` before a comment, you can specify directives like `SerializeField` to expose variables in the Inspector. This prefix helps Studio identify specific comments as directives and process them accordingly.

For example, to define a Serialized Field in Lua, you can use the `--!SerializeField` directive before the variable declaration:

```lua
--!SerializeField
local moveSpeed = 10
```

## Why Use Serialized Fields?

Serialized Fields offer several benefits for game development in Highrise Studio:

1. **Interactive Editing:** Serialized Fields enable interactive modification of variable values in the Inspector panel, allowing real-time adjustments without script code changes.

2. **Customization:** Exposing variables as Serialized Fields enables direct customization of game objects, behaviors, and properties in the Studio Editor, enhancing flexibility and control.

3. **Testing and Debugging:** Serialized Fields offer a convenient way to test various configurations, tweak values, and debug scripts during development, streamlining the iteration process.

4. **Runtime Modifications:** Serialized Fields facilitate changing variable values during runtime, simplifying experimentation with different settings and behaviors without restarting the game.

Overall, Serialized Fields are a powerful feature in Highrise Studio that simplifies the process of tweaking variables, adjusting properties, and customizing game elements directly in the Inspector panel.

## How to Define Serialized Fields
To define a Serialized Field in your Lua script, you need to use the `SerializeField` attribute followed by the variable declaration. This attribute tells the Studio Editor to display the variable in the Inspector panel, enabling you to edit its value interactively.

Here's an example of defining Serialized Fields in Lua:

```lua
--!SerializeField
local myNumber = 5
```

In this example, `myNumber` is a Serialized Field with an initial value of `5`. By adding the `SerializeField` attribute before the variable declaration, you can modify `myNumber` directly in the Inspector panel.

## What Types of Variables Can Be Serialized?

In Highrise Studio, you can serialize various types of variables, including fundamental data types (e.g., numbers, strings, booleans) and Unity-specific types (e.g., GameObject, Transform, Vector3). By marking these variables as Serialized Fields, you can customize and adjust their properties interactively in the Inspector panel.

Here are examples of different types of Serialized Fields in Lua:

```lua
--!SerializeField
local myNumber = 10
--!SerializeField
local myString = "Hello, World!"
--!SerializeField
local myBool = true
--!SerializeField
local myGameObject = nil
--!SerializeField
local myTransform = nil
--!SerializeField
local myVector = Vector3.new(1, 2, 3)
```

> Note: when declaring typed variables, the fundamental types are `lowercase` where the Unity types are `PascalCase`.
> To get more supported Unity Types, see `Learn>Studio>API>Classes` on the Create Portal.

**Fundamental Types Example (lowercase):**
```lua
--!SerializeField
local myString = "Hello, World!" -- Lua String Type
```

**Unity Types Example (PascalCase):**
```lua
--!SerializeField
local Vector3Value = Vector3.new(1, 2, 3) -- Unity Vector3 Type
```

## How to Access Serialized Fields

Once you've defined a Serialized Field in your Lua script, you can access and modify its value in the Inspector panel. To view and edit Serialized Fields, select the game object or script containing the variables, and navigate to the Inspector panel in the Studio Editor.

In the Inspector panel, you'll see the Serialized Fields listed with their corresponding values. You can click on the value field to edit the variable directly, enter a new value, and press `Enter` to apply the changes.

## Video Preview

<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/nWYiGnlCkt8" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


## Conclusion

Serialized Fields are a valuable feature in Highrise Studio that simplifies the process of tweaking variables, adjusting properties, and customizing game elements interactively. By marking variables as Serialized Fields, you can modify their values directly in the Inspector panel, enabling real-time adjustments without changing the script code. This interactive editing capability enhances flexibility, control, and efficiency in game development, making it easier to test configurations, debug scripts, and customize game objects during development.