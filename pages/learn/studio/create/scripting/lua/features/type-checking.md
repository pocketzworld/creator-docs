# Type Checking

Lua supports dynamic typing, which means that variables do not have a fixed data type. The data type of a variable can change during script execution. This flexibility allows you to store different types of values in the same variable.

## Defining a Type

Use the `type` function to determine the data type of a variable. The `type` function returns a string representing the data type of the variable.

Here's an example of using the `type` function in Lua:

```lua
local x = 10
local y = "Hello"

print(type(x)) --> number
print(type(y)) --> string
```

In this example, the `type` function is used to determine the data type of variables `x` and `y`. The output shows that `x` is a number and `y` is a string.

## Type Coercion

Lua performs type coercion when necessary to convert values between different data types. For example, Lua automatically converts numbers to strings when concatenating them with strings.

Here's an example of type coercion in Lua:

```lua
local x = 10
local y = "Hello"

print(x .. y) --> 10Hello
```

In this example, the number `10` is automatically converted to a string when concatenated with the string `"Hello"`. The result is the string `"10Hello"`.