# Client Scripts

Client scripts govern local player interactions and behaviors on the client-side. They manage player input, movement, UI elements, visual effects, and animations, enhancing player immersion in the game world with interactive experiences.

## Client Script Structure

In Highrise Studio, client scripts are written in Lua and adhere to a structured format. They comprise functions triggered by events or actions. Below is a basic example of a client script printing a message upon initialization:

```lua
function self:Awake()
  print("Client initialized")
end

function self:Start()
  print("Client started")
end

function self:Update()
  -- Update function called every frame
end
```

In this script:

- `Awake`: Called during client initialization.
- `print`: Outputs messages to the console.
- `Start`: Called at client start.
- `Update`: Called every frame for game state updates and actions.

## Use Cases

Client scripts are commonly used for the following purposes:

- **Player Input**: Manage movement, interactions, and actions.
- **User Interface**: Handle menus, health bars, and notifications.
- **Visual Effects**: Implement animations, particle systems, and visual effects.
- **Audio**: Control playback and sound effects.
- **Networking**: Manage client-side networking and server communication.

By leveraging client scripts, you can create dynamic and responsive gameplay experiences that captivate players and immerse them in your game world.

## Do and Don't

In this table, we summarize the best practices and common pitfalls when working with client scripts:

| Do                                       | Don't                                    |
|------------------------------------------|------------------------------------------|
| Use client scripts for local player interactions and behaviors. | Use client scripts for server-side logic or data storage. |
| Implement player input handling and user interface interactions. | Implement server communication or data synchronization in client scripts. |
| Optimize client scripts for performance and responsiveness. | Overload client scripts with unnecessary computations or heavy processing. |
| Leverage client scripts to enhance player immersion and engagement. | Rely solely on client scripts for multiplayer interactions or game logic. |

**Real Example:**

```lua
--!Type(Client)
local myRadio = nil;

function self:Awake()
  myRadio = self:GetComponent("Radio")
end

function self:Start()
  myRadio.SetActive(true)
end
```

In this example, the client script initializes a radio component and activates it when the client starts, enabling the player to interact with the radio in the game world.

Now if you were to run this script as a `Server` script, the script will not work as intended and may cause errors due to the fact that you cannot directly modify object components that belong to individual clients. This is why it is important to use the correct script type for the intended functionality.

By following these guidelines and best practices, you can effectively utilize client scripts to create engaging and interactive gameplay experiences in your game projects.

# Video Preview
<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/S1qvp1cbKeE" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>