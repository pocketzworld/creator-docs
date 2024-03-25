# **Multiplayer Button**
![image1](/assets/learn/guides/studio/open-studio-hub.png)

### How to Create an Interactable Button in Studio

#### Step 1: Create a New Project
1. Open Studio Hub and create a new project.
2. Choose a project name and location, then click "Create."

#### Step 2: Set Up Button Object
- In the Hierarchy window, create a new 3D object, such as a cube, to act as your button.
- Ensure the button object has a Box Collider component attached to it to enable interaction.
- Add a TapHandler component to the button object.
  - Set the "Distance" property to 10.
  - Uncheck "WalkTo" for ease of testing.

#### Step 3: Create Lua Script
1. In the Project window, navigate to the desired location.
2. Right-click and select "Create" > "Lua" > "Script."
3. Name the script (e.g., `buttonscript.lua`).
4. Set the script type to `Client and Server` in the Inspector.

#### Step 4: Attach Script to Button
- Drag and drop the newly created Lua script onto the button object in the Hierarchy window or onto the button's Inspector window.

#### Step 5: Write Lua Script
- Double-click on the Lua script in the Project window to open it.
- Write the following code inside the script:

```lua
local buttonTapRequest = Event.new("ButtonTapRequest")
local buttonTapEvent = Event.new("ButtonTapEvent")

function Client()
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

function Server()
    buttonTapRequest:Connect(function()
        buttonTapEvent:FireAllClients() -- Send an Event to all Clients
    end)
end

if server then
    Server()
else
    Client()
end
```

#### Step 6: Set Up Virtual Player
1. Click the "Highrise" toolbar button.
2. Navigate to `Studio` > `Virtual Player`.
3. Dock the virtual player next to your game window.

#### Step 7: Test the Button
- Hit play in the Unity editor.
- Click on the cube button to ensure the event fires.
- Confirm that each client prints "Hello World" in the console.

By following these steps, you can create an interactable button in Studio using the Lua API and test its functionality across multiple clients.