# Scope

In scripting, a block of code is the body of a [control structure](https://create.highrise.game/learn/studio/create/scripting/lua/features/control-structures) or a [function](https://create.highrise.game/learn/studio/create/scripting/lua/features/functions). The scope of a variable refers to the region of code where the variable is accessible and can be used. In Lua, variables have different scopes based on how they are declared.

[variables](https://create.highrise.game/learn/studio/create/scripting/lua/features/variables) and functions have global scope by default. This means they can be accessed from anywhere in the script. However, you can limit the scope of variables and functions by using the `local` keyword.

## Local Variables

Variables declared with the `local` keyword are local to the block where they are defined. Local variables are accessible only within their scope and are not visible outside the block. This means that local variables are not accessible from other blocks of code, including nested blocks.

Here's an example of local variables in Lua:

```lua
local x = 10 -- Local variable
local y = 20 -- Local variable

function myFunction()
    local z = 30 -- Local variable
    print(x, y, z) -- Access local variables
end

myFunction() -- Call the function
print(x, y, z) -- Error: z is not accessible
```

In this example, `x` and `y` are local variables declared outside the function `myFunction`. The variable `z` is a local variable declared inside `myFunction`. When `myFunction` is called, it can access `x`, `y`, and `z`. However, the variable `z` is not accessible outside the function, as it is local to the function's block.

## Global Variables

Variables declared without the `local` keyword are global and can be accessed from anywhere in the script. Global variables have a wider scope and can be modified by any part of the script. Global variables are accessible from all blocks of code, including nested blocks.

Here's an example of global variables in Lua:

```lua
x = 10 -- Global variable
y = 20 -- Global variable

function myFunction()
    z = 30 -- Global variable
    print(x, y, z) -- Access global variables
end

myFunction() -- Call the function
print(x, y, z) -- Access global variables
```

In this example, `x` and `y` are global variables declared outside the function `myFunction`. The variable `z` is a global variable declared inside `myFunction`. When `myFunction` is called, it can access `x`, `y`, and `z`. Additionally, the global variables `x`, `y`, and `z` are accessible outside the function as well.

## Why Use Local Variables?

Using local variables is a good practice in Lua scripting for the following reasons:

- **Encapsulation**: Local variables encapsulate data within specific blocks of code, preventing unintended modifications and conflicts.
- **Memory Management**: Local variables are automatically destroyed when their scope ends, helping manage memory efficiently.
- **Readability**: Local variables make code more readable by limiting the visibility of variables to relevant sections of the script.
- **Debugging**: Local variables reduce the chances of errors and make it easier to identify and fix issues in the script.

By using local variables effectively, you can improve the structure, performance, and maintainability of your Lua scripts in Highrise.