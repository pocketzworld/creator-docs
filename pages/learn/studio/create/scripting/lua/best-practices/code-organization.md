# Code Organization

When writing Lua scripts for your Highrise Studio projects, it's essential to organize your code effectively to improve readability, maintainability, and reusability. Proper code organization can help you manage complex scripts, collaborate with other developers, and debug issues more efficiently.

Here are some best practices for organizing your Lua scripts in Highrise Studio:

## 1. Categorized Sections

When you start a Unity project, you may have a lot of scripts that handle different aspects of your game, such as player movement, enemy behavior, UI interactions, and more. To keep your scripts organized, consider categorizing them into sections based on their functionality or purpose.

> All scripts must be placed in the `Assets` folder of your project to be recognized by Highrise Studio.

Here's an example of how you can categorize your Lua scripts:

```plaintext
Assets/
├── Scripts/
│   ├── Player/
│   │   ├── PlayerController.lua
│   │   ├── PlayerHealth.lua
│   ├── Enemy/
│   │   ├── EnemyAI.lua
│   │   ├── EnemyHealth.lua
│   ├── UI/
│   │   ├── UIManager.lua
|   |   ├── UIManager.uxml
|   |   ├── UIManager.uss
```

<Note type="warning">
When naming your Lua scripts, make sure to use descriptive names that reflect their purpose or functionality. Avoid generic names like `script1.lua` or `new_script.lua` that do not provide meaningful context.

You may also notice that sometimes the script doesn't work as expected and this is because some scripts in Unity or Highrise Studio have similar names and this can cause conflicts. To avoid this, you can use a prefix or suffix to differentiate your scripts.
</Note>

## 2. Modular Design

Modular design involves breaking down your Lua scripts into smaller, reusable components that perform specific tasks or functions. By creating modular scripts, you can improve code reusability, maintainability, and testability. Each module should focus on a single responsibility and interact with other modules through well-defined interfaces.

Are you not familiar with `Module` type scripts? You can learn more about it [here](https://create.highrise.game/learn/studio/create/scripting/script-types/module).

Here's an example of a modular design for Lua scripts:

```plaintext
Assets/
├── Scripts/
│   ├── Player/
│   │   ├── PlayerController.lua
│   │   ├── PlayerHealth.lua
|   ├── Modules/
|   |   ├── Utils.lua
|   |   ├── Constants.lua
```

In this example, the `Utils.lua` module contains utility functions that can be shared across different scripts, while the `Constants.lua` module defines global constants used throughout the project.

## 3. Comments and Documentation

Adding comments and documentation to your Lua scripts is crucial for understanding the purpose, functionality, and usage of your code. Comments help explain complex logic, provide context for future modifications, and make it easier for other developers to collaborate on the project.

Learn more about [commenting in Lua](https://create.highrise.game/learn/studio/create/scripting/lua/features/comments).

Here's an example of how you can document your Lua scripts:

```lua
-- PlayerController.lua
-- Handles player movement and input

function movePlayer(direction)
    -- Move the player in the specified direction
end

function hitPlayer(damage)
    -- Reduce the player's health by the specified damage amount
end

--#TODO: Implement jump functionality
```

By adding comments and documentation to your Lua scripts, you can improve code readability, maintainability, and collaboration among developers.

## 4. Naming Conventions

Follow consistent naming conventions for variables, functions, and other identifiers in your Lua scripts. Descriptive names can help you understand the purpose of each element and make your code more readable and maintainable.

Learn more about [naming conventions in Lua](https://create.highrise.game/learn/studio/create/scripting/lua/best-practices/naming-conventions).

## Summary

Organizing your Lua scripts effectively is essential for creating maintainable, readable, and reusable code in Highrise Studio. By categorizing scripts, adopting a modular design, adding comments and documentation, defining a clear file structure, and following naming conventions, you can enhance the quality of your Lua scripts and streamline your development process.




