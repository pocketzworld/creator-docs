# Variables

A **variable** is a name that holds a value. Variables can be [numbers](/learn/studio/create/scripting/lua/types/numbers), [strings](/learn/studio/create/scripting/lua/types/strings), [booleans](/learn/studio/create/scripting/lua/types/booleans), [tables](/learn/studio/create/scripting/lua/types/tables), [nil](/learn/studio/create/scripting/lua/types/nil) or other data types in Lua. By using variables, you can store and manipulate data in your scripts, making them dynamic and interactive.

## Variable Declaration

In Lua, variables are declared using the following syntax:

```lua
local variableName = value
```

- `local`: Keyword used to declare a local variable.
- `variableName`: Name of the variable (identifier).
- `value`: Initial value assigned to the variable.

Here are examples of variable declarations in Lua:

```lua
local playerName = "Alice"
local playerScore = 100
local isGameOver = false
local players = { "Alice", "Bob", "Charlie" }
```

By declaring variables, you can assign meaningful names to data values and access them throughout your Lua scripts.

## Best Practices

When working with variables in Lua, consider the following best practices:

- **Use descriptive names**: Choose variable names that reflect their purpose or content.
- **Follow naming conventions**: Use camelCase or snake_case for variable names to improve readability.
- **Initialize variables**: Assign initial values to variables to prevent unexpected behavior.
- **Avoid global variables**: Prefer local variables to limit their scope and prevent conflicts.
- **Update variables**: Modify variable values as needed to reflect changes in your script.

By following these best practices, you can write clean, maintainable, and efficient Lua scripts in Highrise Studio.

## Reserved Keywords

Lua has a set of reserved keywords that cannot be used as variable names. These keywords are part of the Lua language syntax and have specific meanings or functions. Avoid using reserved keywords as variable names to prevent conflicts and errors in your scripts.

Here are some common reserved keywords in Lua:

- `and`
- `break`
- `do`
- `else`
- `elseif`
- `end`
- `false`
- `for`
- `function`
- `if`
- `in`
- `local`
- `nil`
- `not`
- `or`
- `repeat`
- `return`
- `then`
- `true`
- `until`
- `while`

When choosing variable names, ensure they do not match any of the reserved keywords in Lua.

## Assigning Values

You can assign new values to variables by using the assignment operator `=`. This allows you to update the content of variables during script execution. Here's an example of assigning new values to variables in Lua:

```lua
local playerName = "Alice"
playerName = "Bob" -- Update playerName to "Bob"
```

By assigning values to variables, you can change their content dynamically based on game events, player interactions, or other conditions in your Highrise world.

## Assigning Values To Multiple Variables

You can assign values to multiple variables simultaneously in Lua by separating the variable names and values with commas. This technique, known as multiple assignment, allows you to initialize multiple variables in a single statement. Here's an example of assigning values to multiple variables in Lua:

```lua
local x, y, z = 10, 20, 30
```

By using multiple assignment, you can streamline variable initialization and improve the readability of your Lua scripts.

## Changing Variable Types

In Lua, variables are dynamically typed, meaning they can change their data type during script execution. This flexibility allows you to reassign variables with different types of values as needed. Here's an example of changing variable types in Lua:

```lua
local score = 100 -- Number
score = "High Score" -- String
```

By changing variable types, you can adapt variables to store different kinds of data and handle diverse scenarios in your Highrise world.

## Scope of Variables

Variables in Lua have different [scopes](https://create.highrise.game/learn/studio/create/scripting/lua/features/scope) that determine where they can be accessed and modified. The two main types of variable [scope](https://create.highrise.game/learn/studio/create/scripting/lua/features/scope) in Lua are:

- **Local Variables**: Variables declared with the `local` keyword are local to the block where they are defined. Local variables are accessible only within their scope and are not visible outside the block.

- **Global Variables**: Variables declared without the `local` keyword are global and can be accessed from anywhere in the script. Global variables have a wider scope and can be modified by any part of the script.

It is recommended to use local variables whenever possible to avoid naming conflicts and improve script performance. By limiting the scope of variables, you can create more modular and maintainable Lua scripts in Highrise Studio.

## Variable Naming Conventions

When naming variables in Lua, it is important to follow consistent naming conventions to enhance code readability and maintainability. Here are some common naming conventions for variables in Lua:

- **camelCase**: Begin with a lowercase letter and capitalize the first letter of each subsequent word. For example, `playerName`, `playerScore`, `isGameOver`.

- **snake_case**: Use lowercase letters and separate words with underscores. For example, `player_name`, `player_score`, `is_game_over`.

- **UPPERCASE**: Use all uppercase letters for constants or variables that should not be changed. For example, `MAX_PLAYERS`, `DEFAULT_SCORE`.

By adopting naming conventions, you can create clear, self-explanatory variable names that improve code quality and consistency in your Lua scripts.