# Comments

A **comment** is a line of text that is ignored by the Lua interpreter. Comments are used to document code and to make it more readable. There are two types of comments in Lua:

1. **Single-line comments**: Begin with `--` and extend to the end of the line.
2. **Multi-line comments**: Enclosed within `--[[` and `]]`.
3. **TODO**: Keep track of tasks that need to be completed.

## Single-Line Comments

You can define single-line comments using the `--` symbol. Anything following `--` on the same line is treated as a comment and is ignored by the Lua interpreter. Single-line comments are useful for adding short descriptions or notes to your code.

```lua
-- This is a single-line comment
print("Hello, Lua!") -- Print a greeting
```

## Multi-Line Comments

You can define multi-line comments using the `--[[` and `]]` symbols. Anything enclosed within `--[[` and `]]` is treated as a comment block and is ignored by the Lua interpreter. Multi-line comments are useful for adding longer descriptions, explanations, or documentation to your code.

```lua
--[[
  This is a multi-line comment block.
  It can span multiple lines and contain detailed information.
  Multi-line comments are useful for documenting code sections.
--]]
local function myCustomFunction()
end
```

## TODO Comments

In addition to regular comments, you can use **TODO comments** to mark tasks that need to be completed or issues that need to be addressed in your Lua scripts. TODO comments help you keep track of pending work and serve as reminders for future updates.

```lua
-- TODO: Complete the implementation of this function
local function myCustomFunction()
end
```

## Why Use Comments?

Comments are an essential part of programming for the following reasons:

- **Documentation**: Comments provide information about the purpose, functionality, and usage of code blocks.
- **Readability**: Comments make code more readable by explaining complex logic or algorithms.
- **Debugging**: Comments help identify and troubleshoot issues by providing context and insights into code behavior.
- **Collaboration**: Comments facilitate collaboration among team members by explaining code intent and design decisions.
- **Maintenance**: Comments assist in maintaining and updating code by documenting changes and improvements over time.

By using comments effectively, you can enhance the quality, clarity, and maintainability of your Lua scripts in Highrise.



