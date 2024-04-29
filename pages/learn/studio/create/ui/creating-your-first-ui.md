# Beginner's Guide to Creating UI in Highrise Studio

Creating interactive user interfaces (UI) in your Highrise World can enhance player engagement significantly. Using Highrise Studio, you can efficiently implement UI elements using Lua scripts, along with UXML and USS files for layout and styling. Here's how you can get started:

## Step 1: Create Your UI Components

1. **Generate the UI Components**:
   - In Unity’s Project window, go to `Create > Lua > UIView`.
   - This action generates three interconnected files:
     - A Lua script (logic)
     - A UXML script (layout)
     - A USS script (styling)
   - Additionally, a UI Visual Tree Factory is created at the root of your assets.
   > Note: Your project must have a UI Tree in order to display UI.

## Step 2: Set Up the UI in Your Scene

1. **Place the Lua Script**:
   - Drag and drop the Lua script onto an object in your scene to initialize the UI.

2. **Configure the UI Output**:
   - The script’s `Output` property offers three settings:
     - **World**: The UI displays in world space, such as on a render texture applied to a 3D object (e.g., a quad).
     - **Above Chat**: The UI remains visible above the chat box and moves up when the chat is opened.
     - **HUD**: The UI displays behind the chat history and occupies a fixed, screen space position.

## Step 3: Design and Style Your UI

1. **Add UI Elements Using UXML**:
   - Modify the UXML file to define the structure of your UI. For an Above Chat UI, add a UILabel inside your UILuaView:
     ```uxml
     <hr:UILuaView class="my-ui" picking-mode="Ignore">
         <hr:UILabel name="myLabel" picking-mode="Ignore">
         </hr:UILabel>
     </hr:UILuaView>
     ```
     > Note: Setting `picking-mode="Ignore"` ensures the UI does not respond to mouse or touch input, making it purely informational.

2. **Style the UI with USS**:
   - Open the USS file to style your UI elements:
     ```uss
     .my-ui {
         -unity-text-align: middle-center;
         margin-top: auto;
         background-color: rgba(255,255,255,0.75);
     }

     .my-ui #myLabel{
         color: rgba(0,0,0,1);
         font-size: 200%;
         letter-spacing: 5%;
     }
     ```

## Step 4: Script UI Interactivity

1. **Bind and Set Properties in Lua**:
   - Edit the Lua script to interact with your UI elements. Bind the UILabel and set its text:
     ```lua
     --!Type(UI)

     --!Bind
     local myLabel : UILabel = nil

     myLabel:SetPrelocalizedText("I am a UILabel")
     ```
     
     > Note: In the Lua script, the label variable`local myLabel` must match the name of the label in the Uxml document `<hr:UILabel name="myLabel">`

## Step 5: Test Your UI

- **Run the Scene**: Click the play button in Unity to see your UI in action. For example, with the Above Chat setting, the UILabel should appear above the chat interface in the game.

### Final Notes

This guide walks you through the basics of setting up and customizing UI in Unity 3D using Highrise Studio. Experiment with different UI elements, styles, and interactions to create a dynamic and engaging user experience in your game.
