# **Multiplayer Button**
In this example we see how to create a 3D Button that runs code on the Client and Server for Multiplayer functionality
### How to Create an Interactable Button in Studio

#### Step 1: Create a New Project
- Open Studio Hub and create a new project.
- Choose a project name and location, then click "Create."

#### Step 2: Set Up Button Object
- In the Hierarchy window, create a new 3D object, such as a cube, to act as your button.
- Ensure the button object has a Box Collider component attached to it to enable interaction.
- Add a TapHandler component to the button object.
  - Set the "Distance" property to 10.
  - Uncheck "WalkTo" for ease of testing.

#### Step 3: Create Lua Script
- In the Project window, navigate to the desired location.
- Right-click and select "Create" > "Lua" > "Script."
- Name the script (e.g., `buttonscript.lua`).
- Set the script type to `Client and Server` in the Inspector.

#### Step 4: Attach Script to Button
- Drag and drop the newly created Lua script onto the button object in the Hierarchy window or onto the button's Inspector window.

#### Step 5: Write Lua Script
- Double-click on the Lua script in the Project window to open it.
- Write the following code inside the script:

>Note:  
>When creating a `Client/Server` lua script, you have access to two versions of the main Event Functions: `Client/Server` - `Awake` `Start` `Update`.  
>For example: `ClientAwake` and `ServerAwake` are the same LifeCycle Function;  
>However `ClientAwake` runs on the `Client` and `ServerAwake` runs on the `Server`.

```lua
local buttonTapRequest = Event.new("ButtonTapRequest")
local buttonTapEvent = Event.new("ButtonTapEvent")

function self:ClientAwake()
    self.gameObject:GetComponent(TapHandler).Tapped:Connect(function()
        -- Insert code to execute locally when the button is tapped
        buttonTapRequest:FireServer() -- Send a Request to the Server
    end)

    buttonTapEvent:Connect(function()
        -- Insert code to execute on all clients when the button is tapped by any one
        print("Hello World")
        --To show which client is saying hello world you can concatenate 'Hello World' with client.localPlayer.name
        print(client.localPlayer.name .. ": Hello World")
    end)
end

function self:ServerAwake()
    buttonTapRequest:Connect(function()
        buttonTapEvent:FireAllClients() -- Send an Event to all Clients
    end)
end
```

#### Step 6: Set Up Virtual Player
- Click the "Highrise" toolbar button.
- Navigate to `Studio` > `Virtual Player`.
- Dock the virtual player next to your game window.

#### Step 7: Test the Button
- Hit play in the Unity editor.
- Click on the cube button to ensure the event fires.
- Confirm that each client prints "Hello World" in the console.

By following these steps, you can create an interactable button in Studio using the Lua API and test its functionality across multiple clients.
