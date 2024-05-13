# Booleans

## Introduction

Booleans in Lua are a data type that represents logical values, such as `true` and `false`. Booleans are used to evaluate conditions, control program flow, and make decisions based on the truth or falsity of expressions in Lua scripts. Understanding how to work with booleans is essential for implementing conditional logic, branching behavior, and event handling in your Highrise world.

## Boolean Literals

In Lua, you can define booleans using boolean literals, which are keywords that represent the logical values `true` and `false`. Boolean literals are used to express the truth or falsity of conditions, comparisons, and logical operations in Lua scripts. Here are examples of boolean literals in Lua:

- `true`: Represents the logical value `true`.
- `false`: Represents the logical value `false`.

```lua
local isReady = true
local hasKey = false
```

By using boolean literals, you can store and evaluate logical states, check conditions, and control the behavior of your Lua scripts based on the truth values of expressions.

## Boolean Operators

Lua provides several boolean operators that allow you to combine, compare, and manipulate boolean values in expressions. Boolean operators are used to perform logical operations, evaluate conditions, and determine the truth or falsity of expressions. Here are examples of common boolean operators in Lua:

- `and`: Logical AND operator.
  ```lua
  local isTrue = true
  local isFalse = false
  local result = isTrue and isFalse --> false
  ```
- `or`: Logical OR operator.
  ```lua
  local isTrue = true
  local isFalse = false
  local result = isTrue or isFalse --> true
  ```
- `not`: Logical NOT operator.
  ```lua
  local isTrue = true
  local result = not isTrue --> false
  ```
- `==`: Equality operator.
  ```lua
  local value1 = 42
  local value2 = 42
  local isEqual = value1 == value2 --> true
  ```
- `~=`: Inequality operator.
  ```lua
  local value1 = 42
  local value2 = 24
  local isNotEqual = value1 ~= value2 --> true
  ```
- `>`: Greater than operator.
  ```lua
  local number1 = 10
  local number2 = 5
  local isGreater = number1 > number2 --> true
  ```
- `<`: Less than operator.
  ```lua
  local number1 = 5
  local number2 = 10
  local isLess = number1 < number2 --> true
  ```
- `>=`: Greater than or equal to operator.
  ```lua
  local number1 = 10
  local number2 = 10
  local isGreaterOrEqual = number1 >= number2 --> true
  ```
- `<=`: Less than or equal to operator.
  ```lua
  local number1 = 5
  local number2 = 5
  local isLessOrEqual = number1 <= number2 --> true
  ```
- `and then`: Short-circuit AND operator.
  ```lua
  local isTrue = true
  local isFalse = false
  local result = isTrue and then isFalse --> false
  ```
- `or else`: Short-circuit OR operator.
  ```lua
  local isTrue = true
  local isFalse = false
  local result = isTrue or else isFalse --> true
  ```
By using boolean operators, you can combine conditions, compare values, and control the flow of your Lua scripts based on logical expressions and truth values.

## Conditional Statements

Conditional statements in Lua allow you to execute code blocks based on the truth or falsity of conditions. Conditional statements are used to implement branching behavior, handle different scenarios, and control the flow of your Lua scripts based on logical expressions. Here are examples of conditional statements in Lua:

- `if` Statement: Executes a block of code if a condition is true.
  ```lua
  local isReady = true

  if isReady then
      print("The game is ready to play!")
  end
  ```
- `if-else` Statement: Executes one block of code if a condition is true and another block if it is false.
  ```lua
  local hasKey = false

  if hasKey then
      print("You have the key!")
  else
      print("You need to find the key.")
  end
  ```

By using conditional statements, you can implement decision-making logic, handle different scenarios, and control the behavior of your Lua scripts based on the evaluation of conditions.

## Conclusion

Understanding booleans, boolean literals, boolean operators, and conditional statements in Lua is essential for implementing conditional logic, branching behavior, and event handling in your Highrise world. By using booleans effectively, you can evaluate conditions, control program flow, and make decisions based on the truth or falsity of expressions in your Lua scripts.