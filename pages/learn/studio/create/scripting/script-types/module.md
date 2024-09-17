# Module Scripts

Module scripts contain reusable functions and variables that can be shared across multiple scripts. They are singleton instances, meaning that the same instance is shared across all scripts that import it. This makes module scripts ideal for managing shared state and creating centralized logic in your game.

> Note: `module` scripts, like `client/server` scripts run on both the `client` and `server`.  
> This will allow use of client/server functions: `ClientAwake()`,`ServerAwake()`, etc.


## Module Script Structure

In Highrise Studio, module scripts are written in Lua and follow a structured format. They consist of functions, variables, and shared state that can be accessed globally by other scripts. Here's an example of a module script:

<Note type="warning">
Variables and functions marked local in a module script will not be accessible outside the script. To make them accessible, remove the local keyword.
</Note>

```lua
--!Type(Module)

-- Events
mySharedEvent = Event.new("SharedEvent")
-- Variables
npcName = "NPC1"
-- Network Value
gameState = IntValue.new("GameState", 0)

-- Functions
function square(num)
  return num * num
end

function printMessage(message)
  print(message)
end
```

In this script:

- `mySharedEvent`: Custom event shared across scripts.
- `npcName`: Variable storing the name of an NPC.
- `gameState`: Network value for storing game state.
- `square`: Function to calculate the square of a number.
- `printMessage`: Function to print a message to the console.

Since module scripts act as singletons, variables like `npcName` and `gameState` will retain their state across different scripts that import this module.

## Use Cases

Module scripts are commonly used for:

- **Singleton State Management:** Managing shared state and variables that need to persist across different scripts.
- **Code Reusability:** Defining common functions and variables that can be shared across multiple scripts.
- **Modularity:** Encapsulating related code snippets into a single script for better organization.
- **Event Handling:** Creating shared events that can be triggered and listened to by other scripts.
- **Network Values:** Storing and synchronizing game state data across the client and server.

## Importing Module Scripts

To use functions and variables defined in a module script, you can import the module into another script by requiring it. For example:

```lua
--!Type(Client)
local MathUtils = require("MathUtils")

function self:Awake()
  local result = MathUtils.square(5)
  MathUtils.printMessage("Hello, World!")
end
```

Since module scripts are singletons, importing them multiple times will still refer to the same instance, meaning that any changes made in one script will be reflected in others that require the same module.

## Conclusion

Module scripts as singletons are essential for creating reusable and maintainable code in Highrise Studio. They enable centralized logic, shared state management, and allow for better organization and collaboration in game development projects.