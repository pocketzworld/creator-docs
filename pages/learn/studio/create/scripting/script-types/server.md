# Server Scripts

Server scripts manage game logic, data storage, and multiplayer interactions on the server-side. They handle core gameplay mechanics, AI behavior, physics calculations, and server-client communication, ensuring consistency and security in multiplayer environments.

## Server Script Structure

In Highrise Studio, server scripts are written in Lua and follow a structured format. They consist of functions triggered by events or actions. Below is a basic example of a server script printing a message upon initialization:

```lua
function self:Awake()
  print("Server initialized")
end

function self:Start()
  print("Server started")
end

function self:Update()
  -- Update function called every frame
end
```

In this script:

- `Awake`: Called during server initialization.
- `print`: Outputs messages to the console.
- `Start`: Called at server start.
- `Update`: Called every frame for game state updates and actions.

## Use Cases

Server scripts are commonly used for the following purposes:

- **Game Logic**: Implementing core gameplay mechanics and rules.
- **Data Storage**: Managing player data, inventory, and game state.
- **Multiplayer Interactions**: Handling server-client communication and synchronization.
- **AI Behavior**: Controlling non-player characters and artificial intelligence.
- **Physics Calculations**: Processing physics simulations and collisions.

By utilizing server scripts, you can create robust and secure game environments that support multiplayer interactions, AI behavior, and complex game mechanics.

## Do and Don't

In this table, we summarize the best practices and common pitfalls when working with server scripts:

| Do                                       | Don't                                    |
|------------------------------------------|------------------------------------------|
| Use server scripts for game logic, data storage, and multiplayer interactions. | Use server scripts for client-side interactions or visual effects. |
| Implement core gameplay mechanics, AI behavior, and physics calculations in server scripts. | Implement client input handling or user interface interactions in server scripts. |
| Optimize server scripts for performance and security. | Overload server scripts with unnecessary computations or heavy processing. |
| Leverage server scripts to ensure consistency and security in multiplayer environments. | Rely solely on server scripts for client-side interactions or visual effects. |

**Real Example:**

```lua
--!Type(Server)
local playerHealth = 100;

function self:Awake()
  print("Player health: " .. playerHealth) -- Output: Player health: 100
end

function self:Update()
  playerHealth = playerHealth - 1
  print("Player health: " .. playerHealth) -- Output: Player health: 99, 98, 97, ...
end
```

By following best practices and leveraging server scripts effectively, you can create engaging and immersive game experiences that captivate players and bring your creative vision to life. Experiment with server scripts to explore their capabilities and enhance your game development process.