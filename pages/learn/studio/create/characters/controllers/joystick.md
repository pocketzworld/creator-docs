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

1. **Footstep Walk Sound**: The sound that plays when the character is walking.
2. **Footstep Run Sound**: The sound that plays when the character is running.
3. **External Input Action**: The input action that triggers the joystick movement.
4. **Running Speed Threshold**: The speed at which the character switches from walking to running.
5. **Is 2D**: Whether the joystick should move the character in 2D space.
6. **Max Link Distance**: The maximum distance the joystick can be from the character.
7. **Max Line Angle**: The maximum angle the joystick can be from the character.
8. **Max Link Move Step Change**: The maximum step change when moving the joystick.

<Note type="info">
When assigning the `External Input Action` or `Footstep Sounds`, make sure you toggle the "eye" icon to show all the available actions or sounds within the package.
</Note>

## Conclusion

Joystick character controllers are a great way to add touch-based controls to your game. By following the steps outlined in this guide, you can easily add a Joystick character controller to your character and customize it to fit your game's needs. Happy game developing!