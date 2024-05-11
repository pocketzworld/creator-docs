# Variables and Data Types

## Introduction

Variables and data types are foundational concepts in programming that enable you to work with different types of information in your scripts. By understanding how to declare variables and use common data types, you can create dynamic and interactive behavior in your Highrise worlds. Experiment with different data types and explore their capabilities to enhance your scripting skills and develop engaging gameplay experiences.

## What Are Variables?

In programming, a variable is a named storage location that holds a value or data. Variables allow you to store information temporarily and reference it throughout your script. By assigning values to variables, you can create dynamic and interactive behavior in your Highrise worlds. Variables can store various types of data, such as numbers, strings, and objects, depending on their data type.

## Declaring Variables

To declare a variable in Lua, you use the following syntax:

```lua
local variableName = value
```

- `local`: Indicates that the variable is local to the current scope.
- `variableName`: The name of the variable you want to declare.
- `value`: The initial value assigned to the variable.

For example, to declare a variable named `playerName` and assign it the value `"Alice"`, you would write:

```lua
local playerName = "Alice"
```

## Common Data Types

### 1. Numbers

Numbers in Lua can be integers or floating-point values. You can perform arithmetic operations on numbers, such as addition, subtraction, multiplication, and division. Here's an example of declaring a variable of type number:

```lua
local score = 100
```

### 2. Strings

Strings are sequences of characters enclosed in double or single quotes. You can concatenate strings using the `..` operator. Here's an example of declaring a variable of type string:

```lua
local greeting = "Hello, world!"
```

### 3. Booleans

Booleans represent logical values and can be either `true` or `false`. Booleans are commonly used in conditional statements and comparisons. Here's an example of declaring a variable of type boolean:

```lua
local isPlayerAlive = true
```

### 4. Tables

Tables are Lua's primary data structure and can store collections of key-value pairs. Tables are versatile and can represent arrays, dictionaries, and objects. Here's an example of declaring a table variable:

```lua
local player = {
    name = "Alice",
    score = 100,
    isAlive = true
}
```

### 5. Nil

`nil` is a special value in Lua that represents the absence of a value. Assigning a variable to `nil` effectively removes its value. Here's an example of declaring a variable with a `nil` value:

```lua
local playerName = nil
```
[learn more about data types](https://www.lua.org/pil/2.html)
## Conclusion

Variables and data types are foundational concepts in programming that enable you to work with different types of information in your scripts. By understanding how to declare variables and use common data types, you can create dynamic and interactive behavior in your Highrise worlds. Experiment with different data types and explore their capabilities to enhance your scripting skills and develop engaging gameplay experiences.

### Let's learn more about [control structures](https://create.highrise.game/learn/studio/basics/coding-fundamentals/control-structures) to further enhance your scripting knowledge. 🚀