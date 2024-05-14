# NavMesh

NavMesh is a tool for creating a navigation mesh, vital for player movement in the game world.

## Importance

Without a NavMesh, player movement and navigation in the game world wouldn't be possible, impacting the game's realism and immersion.

## NavMesh Benefits

- **Player Navigation**: Enables movement in the game world.
- **Pathfinding**: Finds the shortest route to destinations.
- **Obstacle Avoidance**: Automatically steers clear of obstacles.
- **Dynamic Navigation**: Adapts to real-time changes in the game world.

## Creating a NavMesh

In Highrise Studio, a NavMesh is automatically generated for new scenes. Alternatively, follow these steps to create one manually:

1. Right-click in the Hierarchy window.
2. Select `Create Empty`.
3. Rename the new GameObject to `NavMesh`.
4. In the Inspector window, click `Add Component`.
5. Search for `NavMesh Surface` and add it to the GameObject.
6. Click `Bake` to generate the NavMesh.

<Note type="warning">
Ensure your player character has a NavMesh Agent attached for the NavMesh to function. (This is enabled by default in Highrise Studio)
</Note>

## Editing the NavMesh

Adjust settings in the NavMesh Surface component to customize the NavMesh for your game world.

<Note type="warning">
When editing the NavMesh make sure you select the **Show NavMesh** option in the `AI Navigation` window in the Scene view to see the changes in real-time.
</Note>

## Type of NavMesh

There are different types of NavMesh that you can create based on the requirements of your game. Some common types of NavMesh include:

- **NavMesh Agent**: Used for player characters and NPCs.
- **NavMesh Obstacle**: Used for dynamic obstacles in the game world.
- **NavMesh Link**: Used for connecting different NavMesh areas.
- **NavMesh Modifier**: Used for modifying the NavMesh based on specific rules.
- **NavMesh Modifier Volume**: Used for modifying the NavMesh in a specific area.
- **NavMesh Surface**: Used for generating the NavMesh in the game world.

## Excluding Areas or Objects

If you ever need to exclude certain areas or objects from the NavMesh, you can use the `NavMesh Modifier` component and set the `Mode` to `Remove Object`. You can also change the other properties to customize the exclusion area.

## Baking the NavMesh

When editing the NavMesh, you must bake it to apply the changes to the game world. Select the Object with the `NavMesh Surface` component and click `Clear` to remove the existing NavMesh and then click `Bake` to generate the new NavMesh.

## Conclusion

NavMesh is essential for creating immersive game worlds. Utilize its features to enable player navigation, pathfinding, obstacle avoidance, and dynamic navigation for a polished gaming experience.
