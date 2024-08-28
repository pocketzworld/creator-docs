# Joystick Character Controller

## Introduction

**Joystick** character controllers are a type of character controller that allows the player to move a character using an on-screen joystick.

<Note type="warning">
Joystick is still in beta and may have some limitations or bugs. Please report any issues you encounter to the Highrise Studio team.
</Note>

## Adding a Joystick Character Controller

Luckily, Highrise Studio comes with a built-in Joystick character controller that you can use to control your characters. Here's how you can add a Joystick character controller to your character:

<Note type="warning">
You need version "0.12.2" or later of Highrise Studio to use the Joystick character controller.
</Note>

1. **Right-click** in the project view and select `Create > Highrise > Scene Variant` to create a new scene variant.
2. Rename the scene variant to something like "JoystickScenePrefab".
3. In the **JoystickScenePrefab**, add a component called `JoystickCharacterController`
4. Remove the default `PlayerCharacterController` component from the **JoystickScenePrefab**
5. Customize the Joystick properties in the `JoystickCharacterController` component
6. Click "Use this prefab" to set it as the default scene variant

## Customizing the Joystick

You can customize the Joystick character controller by adjusting the following properties in the `JoystickCharacterController` component:

### Basic Properties
1. **Footstep Walk Sound**: The sound that plays when the character is walking.
2. **Footstep Run Sound**: The sound that plays when the character is running.
3. **External Input Action**: External input action for external devices like keyboards or gamepads. ("Movement/Movement" is recommended)
4. **Running Speed Threshold**: The speed at which the character switches from walking to running.
5. **Is 2D**: Will use XY coordinates of the joytstick movement as the XY coordinates of the movements in the world. This is useful for 2D games.

### Advanced Properties
### Advanced Properties
6. **Max Link Distance**: This is the maximum in-world distance between the character and the link endpoint. If the distance exceeds this threshold, the link won't be considered.
7. **Max Line Angle**: This is the angle between your movement direction and the link's jump direction. If the angle is too large, the link won't be used.
8. **Max Link Move Step Change**: This measures the difference (as a proportion) between your desired movement (velocity vector * time delta) and the actual movement allowed by the nav mesh. For example, if you're on the edge of a cliff and can't move right, the step change is 1. A value of 0 means no change—your movement is fully within the nav mesh. This prevents jumping through links when you can simply move. A value of 0.5 means the link will be used only if your movement is at least half restricted, like approaching an edge at an angle.

<Note type="info">
When assigning the `External Input Action` or `Footstep Sounds`, make sure you toggle the "eye" icon to show all the available actions or sounds within the package.
</Note>

## Considerations

When using the Joystick character controller, keep the following considerations in mind:

1. **Performance**: Joystick character controllers can be more performance-intensive than other character controllers due to the continuous input processing.
2. **Camera Movement**: Make sure your camera follows the character's movement to keep the character in view. (default RTS camera is compatible with Joystick)
3. **Customization**: You can customize the Joystick character controller to fit your game's needs by adjusting the properties and styling of the joystick.
4. **Feedback**: Provide visual and audio feedback to the player when using the joystick to indicate movement and actions.

<Note type="warning">
Joystick does not currently support multi-touch input and it does not support the "Anchor" property yet. These features may be added in future updates.
</Note>

## Conclusion

Joystick character controllers are a great way to add touch-based controls to your game. By following the steps outlined in this guide, you can easily add a Joystick character controller to your character and customize it to fit your game's needs. Happy game developing!