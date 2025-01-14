# Lecture 9: Camera Controls

## Introduction

In this lecture, we'll learn how to use Camera Controls in Highrise Studio to give players the best view of your game world. Proper camera setups make your game more exciting and immersive.

### What Are Camera Controls?

Camera Controls let you decide how the game world is seen by players. You can change camera angles, movements, and behaviors to highlight different parts of your game and enhance the overall experience.

<Note type="info">
Highrise Studio supports various camera types like 2D, 3D, and Isometric, helping you match the camera to your game's style.
</Note>

## Accessing Different Camera Views

Here’s how to switch camera views in Highrise Studio:

1. **Open Camera Settings**:
   - Right-click in the Hierarchy window.
   - Navigate to `Highrise` > `Cameras` to see different options.
2. **Choose a Camera Type**:
   - **First-Person Camera**: Puts you in the character's shoes for a close-up experience.
   - **RTS Camera**: Offers a bird’s-eye view, great for strategy games.
   - **Side-Scroller Camera**: Best for 2D games, showing action from the side.
   - **Third-Person Camera**: Follows the character from behind, common in adventure games.
  ![Camera Types](/assets/learn/guides/studio/Lectures/camera-types.png)

<Note type="warning">
Ensure only one active camera at a time to prevent conflicts.
</Note>

## Setting a Default Camera

To set a default camera view:

1. **Select Your Preferred Camera** in the Hierarchy.
2. **Tag as Main Camera**:
   - Go to the `Inspector`, find `Tag`, and choose `MainCamera`.
   - This makes it the primary camera for your scene.

![Main Camera Tag](/assets/learn/guides/studio/Lectures/maincamera-tag.png)

## Adjusting Camera Settings

Customize your camera settings to enhance player experience:

1. **Zoom Level**: Controls how close the camera is to the action.
2. **Field of View (FOV)**: Adjusts how much of the game world is visible.
3. **Pitch and Yaw**: Alters the camera angle for different perspectives.
4. **Center on Character**: Automatically focuses on the character when the game starts.

<Note type="info">
To see changes, you'll need to run your game as adjustments in the Scene window won’t affect gameplay directly.
</Note>

![Camera Settings](/assets/learn/guides/studio/Lectures/camera-settings.png)

## Conclusion

Mastering Camera Controls can greatly improve your game by ensuring players always have the best perspective. These settings are crucial for guiding players and showcasing your game world.

## Next Steps

Experiment with different camera settings to find the perfect setup for your game. Try various camera types and adjust their settings to discover what best suits your game’s style and narrative.

- [Lecture Ten: Lighting and Shadows](https://create.highrise.game/learn/studio/create/beginner-guide/lecture-ten/lecture-overview)