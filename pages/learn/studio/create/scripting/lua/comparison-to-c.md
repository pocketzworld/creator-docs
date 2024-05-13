# Lua and C# Comparison

## Introduction
Highrise Studio uses Lua as its scripting language, which is different from C# used in Unity. While both languages share similarities, they have distinct features and syntax that set them apart.

## Line Endings

You may have noticed that Lua uses semicolons (`;`) to separate statements, while C# uses semicolons at the end of each statement. In Lua, semicolons are optional, and line breaks are used to separate statements.

```lua
-- Lua
local message = "Hello, world!" --> No semicolon needed
print(message); --> Semicolon is optional
```

```csharp
// C#
string message = "Hello, world!"; // Semicolon is required
Console.WriteLine(message); // Semicolon is required
```

## Comments

Both Lua and C# support single-line and multi-line comments. In Lua, single-line comments start with `--`, while multi-line comments are enclosed in `--[[` and `]]`. In C#, single-line comments begin with `//`, and multi-line comments are enclosed in `/*` and `*/`.

**Comments In Lua**
```lua
-- This is a single-line comment

--[[
  Block comment
--]]
```

**Comments In C#**
```csharp
// This is a single-line comment

/*
  Block comment
*/
```

## Reserved Keywords

The following table compares some common reserved keywords in Lua and C#:

