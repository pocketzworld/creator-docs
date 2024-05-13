# Tables

## Introduction

Tables in Lua are versatile data structures that can store collections of values, such as numbers, strings, booleans, and other tables. They are used to represent arrays, dictionaries, lists, and objects in Lua scripts. Understanding how to work with tables is essential for organizing data, managing resources, and implementing complex data structures in your Highrise world.

## Table Literals

In Lua, you can define tables using table literals, which are key-value pairs enclosed in curly braces `{}`. Here are examples of table literals in Lua:

- Empty Table: `{}`
- Table with Values: `{ key1 = value1, key2 = value2 }`

```lua
local emptyTable = {}
local player = { name = "Alice", level = 5, health = 100 }
```

You can use tables to store player data, item attributes, game settings, and other structured information in your Lua scripts. By assigning key-value pairs to tables, you can organize data efficiently and access specific values based on their keys.

## Table Access

You can access table values using keys or indices. To access a value in a table, you can use the key or index within square brackets `[]`. Here are examples of table access in Lua:

- Access by
  Key: `table
  ["key"]`
  ```lua
  local player = { name = "Alice", level = 5, health = 100 }
  local playerName = player["name"] --> "Alice"
  ```
- Access by Index: `table[index]`
  ```lua
  local numbers = { 1, 2, 3, 4, 5 }
  local thirdNumber = numbers[3] --> 3
  ```
- Access by Variable: `table[variable]`
  ```lua
  local key = "level"
  local player = { name = "Alice", level = 5, health = 100 }
  local playerLevel = player[key] --> 5
  ```

By accessing table values, you can retrieve specific data, update values, and perform operations based on the contents of the table. Tables provide a flexible way to store and manipulate structured data in your Lua scripts.

## Table Methods

Lua provides built-in table methods that allow you to manipulate and transform table values. These methods can be used to add elements, remove entries, iterate over items, and perform other table-related operations. Here are examples of common table methods in Lua:

- `table.insert`: Inserts an element into a table.
  ```lua
  local numbers = { 1, 2, 3 }
  table.insert(numbers, 4) -- Adds the element 4 at the end
  ```

- `table.remove`: Removes an element from a table.
  ```lua
  local numbers = { 1, 2, 3 }
  table.remove(numbers, 2) -- Removes the element at index 2
  ```

- `pairs`: Iterates over key-value pairs in a table.
  ```lua
  local player = { name = "Alice", level = 5, health = 100 }
  for key, value in pairs(player) do
      print(key, value) -- name Alice, level 5, health 100
  end
  ```

- `ipairs`: Iterates over array elements in a table.
  ```lua
  local numbers = { 1, 2, 3, 4, 5 }
  for index, value in ipairs(numbers) do
      print(index, value) -- 1 1, 2 2, 3 3, 4 4, 5 5
  end
  ```

By using table methods, you can modify table contents, manage data structures, iterate over elements, and enhance the functionality of your Lua scripts.

## Conclusion

Tables are powerful data structures that enable you to organize, access, and manipulate data in Lua. By using tables to store collections of values, you can create arrays, dictionaries, lists, and objects that represent various aspects of your Highrise world. Experiment with table literals, access methods, and iteration techniques to master the art of working with tables and build dynamic gameplay experiences for players.
