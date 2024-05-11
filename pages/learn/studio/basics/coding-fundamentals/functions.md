# Functions

## Introduction

Functions are code blocks that perform specific tasks when called. They help organize your code, reduce redundancy, and improve readability. Understanding functions is essential for creating modular and maintainable scripts in your Highrise world.

## Defining Functions

In Lua, you can define functions using the `function` keyword followed by the function name and parameters. Here's the general syntax for defining a function:

```lua
function functionName(parameter1, parameter2, ...)
    -- Code block to execute
end
```

- `function`: Keyword indicating the start of a function definition.
- `functionName`: Name of the function you want to define.
- `parameter1, parameter2, ...`: Input values (parameters) the function expects.

For example, to define a function that prints a message based on the player's name:

```lua
function greetPlayer(playerName)
    print("Hello, " .. playerName .. "!")
end
```
[Learn more about input values and parameters](https://www.lua.org/pil/5.2.html).
## Calling Functions

Once you've defined a function, you can call it from other parts of your script. To call a function, use the function name followed by parentheses and any required arguments. Here's an example of calling the `greetPlayer` function:

```lua
greetPlayer("Alice")
```

When you call a function, Lua executes the code block defined in the function, passing the specified arguments to the function parameters.

## Return Values

Functions can return values to the calling code block. To specify a return value, use the `return` keyword followed by the value you want to return. Here's an example of a function that calculates the sum of two numbers and returns the result:

```lua
function addNumbers(a, b)
    return a + b
end
```

You can capture the return value of a function by assigning it to a variable or using it directly in your script.

[Learn more about return values and multiple return values](https://www.lua.org/pil/5.1.html).

## Conclusion

Functions are a fundamental concept in Lua scripting and play a crucial role in structuring your code. By defining and calling functions, you can create reusable code blocks that perform specific tasks, enhancing the functionality and maintainability of your Highrise scripts. 

### Ready to level up your scripting skills? Let's explore [event handling](https://create.highrise.game/learn/studio/basics/coding-fundamentals/events) next! 🚀