# Anchors

Anchors enable specific actions for players upon reaching designated points in the environment, such as sitting down, standing up, or other actions.

## Creating an Anchor

To create an anchor, follow these steps:

1. Right-click in the `Hierarchy` window and select `Create Empty`.
2. Rename the new object to `Anchor`.
3. Add an `Anchor` component to the object by clicking `Add Component` in the `Inspector`.
4. Specify the desired `Action` for the anchor.
5. Attach a `Tap Handler` component to make the anchor interactive.
6. Include a `Collider` component to trigger the anchor.

<Note type="warning">
An object must have both a `Collider` component and a `Tap Handler` component for the Anchor to function properly.
</Note>

## Anchor Actions

Anchors support the following actions:

1. **Sit**: Player sits down upon reaching the anchor.
2. **Stand**: Player stands up upon reaching the anchor.
3. **Run**: Player runs in place upon reaching the anchor.
4. **Walk**: Player walks in place upon reaching the anchor.

## Anchor Properties

Anchors have the following properties:

1. **Animation**: The animation to play when the player reaches the anchor.
2. **Tappable**: Whether the anchor is tappable by the player.
3. **Enter From**: The direction from which the player enters the anchor.
4. **Exit To**: The direction to which the player exits the anchor.

<Note type="info">
Anchors can be set to any game object in the environment, whether it is an empty object or a 3D model.
</Note>

## Anchor Examples

Here are some examples of how anchors can be used in a scene:

- **Sitting Area**: Create an anchor that allows the player to sit down on a bench.
- **Running Track**: Create an anchor that allows the player to run in place on a treadmill.
- **Walking Path**: Create an anchor that allows the player to walk in place along a path.

# Conclusion

Anchors are a powerful tool for creating interactive experiences in the environment. By using anchors, you can add a new level of engagement and immersion to your scene.