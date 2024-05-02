# **Multiplayer Button**

## **Introduction**
This example demonstrates how to create a 3D button that runs code on the client and server for multiplayer functionality.

## Create an Interactable Button in Studio

### 1. Create a New Project

- Open Studio Hub and create a new project.
- Choose a project name and location, then click **Create**.

### 2. Set Up Button Object

- In the Hierarchy window, create a new 3D object, such as a cube, to act as your button.
- Ensure the button object has a Box Collider component attached to enable interaction.
- Add a TapHandler component to the button object.
  - Set the **Distance** property to 10.
  - Uncheck **WalkTo** for ease of testing.

### 3. Create Lua Script

- In the Project window, navigate to the desired location.
- Right-click and select `Create > Lua > Script`.
- Name the script (e.g., `buttonscript.lua`).
- Set the script type to **Client and Server** in the Inspector.

### 4. Attach Script to Button

- Drag and drop the Lua script onto the button object in the Hierarchy window or the button's Inspector window.

### 5. Write Lua Script

- Double-click the Lua script in the Project window to open it.
- Write the following code inside the script:

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
        -- To show which client is saying hello world, concatenate 'Hello World' with client.localPlayer.name
        print(client.localPlayer.name .. ": Hello World")
    end)
end

function self:ServerAwake()
    buttonTapRequest:Connect(function()
        buttonTapEvent:FireAllClients() -- Send an Event to all Clients
    end)
end
```

> **Note:**
> When creating a **Client/Server** Lua script, you have access to two versions of the main event functions: **Client** and **Server** versions of `Awake`, `Start`, and `Update`.
> For example, `ClientAwake` and `ServerAwake` are the same lifecycle function, but `ClientAwake` runs on the client and `ServerAwake` runs on the server.

### 6. Set Up Virtual Player

- Click the **Highrise** toolbar button.
- Navigate to **Studio > Virtual Player**.
- Dock the virtual player next to your game window.

### 7. Test the Button

- Hit play in the Unity editor.
- Click the cube button to ensure the event fires.
- Confirm that each client prints "Hello World" in the console.

By following these steps, you can create an interactable button in Studio using the Lua API and test its functionality across multiple clients.