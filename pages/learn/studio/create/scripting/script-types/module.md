# Module Scripts

Module scripts contain reusable functions and variables that can be shared across multiple scripts. They serve as a library of common code snippets that can be imported and used in other scripts, enhancing code modularity and reusability.

> Note: `module` scripts, like `client/server` scripts run on both the `client` and `server`.  
> This will allow use of client/server functions: `ClientAwake()`,`ServerAwake()`, etc.


## Module Script Structure

In Highrise Studio, module scripts are written in Lua and follow a structured format. They consist of functions and variables that can be accessed by other scripts. Below is a basic example of a module script defining a function to calculate the square of a number:

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

## Use Cases

Module scripts are commonly used for the following purposes:

- **Code Reusability**: Defining common functions and variables that can be shared across multiple scripts.
- **Modularity**: Encapsulating related code snippets into a single script for better organization.
- **Event Handling**: Creating shared events that can be triggered and listened to by other scripts.
- **Network Values**: Storing and synchronizing game state data across the client and server.

By leveraging module scripts, you can streamline your game development process, reduce redundancy in your codebase, and create a more maintainable and scalable project structure.

## Importing Module Scripts

To use functions and variables defined in a module script, you can import the module into another script just by requiring it. For example, if our module script is named `MathUtils`, we can import it in another script as follows:

```lua
--!Type(Client)
local MathUtils = require("MathUtils")

function self:Awake()
  local result = MathUtils.square(5)
  MathUtils.printMessage("Hello, World!")
end
```

Now it's important to understand that when importing a module script, the path to the script should be relative to the script importing it. For instance, if the `MathUtils` script is in the same directory as the importing script, you can simply use `require("MathUtils")`. If the `MathUtils` script is in a subdirectory, you can still require it using only the name of the script, like `require("MathUtils")`.

## Do and Don't

In this table, we summarize the best practices and common pitfalls when working with module scripts:

| Do                                       | Don't                                    |
|------------------------------------------|------------------------------------------|
| Use module scripts for defining reusable functions and variables. | Use module scripts for game logic or player interactions. |
| Encapsulate related code snippets into module scripts for better organization. | Define script-specific functions and variables in module scripts. |
| Create shared events and network values in module scripts for cross-script communication. | Overload module scripts with unnecessary functions or variables. |
| Import module scripts into other scripts to reuse their functionality. | Rely solely on module scripts for core game mechanics or AI behavior. |

## Conclusion

Module scripts play a crucial role in enhancing code modularity, reusability, and organization in your game development projects. By defining common functions, variables, events, and network values in module scripts, you can create a more maintainable and scalable codebase that facilitates collaboration and accelerates the development process. Experiment with module scripts to streamline your workflow and optimize your game development experience.