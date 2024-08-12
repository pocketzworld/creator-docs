# Beginner's Guide to Creating UI in Highrise Studio

## Introduction

In this guide, you will learn how to create user interfaces (UI) in Highrise Studio. We are going to create a simple UI component that consists of a button and a label. The button will increment a counter when clicked, and the label will display the current count. By following these steps, you will gain a basic understanding of creating UI elements in Highrise Studio and how to interact with them using Lua scripts.

## Step 1: Create Your UI Components

1. **Generate the UI Components**:
   - In Unity’s Project window, go to `Create > Lua > UI`.
   - This action generates three interconnected files:
     - A Lua script (logic)
     - A UXML script (layout)
     - A USS script (styling)
   - Additionally, a UI Visual Tree Factory is created at the root of your assets.

<Note type="warning">
Your project must have a UI Tree in order to display UI. Can be found in the root of your assets folder. (Included when you create a UI component)
</Note>

## Step 2: Set Up the UI in Your Scene

1. Right-click in the Hierarchy window and select `Create Empty` to create an empty GameObject.
2. Change the name of the GameObject to something meaningful (e.g., `MyUI`).
3. Drag the UI Lua script onto the GameObject to initialize the UI.
4. Configure the UI Output:
   - The script’s `Output` property offers three settings:
     - **World**: The UI displays in world space, such as on a render texture applied to a 3D object (e.g., a quad).
     - **Above Chat**: The UI remains visible above the chat box and moves up when the chat is opened.
     - **HUD**: The UI displays behind the chat history and occupies a fixed, screen space position.
5. Set the `Output` property to your desired display mode.
6. Open the UXML file to design your UI layout.

<Note type="info">
When using the "World" output mode, you cannot use Button or InputField elements in your UI. For interactive UI elements, use the "Above Chat" or "HUD" output modes.
</Note>

## Step 3: Design and Style Your UI

In the example below we are going to create a simple UIButton that increases a counter when clicked.

<Note type="warning">
In the following example, my UI files are named `miniGame`, make sure you change the `UILuaView` element to match the name of your UI.
</Note>

1. **Add UI Elements Using UXML**:
   - Modify the UXML file to define the structure of your UI. For an Above Chat UI, add a UILabel inside your UILuaView:
     ```xml
     <hr:UILuaView class="mini-game">
         <hr:UILabel class="mini-game__counter" name="_counterLabel" picking-mode="Ignore" />
         <VisualElement class="mini-game__buttons">
            <hr:UIButton class="secondary-button" name="_Button">
               <Label text="Click me!"/>
            </hr:UIButton>
         </VisualElement>
      </hr:UILuaView>
     ```
<Note type="warning">
Setting `picking-mode="Ignore"` ensures the UI does not respond to mouse or touch input, making it purely informational.
</Note>

1. **Style the UI with USS**:
   - Open the USS file to style your UI elements:
     ```css
     .mini-game {
         position: relative;
         display: flex;
         flex-direction: column;
         align-self: center;
         flex-grow: 1;
         -unity-font-definition: var(--font-regular);
      }

      .mini-game__counter {
         position: absolute;
         align-self: center;
         top: 40;
         font-size: 70px;
         color: #fff;
         text-shadow: 2px 2px 0px rgba(0, 0, 0, 0.5);
      }

      .mini-game__game {
         position: absolute;
         display: flex;
         flex-direction: column;
         align-self: center;
         bottom: 0;
      }

      .secondary-button:hover {
         background-color: rgba(0, 255, 0, 0.4);
      }
     ```

## Step 4: Script UI Interactivity

1. **Bind and Set Properties in Lua**:
   - Edit the Lua script to interact with your UI elements. Bind the UILabel and set its text:
     ```lua
     --!Type(UI)

     --!Bind
     local _counterLabel : UILabel = nil
     --!Bind
     local _Button : UIButton = nil

     local counter = 0 -- Initialize the counter

     -- Register a callback for when the button is pressed
     _Button:RegisterPressCallback(function()
         counter = counter + 1 -- Increment the counter
         _counterLabel:SetPrelocalizedText(tostring(counter)) -- Update the label text
     end, true, true, true)
     ```
     
<Note type="warning">
In the Lua script, the label variable `_counterLabel` is bound to the UILabel element in the UXML file. The button variable `_Button` is bound to the UIButton element. This is important for interacting with the UI elements in your script. Make sure the names match the names in your UXML file.
</Note>

## Step 5: Test Your UI

Click the Play button in Unity to test your UI. You should see the UI elements displayed in the scene. Click the button to interact with the UI and verify that the counter increases as expected.

### Conclusion

This guide has provided you with a basic understanding of creating UI elements in Highrise Studio. By following these steps, you can design and customize UI components to enhance the user experience in your games. Experiment with different layouts, styles, and interactions to create engaging and visually appealing interfaces for your players. Happy creating!