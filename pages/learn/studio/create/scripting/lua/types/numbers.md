# Numbers

## Introduction

The `Number` type in Lua represents numerical values, including integers and floating-point numbers. Numbers are used to perform arithmetic operations, store quantities, and calculate values in Lua scripts. Understanding how to work with numbers is essential for implementing game logic, managing variables, and creating interactive experiences in Highrise Studio.

## Number Literals

In Lua, you can define numbers using numeric literals, which are numerical values written directly in the script code. Numeric literals can be integers or floating-point numbers, depending on the presence of a decimal point. Here are examples of number literals in Lua:

- Integer: `42`
- Floating-Point: `3.14`

```lua
local integer = 42
local pi = 3.14
```

You can use numbers to represent various quantities, such as health points, scores, positions, speeds, and more. By assigning numerical values to variables, you can store and manipulate data efficiently in your Lua scripts.

## Arithmetic Operations

Numbers in Lua can be used in arithmetic operations to perform calculations, manipulate values, and generate results. Lua supports standard arithmetic operators for addition, subtraction, multiplication, division, and more. Here are examples of arithmetic operations using numbers in Lua:

- Addition: `a + b`
  ```lua
  local sum = 3 + 5 --> 8
  ```
- Subtraction: `a - b`
  ```lua
  local difference = 10 - 3 --> 7
  ```
- Multiplication: `a * b`
  ```lua
  local product = 2 * 4 --> 8
  ```
- Division: `a / b`
  ```lua
  local quotient = 10 / 2 --> 5
  ```
- Modulus: `a % b`
  ```lua
  local remainder = 10 % 3 --> 1
  ```
- Exponentiation: `a ^ b`
  ```lua
  local power = 2 ^ 3 --> 8
  ```

By combining numbers with arithmetic operators, you can create complex calculations, implement game mechanics, and simulate dynamic behaviors in your Highrise world.

## Number Conversions

In Lua, you can convert numbers between integer and floating-point formats using type conversion functions. The `tonumber` function converts a value to a number, while the `math.floor` and `math.ceil` functions round numbers down and up, respectively. Here are examples of number conversions in Lua:

- Convert to Number: `tonumber("42")`
  ```lua
  local num = tonumber("42") --> 42
  ```
- Round Down: `math.floor(3.14)`
  ```lua
  local roundedDown = math.floor(3.14) --> 3
  ```
- Round Up: `math.ceil(3.14)`
  ```lua
  local roundedUp = math.ceil(3.14) --> 4
  ```
- Convert to Integer: `math.floor(3.14)`
  ```lua
  local integer = math.floor(3.14) --> 3
  ```
- Convert to Floating-Point: `tonumber("42.0")`
  ```lua
  local float = tonumber("42.0") --> 42.0
  ```

By converting numbers between different formats, you can adjust precision, format data, and perform calculations with the desired data type.

## Conclusion

Numbers are fundamental data types in Lua that play a crucial role in game development, mathematical computations, and interactive experiences. By working with numbers, you can implement game mechanics, manage variables, and create dynamic behaviors in your Highrise world.