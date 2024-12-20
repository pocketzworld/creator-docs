# UI Mechanics Document

This document provides a comprehensive overview of the User Interface (UI) mechanics implemented in the game. It explains how various UI components are structured, managed, and animated to ensure a cohesive player experience.

## Overview

The UI system supports interactive elements such as popups, animations, and task-specific displays. Key features include:
- Popup dialogs for confirmation and informational messages.
- Animated transitions for enhanced visual appeal.
- Task-specific UIs such as dress-up nodes and quest objectives.
- Dynamic state handling for interactive components.

## Core Components

### 1. **UI Manager**
The `UIManager` handles the lifecycle of UI components, including opening, closing, and animating.

#### Key Features
- **State Management**: Tracks the open or closed state of UIs.
- **Event Handling**: Fires events on UI state changes.
- **Prefab Management**: Instantiates and destroys UI prefabs dynamically.

#### Key Functions
- `OpenPopup`: Opens a popup UI with animation.
- `CloseUI`: Closes a UI and cleans up resources.
- `GetUI`: Retrieves the component of an open UI by its ID.
- `DoAnimation`: Applies specified animations to UI components.

### 2. **Popup UIs**
#### Generic Popup
Used for displaying simple messages with optional confirmation callbacks.

##### Key Functions
- `Init`: Initializes the popup with a message and OK callback.
- `InitPurchase`: Extends functionality for purchase confirmation with custom callbacks.

#### Welcome Popup
Provides an introduction or tutorial to new players.

#### Outfit Choice Popup
Allows players to select from multiple clothing options for tasks or customization.

### 3. **Dress-Up UIs**

#### Dress-Up Node UI
Handles individual dress-up nodes, displaying clothing options and animations.

##### Key Functions
- `Init`: Initializes the node with parent data and world anchor.
- `SetChosen`: Updates the visual state to indicate selection.
- `PlayScaleUpAnim`: Plays a scale-up animation when the node is selected.
- `PlayPulsingAnim`: Animates the node with a pulsing effect.

#### Dress-Up Closet UI
Manages the overall interface for selecting and modifying outfits.

##### Key Functions
- `Init`: Initializes the closet with the parent controller.
- `Refresh`: Updates the state based on current dress-up choices.
- `Show`: Toggles visibility of the UI and its nodes.

### 4. **UI Animations**

#### Popup Animation Helper
Provides reusable animations for scaling and sliding UI elements.

##### Key Functions
- `PlayOpenAnim`: Scales a UI element from 0 to full size.
- `PlaySlideUpAnim`: Slides a UI element up from an offset position.

### 5. **Task-Specific UIs**

#### Node UI
Handles task nodes, such as dress-up or quest objectives.

##### Key Functions
- `SetChosen`: Marks a node as selected or unselected.
- `HideNodeForScaleUp`: Prepares a node for a scaling animation.
- `ClientUpdate`: Updates the node's position relative to the screen.

#### Quest HUD
Displays objectives and progress for ongoing quests.

## Workflow

1. **Opening a UI**
   - Use `UIManager.OpenPopup` with a prefab and ID.
   - The `DoAnimation` function applies a transition effect.

2. **Interacting with a Popup**
   - Call `Init` to configure message and callback behavior.
   - Buttons trigger callbacks and close the UI using `CloseUI`.

3. **Refreshing Task UIs**
   - Nodes update their state dynamically with `RefreshNodes`.
   - Animations like `PlayScaleUpAnim` enhance interactivity.

## Example Implementation

### Opening a Popup
```lua
local popup = UIManager.OpenPopup(_genericPopupPrefab, "GenericPopup")
popup.Init("Are you sure?", function() print("Confirmed!") end)
```

### Scaling Up a Node
```lua
local node = UIManager.OpenNodeUI()
node.Init(parent, nodeData, worldAnchor)
node.PlayScaleUpAnim()
```
