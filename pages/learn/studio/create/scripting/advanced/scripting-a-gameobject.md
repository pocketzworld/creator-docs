# Scripting a GameObject

## Introduction
In this guide you will learn how to create a basic Lua script and add it to a game object.

### What is a Lua Script?
- Lua is the scripting language used for creating dynamic and interactive Highrise Worlds.
- [Learn more about Lua scripting](https://create.highrise.game/learn/studio/create/scripting/lua/overview).

> ❗️ When building a Highrise World, C# scripts are not included in the build. Make sure to use Lua scripts for your game objects.

## Creating a Hello World Script
Let's create a simple script that prints "Hello, World!" to the console when the game starts.

### Step 1: Create a Lua Script

1. Open your project in Unity.
2. In the **Project** panel, right-click and select **Create > Highrise > Lua Script**.
3. Name the script `HelloWorldScript` and press **Enter**.

### Step 2: Opening the Script

1. Double-click the `HelloWorldScript` to open it in your code editor.
2. Write the following code in the script:

```lua
-- This script prints "Hello, World!" to the console
print("Hello, World!")
```
[Learn more about coding fundamentals](https://create.highrise.game/learn/studio/create/coding-fundamentals/overview).

### Step 3: Attaching the Script to a GameObject

1. Right-click the `Hierarchy` panel.
2. Select **3D Object > Create Empty** to create an empty game object.
3. Rename the object to `HelloWorldObject`.
4. Pick the `HelloWorldObject` in the `Hierarchy` panel.
5. Drag the `HelloWorldScript` onto the `HelloWorldObject` in the `Inspector` panel.

### Step 4: Testing the Script

1. Hit **Play** in Unity to enter Play Mode.
2. Check the console for the "Hello, World!" message.

## Conclusion

You have successfully created a Lua script that prints "Hello, World!" to the console when the game starts. This simple script demonstrates the basics of scripting in Highrise Studio. Experiment with different scripts to add interactivity and functionality to your game objects.


## Video Preview
<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/iT6h-kq97S0" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

### Next Steps

Delve deeper into lua scripting by learning about:
- [Variables and Data Types](https://create.highrise.game/learn/studio/create/coding-fundamentals/variables-and-data-types)
- [Control Structures](https://create.highrise.game/learn/studio/create/coding-fundamentals/control-structures)
- [Functions](https://create.highrise.game/learn/studio/create/coding-fundamentals/functions)
- [Script Types](https://create.highrise.game/learn/studio/create/coding-fundamentals/script-types)
