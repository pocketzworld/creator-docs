# NavMesh

## Overview

A NavMesh is a component that outlines areas accessible to characters and identifies obstacles in Highrise Studio environments.

## Setup Guide

### Enabling and Visualizing NavMesh

- **Access and Enable**:
  - Open the Scene View Toolbar.
  - Use the `~` key to toggle the visibility of NavMesh AI Navigation if it's not visible.
  - Ensure "Show NavMesh" is active and Gizmos are turned on for visualization.

  ![Visualization of AI Navigation](/assets/learn/guides/studio/Lectures/AI-navigation.png)

## Key Components of NavMesh

### Nav Mesh Surface

This is the core component for generating the NavMesh:

- **Installation**:
  - Attach the Nav Mesh Surface component to a GameObject.
- **Configuration and Generation**:
  - Adjust the settings to suit your game's environment and click **Bake** to create the NavMesh.

<Note type="warning">
A basic template may already include this component. If absent, it needs to be added manually.
</Note>

  ![Configuring Nav Mesh Surface](/assets/learn/guides/studio/Lectures/navmesh-surface.png)

### Nav Mesh Agent

Enables path following based on the NavMesh:

- **Application**:
  - Add the Nav Mesh Agent to any game object requiring navigational abilities.
- **Customization**:
  - Modify properties such as speed and pathfinding to optimize character movement.

<Note type="warning">
Characters typically come with a pre-attached Nav Mesh Agent.
</Note>

  ![Nav Mesh Agent Setup](/assets/learn/guides/studio/Lectures/navmesh-agent.png)

### Nav Mesh Obstacle

Identifies non-walkable areas within the game:

- **Usage**:
  - Apply this component to objects that should obstruct character movement.
- **Configuration**:
  - Set the dimensions and form to dictate navigation paths.

  ![Nav Mesh Obstacle Example](/assets/learn/guides/studio/Lectures/navmesh-obstacle.png)

### Nav Mesh Link

Facilitates advanced pathfinding across separate NavMesh areas:

- **Function**:
  - Ideal for creating direct routes or alternative paths.
- **Settings**:
  - Adjust the properties to enable diverse navigational behaviors.

  ![Nav Mesh Link Illustration](/assets/learn/guides/studio/Lectures/navmesh-link.png)

### Nav Mesh Modifier & Nav Mesh Modifier Volume

Adjusts the NavMesh application in specific areas or volumes:

- **Adjustments**:
  - Use these components to refine NavMesh details in particular sections of the environment.
- **Options**:
  - Designate areas to be ignored or specifically included in the NavMesh.

  ![Nav Mesh Modifier Setup](/assets/learn/guides/studio/Lectures/navmesh-modifier.png)

## Baking and Managing the NavMesh

- **Finalization**:
  - Set the correct parameters on the Nav Mesh Surface and click **Bake** to establish the walkable zones.
- **Ongoing Management**:
  - Re-bake the NavMesh following any changes in the scene that impact navigation.

![Baking the NavMesh](/assets/learn/guides/studio/Lectures/bake-navmesh.png)

<Note type="info">
Blue-highlighted areas depict the walkable paths for characters.
</Note>

## Conclusion

Implementing a NavMesh in Highrise Studio is vital for crafting responsive and intelligent environments where characters can navigate effectively. Each component contributes significantly to enhancing the navigational capabilities.