| Lua      | C#           |
|----------|--------------|
| `and`    | `&&`         |
| `break`  | `break`      |
| `do`     | `do`         |
| `else`   | `else`       |
| `elseif` | `else if`    |
| `if`     | `if`         |
| `then`   |              |
| `end`    | `}`          |
| `for`    | `for` or `foreach` |
| `function` | `function`  |
| `in`     | `in`         |
| `local`  | `var` (in most cases) |
| `nil`    | `null`       |
| `not`    | `!`          |
| `or`     | `||`         |
| `repeat` | `do while`   |
| `return` | `return`     |
| `until`  | `}` (end of `do while` loop in C#) |
| `while`  | `while`      |

## Data Types

### Strings

**Strings In Lua**
```lua
-- Multi-line string
local message = [[
  Hello, world!
]]

-- Concatenation
local name = "Alice"
local greeting = "Hello, " .. name .. "!"
local message = string.format("Hello, %s!", name)
```

**Strings In C#*
```csharp
// Multi-line string
string message = @"
  Hello, world!
";

// Concatenation
string name = "Alice";
string greeting = "Hello, " + name + "!";
string message = string.Format("Hello, {0}!", name);
```

## Tables (Arrays)

**Tables In Lua**
```lua
-- Creating a table
local fruits = {"apple", "banana", "orange"}

-- Accessing elements
print(fruits[1]) --> apple

-- Iterating over elements
for i, fruit in ipairs(fruits) do
    print(fruit)
end
```

**Arrays In C#**
```csharp
// Creating an array
string[] fruits = {"apple", "banana", "orange"};

// Accessing elements
Console.WriteLine(fruits[0]); // apple

// Iterating over elements
foreach (string fruit in fruits)
{
    Console.WriteLine(fruit);
}
```

## Operators

### Conditional Operators

In this table, we compare conditional operators in Lua and C#:

| Operator | Lua | C# |
|----------|-----|----|
| Equal to | `==` | `==` |
| Not equal to | `~=` | `!=` |
| Less than | `<` | `<` |
| Less than or equal to | `<=` | `<=` |
| Greater than | `>` | `>` |
| Greater than or equal to | `>=` | `>=` |
| Logical AND | `and` | `&&` |
| Logical OR | `or` | `||` |
| Logical NOT | `not` | `!` |

### Arithmetic Operators

In this table, we compare arithmetic operators in Lua and C#:

| Operator | Lua | C# |
|----------|-----|----|
| Addition | `+` | `+` |
| Subtraction | `-` | `-` |
| Multiplication | `*` | `*` |
| Division | `/` | `/` |
| Modulus | `%` | `%` |
| Exponentiation | `^` | `**` |

## Variables

**Variables In Lua**
In Lua, variables don't specify a data type and are dynamically typed. You can assign any value to a variable without declaring its type explicitly.
```lua
-- Declaring variables
local health = 100 -- Integer
local name = "Alice" -- String

-- "Public" declaration
playerName = "Bob"

-- "Private" declaration
local score = 0
```

**Variables In C#**

In C#, variables must specify a data type and are statically typed. You need to declare the type of a variable before assigning a value to it.
```csharp
// Declaring variables
int health = 100; // Integer
string name = "Alice"; // String

// "Public" declaration
public string playerName = "Bob";

// "Private" declaration
private int score = 0;
```

## Conditional Statements

**Conditional Statements In Lua**
```lua
-- One Condition
if health < 25 then
    print("Low health! Take cover!")
end

-- Multiple Conditions
if health < 25 then
    print("Low health! Take cover!")
elseif health < 50 then
    print("Health is moderate. Be cautious!")
else
    print("Health is good. Keep fighting!")
end
```

**Conditional Statements In C#**
```csharp
// One Condition
if (health < 25)
{
    Console.WriteLine("Low health! Take cover!");
}

// Multiple Conditions
if (health < 25)
{
    Console.WriteLine("Low health! Take cover!");
}
else if (health < 50)
{
    Console.WriteLine("Health is moderate. Be cautious!");
}
else
{
    Console.WriteLine("Health is good. Keep fighting!");
}
```

## Loops

### While and Repeat Loops

**While Loop In Lua**
```lua
local countdown = 5

while countdown > 0 do
    print(countdown)
    countdown = countdown - 1
end

-- Repeat Loop
repeat
    print(countdown)
    countdown = countdown - 1
until countdown == 0
```

**While Loop In C#**
```csharp
int countdown = 5;

while (countdown > 0)
{
    Console.WriteLine(countdown);
    countdown--;
}

// No direct equivalent to repeat loop in C#
do
{
    Console.WriteLine(countdown);
    countdown--;
} while (countdown > 0);
```

## Functions

### Generic Functions

**Functions In Lua**
```lua
function greetPlayer(playerName)
    print("Hello, " .. playerName .. "!")
end

greetPlayer("Alice")
```

**Functions In C#**
```csharp
void GreetPlayer(string playerName)
{
    Console.WriteLine("Hello, " + playerName + "!");
}

GreetPlayer("Alice");
```

### Variable Arguments Number

**Variable Arguments In Lua**
```lua
function addNumbers(...)
    local sum = 0
    for i, num in ipairs{...} do
        sum = sum + num
    end
    return sum
end

local total = addNumbers(1, 2, 3, 4, 5)
print(total) --> 15
```

**Variable Arguments In C#**
```csharp
int AddNumbers(params int[] numbers)
{
    int sum = 0;
    foreach (int num in numbers)
    {
        sum += num;
    }
    return sum;
}

int total = AddNumbers(1, 2, 3, 4, 5);
Console.WriteLine(total); // 15
```

### Named Arguments

**Named Arguments In Lua**
```lua
function greetPlayer(playerName, message)
    print(message .. ", " .. playerName .. "!")
end

greetPlayer{playerName = "Alice", message = "Hello"}
```

**Named Arguments In C#**
```csharp
void GreetPlayer(string playerName, string message)
{
    Console.WriteLine(message + ", " + playerName + "!");
}

GreetPlayer(playerName: "Alice", message: "Hello");
```

## Try-Catch Blocks

**Try-Catch In Lua**
```lua
local status, result = pcall(function()
    -- Code that may throw an error
end)

if not status then
    print("An error occurred: " .. result)
end
```

**Try-Catch In C#**
```csharp

try
{
    // Code that may throw an error
}
catch (Exception e)
{
    Console.WriteLine("An error occurred: " + e.Message);
}
```

## Conclusion

While Lua and C# share some similarities, they have distinct features and syntax that set them apart. Understanding these differences will help you transition between the two languages more effectively and write cleaner, more efficient code in Highrise Studio.
