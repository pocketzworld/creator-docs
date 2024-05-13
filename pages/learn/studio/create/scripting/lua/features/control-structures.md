# Control Structures

Control structures are used to control the flow of a program. They are used to execute a block of code based on a condition. Lua has the following control structures:

- `if` statement
- `if...else` statement
- `if...elseif...else` statement
- `while` loop
- `repeat...until` loop
- `for` loop

Understanding control structures is essential for writing dynamic and interactive scripts in Highrise Studio. By using control structures effectively, you can create conditional behaviors, loop through data, and manage program flow based on player interactions.

## If Statement

The `if` statement is used to execute a block of code if a condition is `true`. If the condition is `false`, the block of code is skipped. Here's the syntax of the `if` statement in Lua:

```lua
if condition then
    -- Code block to execute if condition is true
end
```

- `condition`: A boolean expression that determines whether the code block should be executed.

Here's an example of using the `if` statement in Lua:

```lua
local score = 100

if score > 50 then
    print("High score achieved!")
end
```

In this example, the code block inside the `if` statement is executed because the condition `score > 50` is `true`. The message "High score achieved!" is printed to the console.

## If...Else Statement

The `if...else` statement is used to execute one block of code if a condition is `true` and another block of code if the condition is `false`. Here's the syntax of the `if...else` statement in Lua:

```lua
if condition then
    -- Code block to execute if condition is true
else
    -- Code block to execute if condition is false
end
```

- `condition`: A boolean expression that determines which code block should be executed.

Here's an example of using the `if...else` statement in Lua:

```lua
local score = 30

if score > 50 then
    print("High score achieved!")
else
    print("Try again!")
end
```

In this example, the code block inside the `else` statement is executed because the condition `score > 50` is `false`. The message "Try again!" is printed to the console.

## If...Elseif...Else Statement

The `if...elseif...else` statement is used to execute different blocks of code based on multiple conditions. It allows you to check multiple conditions sequentially and execute the corresponding code block when a condition is `true`. Here's the syntax of the `if...elseif...else` statement in Lua:

```lua
if condition1 then
    -- Code block to execute if condition1 is true
elseif condition2 then
    -- Code block to execute if condition2 is true
else
    -- Code block to execute if all conditions are false
end
```

- `condition1`, `condition2`: Boolean expressions that determine which code block should be executed.

Here's an example of using the `if...elseif...else` statement in Lua:

```lua
local score = 70

if score > 90 then
    print("Excellent!")
elseif score > 60 then
    print("Good job!")
else
    print("Keep practicing!")
end
```

In this example, the code block inside the `elseif` statement is executed because the condition `score > 60` is `true`. The message "Good job!" is printed to the console.

## While Loop

The `while` loop is used to repeatedly execute a block of code as long as a condition is `true`. The loop continues to execute until the condition becomes `false`. Here's the syntax of the `while` loop in Lua:

```lua
while condition do
    -- Code block to execute while condition is true
end
```

- `condition`: A boolean expression that determines whether the loop should continue executing.

Here's an example of using the `while` loop in Lua:

```lua
local count = 1

while count <= 5 do
    print("Count: " .. count)
    count = count + 1
end
```

In this example, the loop prints the value of `count` and increments it by `1` until `count` is greater than `5`. The loop stops when `count` reaches `6`.

## Repeat...Until Loop

The `repeat...until` loop is similar to the `while` loop, but it executes the code block at least once before checking the condition. The loop continues to execute until the condition becomes `true`. Here's the syntax of the `repeat...until` loop in Lua:

```lua
repeat
    -- Code block to execute at least once
until condition
```

- `condition`: A boolean expression that determines whether the loop should continue executing.

Here's an example of using the `repeat...until` loop in Lua:

```lua
local count = 1

repeat
    print("Count: " .. count)
    count = count + 1
until count > 5
```

In this example, the loop prints the value of `count` and increments it by `1` until `count` is greater than `5`. The loop stops when `count` reaches `6`.

## For Loop

The `for` loop is used to iterate over a range of values or elements. It allows you to execute a block of code a specific number of times. Here's the syntax of the `for` loop in Lua:

```lua
for variable = start, stop, step do
    -- Code block to execute for each iteration
end
```

- `variable`: The loop variable that changes with each iteration.
- `start`: The initial value of the loop variable.
- `stop`: The final value of the loop variable.
- `step`: The amount by which the loop variable changes in each iteration.

Here's an example of using the `for` loop in Lua:

```lua
for i = 1, 5, 1 do
    print("Count: " .. i)
end
```

In this example, the loop variable `i` starts at `1` and increments by `1` until it reaches `5`. The loop prints the value of `i` for each iteration.

## Tips for Using Control Structures

Here are some tips for using control structures effectively in Lua scripts:

- **Use meaningful conditions**: Ensure that the conditions in your control structures are clear and relevant to the context of your script.
- **Avoid infinite loops**: Be careful when using loops to prevent infinite loops that can cause your script to hang or crash.
- **Test your code**: Test your control structures with different inputs to verify that they work as expected.
- **Use comments**: Add comments to explain the purpose of your control structures and how they affect the flow of your script.

By following these tips, you can write well-structured Lua scripts with effective control structures that enhance the interactivity and gameplay experience of your Highrise worlds.
