# Strings

## Introduction

Strings in Lua are sequences of characters enclosed in single or double quotes. They are used to represent text, messages, file paths, and other character data in Lua scripts. Understanding how to work with strings is essential for manipulating text, formatting output, and processing user input in your Highrise world.

## String Literals

In Lua, you can define strings using string literals, which are text values enclosed in single or double quotes. Here are examples of string literals in Lua:

- Single-Quoted String: `'Hello, Lua!'`
- Double-Quoted String: `"Welcome to Highrise!"`

```lua
local singleQuote = 'Hello, Lua!'
local doubleQuote = "Welcome to Highrise!"
```

You can use strings to store player names, dialogues, item descriptions, and other textual content in your Lua scripts. By assigning string values to variables, you can manage text data efficiently and create engaging narratives in your Highrise world.

## String Concatenation

Strings in Lua can be concatenated using the `..` operator to combine multiple strings into a single string. String concatenation allows you to build longer messages, format output, and construct dynamic text content. Here are examples of string concatenation in Lua:

- Concatenation: `string1 .. string2`
  ```lua
  local greeting = "Hello, "
  local playerName = "Alice"
  local message = greeting .. playerName .. "!" --> "Hello, Alice!"
  ```

By concatenating strings, you can create personalized messages, generate dynamic labels, and customize text content based on player interactions in your Highrise world.

## String Methods

Lua provides built-in string methods that allow you to manipulate and transform string values. These methods can be used to search for substrings, extract characters, convert case, and perform other string-related operations. Here are examples of common string methods in Lua:

- `string.upper`: Converts a string to uppercase.
  ```lua
  local text = "hello lua"
  local upperText = string.upper(text) --> "HELLO LUA"
  ```
- `string.lower`: Converts a string to lowercase.
  ```lua
  local text = "Hello Lua"
  local lowerText = string.lower(text) --> "hello lua"
  ```
- `tostring`: Converts a value to a string.
  ```lua
  local number = 42
  local text = tostring(number) --> "42"
  ```
- `string.sub`: Extracts a substring from a string.
  ```lua
  local text = "Hello, Lua!"
  local subText = string.sub(text, 1, 5) --> "Hello"
  ```
- `string.find`: Finds the position of a substring in a string.
  ```lua
  local text = "Hello, Lua!"
  local position = string.find(text, "Lua") --> 8
  ```
- `string.len`: Returns the length of a string.
  ```lua
  local text = "Hello, Lua!"
  local length = string.len(text) --> 11
  ```

By using string methods, you can modify text appearance, validate input, parse data, and enhance the interactivity of your Lua scripts.

## Conclusion

Strings are a fundamental data type in Lua scripting and play a crucial role in managing textual content in your Highrise world. By working with strings, you can create dialogues, display messages, format output, and interact with players through text-based interactions.