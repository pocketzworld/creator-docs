# Control Structures

## Introduction

Control structures are statements that control the flow of code execution in a script. They determine which code blocks to execute based on conditions or loops. Understanding control structures is crucial for creating interactive and dynamic behavior in your Highrise world.

## Conditional Statements

Conditional statements allow you to execute code based on specific conditions. The most common conditional statement in Lua is the `if` statement, which evaluates an expression and executes a block of code if the condition is true. You can also use `else` and `elseif` to handle alternative scenarios.

### If Statement

The `if` statement has the following syntax:

```lua
if condition then
    -- Code block to execute if condition is true
end
```

For example, to check if a player's health is below a certain threshold and display a message:

```lua
local playerHealth = 50

if playerHealth < 25 then
    print("Low health! Take cover!")
end
```

### Else Statement

The `else` statement allows you to specify an alternative code block to execute if the `if` condition is false. It follows the `if` block and has the following syntax:

```lua
if condition then
    -- Code block to execute if condition is true
else
    -- Code block to execute if condition is false
end
```

For example, to display a message based on a player's health status:

```lua
local playerHealth = 75

if playerHealth < 25 then
    print("Low health! Take cover!")
else
    print("Health is good. Keep fighting!")
end
```

### Elseif Statement

The `elseif` statement allows you to check additional conditions after the initial `if` statement. It follows the `if` block and precedes the `else` block. The syntax is as follows:

```lua

if condition1 then
    -- Code block to execute if condition1 is true
elseif condition2 then
    -- Code block to execute if condition2 is true
else
    -- Code block to execute if all conditions are false
end
```

For example, to display different messages based on a player's health status:

```lua
local playerHealth = 50

if playerHealth < 25 then
    print("Low health! Take cover!")
elseif playerHealth < 50 then
    print("Health is moderate. Be cautious!")
else
    print("Health is good. Keep fighting!")
end
```

## Looping Structures

Looping structures allow you to repeat code blocks multiple times. The two primary loop structures in Lua are `for` and `while` loops.

### For Loop

The `for` loop is used to iterate over a range of values or elements. It has the following syntax:

```lua
for variable = startValue, endValue, step do
    -- Code block to execute
end
```

For example, to print numbers from 1 to 5:

```lua
for i = 1, 5 do
    print(i)
end
```

You can also specify a step value to increment by a different amount:

```lua
for i = 0, 10, 2 do
    print(i)
end
```

### While Loop

The `while` loop repeats a code block as long as a condition is true. It has the following syntax:

```lua
while condition do
    -- Code block to execute
end
```

For example, to count down from 5 to 1:

```lua
local countdown = 5

while countdown > 0 do
    print(countdown)
    countdown = countdown - 1
end
```

## Conclusion

Control structures are essential tools for creating dynamic and interactive behavior in your Highrise world. By using conditional statements and looping structures, you can control the flow of your scripts, respond to changing conditions, and create engaging gameplay experiences for players. Experiment with different control structures to enhance your scripting skills and bring your creative ideas to life.

### Ready to explore more scripting concepts? Learn about [functions](https://create.highrise.game/learn/studio/basics/coding-fundamentals/functions) to further expand your scripting knowledge. 🚀