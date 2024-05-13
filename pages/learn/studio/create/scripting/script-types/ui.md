# UI Scripts

UI scripts in Highrise Studio are specialized scripts that control the behavior and interactions of user interface elements in the game. They are responsible for managing UI components, handling user input, updating visual elements, and creating dynamic interfaces that enhance player experience and engagement.

Using Highrise Studio, you can efficiently implement UI elements using Lua scripts, along with UXML and USS files for layout and styling. Here's how you can get started:

## UXML and USS Files

- **UXML (UI Markup Language)**: UXML files define the structure and hierarchy of UI elements in your game. They contain XML-like tags that represent various UI components such as buttons, text fields, images, and panels.

- **USS (UI Style Sheet)**: USS files define the visual appearance and styling of UI elements. They use CSS-like syntax to specify properties like colors, fonts, margins, padding, and animations.

Example UXML file (`MyUI.uxml`):

```xml
<hr:UILuaView class="my-ui" picking-mode="Ignore">
    <hr:UILabel name="myLabel" picking-mode="Ignore">
    </hr:UILabel>
</hr:UILuaView>
```

Example USS file (`MyUI.uss`):

```css
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

By combining Lua scripts with UXML and USS files, you can create visually appealing and interactive user interfaces that seamlessly integrate with your game's design and functionality.

## UI Types

The script’s `Output` property offers three settings:
- **World**: The UI displays in world space, such as on a render texture applied to a 3D object (e.g., a quad).
- **Above Chat**: The UI remains visible above the chat box and moves up when the chat is opened.
- **HUD**: The UI displays behind the chat history and occupies a fixed, screen space position.

## UI Type Script

UI scripts in Highrise Studio are defined using the `UI` type. This type is specifically designed for handling UI elements and events within the game. Here's a basic example of a UI script that updates a text label when a button is clicked:

```lua
--!Type(UI)

--!Bind
local myLabel : UILabel = nil

myLabel:SetPrelocalizedText("I am a UILabel")
```

> Note: In the Lua script, the label variable `local myLabel` must match the name of the label component in the UXML file.

In this script:

- `myLabel`: Reference to the UILabel component in the UXML file.
- `SetPrelocalizedText`: Function to set the text content of the label.

By defining UI scripts with the `UI` type, you can easily access and manipulate UI components, respond to user input, and create dynamic user interfaces that enhance player interaction and engagement.

## Use Cases

UI scripts are commonly used for the following purposes:

- **Button Click Events**: Handling button clicks and interactions.
- **Text Updates**: Updating text labels, descriptions, and notifications.
- **Slider and Input Field Handling**: Managing user input and data entry.
- **Panel Visibility**: Showing, hiding, and animating UI panels.

By leveraging UI scripts, you can create intuitive and visually appealing user interfaces that provide players with seamless navigation, feedback, and interaction within your game.

## Do and Don't

In this table, we summarize the best practices and common pitfalls when working with UI scripts:

| Do                                       | Don't                                    |
|------------------------------------------|------------------------------------------|
| Use UI scripts for managing UI elements and interactions. | Use UI scripts for game logic or data storage. |
| Implement button click events, text updates, and user input handling. | Implement complex game mechanics or AI behavior in UI scripts. |
| Optimize UI scripts for performance and responsiveness. | Overload UI scripts with unnecessary computations or heavy processing. |
| Leverage UI scripts to enhance player interaction and engagement. | Rely solely on UI scripts for core gameplay mechanics or multiplayer interactions. |

## Conclusion

UI scripts play a crucial role in creating engaging and interactive user interfaces that enhance player experience and immersion in your game. By utilizing UI scripts effectively, you can design intuitive interfaces, provide visual feedback, and facilitate seamless interactions that captivate players and elevate your game's overall quality. Experiment with UI scripts to explore their capabilities and create compelling user interfaces that resonate with your audience.