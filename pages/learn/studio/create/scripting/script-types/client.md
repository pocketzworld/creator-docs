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

--!SerializeField
local sparkles : ParticleSystem = nil

function self:Awake()
  self.gameObject:GetComponent(TapHandler).Tapped:Connect(function()
    sparkles:Play()
  end)
end
```

In this example, the client script plays a particle effect when the player taps the object (which needs a TapHandler and a Collider). The tap and the effect both happen on the player's own device, so only the player who tapped sees the sparkles.

This wouldn't work as a `Server` script: the server has no screen, so it never receives taps, and `ParticleSystem:Play` is client-only. To show the effect to every player, the client tells the server about the tap, and the server tells every client to play it, as [Client-Server Communication](https://create.highrise.game/learn/studio/create/scripting/advanced/client-server-communication) shows.

By following these guidelines and best practices, you can effectively utilize client scripts to create engaging and interactive gameplay experiences in your game projects.

# Video Preview
<iframe width="100%" height="100%" style={{"aspect-ratio":"16/9"}} src="https://www.youtube.com/embed/S1qvp1cbKeE" title="YouTube Video Player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>