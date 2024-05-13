# Functions

Functions are [blocks of code](https://create.highrise.game/learn/studio/create/scripting/lua/features/scope) that can be called from other parts of your script. They can take arguments and return values. Functions are a fundamental building block of Lua scripts.

## Basic Function

A function definition includes:

- The [scope](https://create.highrise.game/learn/studio/create/scripting/lua/features/scope) of the function (local or global).
- The `function` keyword.
- The name of the function in `camelCase`.
- The list of arguments enclosed in parentheses.
- The body of the function enclosed in `end`.

Here's an example of a basic function in Lua:

```lua
function greetPlayer(playerName)
    print("Hello, " .. playerName .. "!")
end
```

In this example, the `greetPlayer` function takes one argument `playerName` and prints a greeting message to the console.

## Parameters

Parameters are [variables](https://create.highrise.game/learn/studio/create/scripting/lua/features/variables) that are used to pass values to a function. You can define multiple parameters in a function separated by commas. Parameters are local variables that are accessible only within the function's scope.

Here's an example of a function with multiple parameters in Lua:

```lua
function addNumbers(a, b)
    print(a + b)
end

addNumbers(10, 20) -- Output: 30
addNumbers(5) -- Output: Error: attempt to perform arithmetic on a nil value
```

## Return Values

In the body of the function, the `return` statement is used to return a value from the function. The return value can be assigned to a variable or used directly in the script.

Here's an example of a function that returns a value in Lua:

```lua
-- This function returns one return value
local function calculateSum(a, b)
    local sum = a + b
    return sum
end

print(calculateSum(10, 20)) -- Output: 30

local result = calculateSum(5, 5)
print(result) -- Output: 10

-- This function returns multiple return values: sum and difference
local function calculateSumAndDifference(a, b)
    local sum = a + b
    local difference = a - b
    return sum, difference
end

-- Calling a function and expecting multiple return values
local sum, difference = calculateSumAndDifference(10, 5)
print(sum, difference) -- Output: 15 5
```

## Methods

Methods are functions that are members of an object or a table. They are called using the `:` operator and have an implicit `self` parameter that refers to the object or table.

Here's an example of a method in Lua:

```lua
local player = {
    name = "Alice",
    score = 100,
    isAlive = true,
    greet = function(self)
        print("Hello, " .. self.name .. "!")
    end
}

player:greet() -- Output: Hello, Alice!
```

In this example, the `greet` method is defined within the `player` table and uses the `self` parameter to access the `name` property of the `player` table.

## Anonymous Functions

Anonymous functions, also known as lambda functions, are functions without a name. They are defined using the `function` keyword and can be assigned to variables or passed as arguments to other functions.

Here's an example of an anonymous function in Lua:

```lua
local greetPlayer = function(playerName)
    print("Hello, " .. playerName .. "!")
end

greetPlayer("Bob") -- Output: Hello, Bob!
```

In this example, the `greetPlayer` function is an anonymous function that takes one argument `playerName` and prints a greeting message to the console.
