# Write Your First Script

## Introduction

Coding might seem daunting initially, but with practice and perseverance, it becomes a rewarding skill. This guide aims to help you write your first script in Lua, Highrise's primary scripting language. By the end, you'll have a basic understanding of scripting concepts and the ability to create simple interactions in your Highrise world.


## Understanding Lua Scripts

Lua scripts are text files containing instructions that dictate the behavior of the game engine. Written in Lua, known for its simplicity and flexibility, these scripts control various aspects of your Highrise world, including player movement, object interactions, and game logic.


## What to Understand Before Writing Scripts

Before diving into scripting, grasp these fundamental concepts:


- [Script Types](https://create.highrise.game/learn/studio/create/scripting/script-types/overview): Different scripts control various gameplay aspects.
- [Variables and Data Types](https://create.highrise.game/learn/studio/create/coding-fundamentals/variables-and-data-types): Containers for storing and manipulating data.
- [Control Structures](https://create.highrise.game/learn/studio/create/coding-fundamentals/control-structures): Statements controlling code execution flow.
- [Functions](https://create.highrise.game/learn/studio/create/coding-fundamentals/functions): Code blocks performing specific tasks.


## Creating Scripts in Unity

To initiate a new script in Unity:

1. Open your project.
2. In the **Project** panel, right-click and select **Create > Highrise > Lua Script**.
3. Choose the script type (Client, Server, ClientAndServer, Module, or UI).
4. Name your script and press **Enter**.

## Writing Your First Script

Let's craft a straightforward script printing a greeting message when a player enters the game:

```lua
-- This script prints the player's name when they join the game
  scene.PlayerJoined:Connect(function(scene, player)
      print("Welcome, " .. player.name .. "!")
  end)
```

## Attaching Scripts to Objects

After scripting:

1. Right-click the `Hierarchy` panel.
2. Select **3D Object > Create Empty** to make an empty game object.
3. Rename it to `PlayerManager`.
4. Pick the `PlayerManager` object in the `Hierarchy` panel.
5. Drag your script onto the `PlayerManager` object in the `Inspector` panel.

## Testing Your Script

To test:

1. Hit **Play** in Unity to enter Play Mode.
2. Watch the console for the greeting message when a player joins.

## Conclusion

Kudos on writing your first Lua script in Highrise! Scripts empower you to craft dynamic and interactive experiences in your worlds. With continued practice and exploration of scripting concepts, you'll unlock endless possibilities for your game development journey. 🚀