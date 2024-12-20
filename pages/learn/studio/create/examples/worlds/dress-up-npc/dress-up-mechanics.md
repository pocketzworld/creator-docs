# Dress-Up Mechanics

This document provides a comprehensive guide to the dress-up mechanics implemented in the game, detailing how players can customize outfits, interact with NPCs, and complete dress-up tasks.

## Overview

The dress-up system allows players to create customized outfits, complete tasks, and interact with game elements. Key features include:

- Outfit customization for players and NPCs.
- Integration with quests and rewards.
- Interactive UI for selecting clothing and accessories.
- Validation and scoring of outfits for task completion.


## Core Concepts

### 1. **Clothing Templates**

Clothing templates define individual clothing items and collections that players can use.

#### Attributes
- **ID** (`_id`): Unique identifier for the clothing item.
- **Item ID** (`_itemId`): Reference to the clothing item in the database.
- **Palette** (`_palette`): Color palette associated with the clothing.
- **Display Data** (`_displayData`): Visual representation details for the UI.
- **Stackable** (`GetStackable`): Indicates whether the item can stack.

#### Key Functions
- `GetClothingData`: Returns a table containing the ID and color of the clothing.
- `GetDisplayData`: Retrieves the visual data for UI rendering.

### 2. **Dress-Up Tasks**

Dress-up tasks represent objectives that players must complete using the dress-up system.

#### Attributes
- **ID** (`_id`): Unique identifier for the task.
- **Closet Task** (`_closetTask`): Determines if the task requires using the closet.
- **Character Outfits** (`_characterOutfits`): Predefined outfits for NPCs.
- **Type Targets** (`_typeTargets`): Types of clothing needed for task completion.
- **Dialog Templates**: Include start, success, and failure dialogs.
- **Loot Container** (`_lootContainerTemplate`): Rewards given upon task completion.

#### Key Functions
- `GetDressUpData`: Retrieves data for specific clothing nodes.
- `GetPercentOfBestChoicesCorrect`: Calculates the accuracy of player choices.
- `GetLootContainerTemplate`: Provides rewards based on task success.

### 3. **Dress-Up State**

The dress-up state manages the current task, player choices, and original NPC outfits.

#### Attributes
- **Active**: Indicates whether a dress-up task is in progress.
- **Task**: Reference to the current dress-up task.
- **Original Outfit**: Stores the NPC's default outfit.
- **Added Clothing**: Tracks player-selected clothing.
- **Choices**: Stores the player’s selected options.

### 4. **Dress-Up Camera**

The `DressUpCamera.lua` script manages the camera’s behavior during dress-up tasks, including zooming, panning, and centering.

#### Key Settings
- **Zoom**: Adjustable zoom levels.
- **Rotation**: Enables camera rotation.
- **Centering**: Automatically centers on characters during dress-up interactions.
- **Panning**: Smoothly follows players or targets as needed.

## Workflow

1. **Task Initialization**
   - The system initializes a dress-up task using the `InitDressUpData` function.
   - Player choices and added clothing are reset.

2. **Outfit Selection**
   - Players select clothing items via the dress-up UI or closet interface.
   - Choices are validated against task requirements.

3. **Submission and Scoring**
   - Player choices are submitted using `SubmitDressUp`.
   - Scores are calculated based on matching best choices.

4. **Completion and Rewards**
   - Success or failure dialogs are shown based on the score.
   - Rewards are distributed via the `GetLootContainerTemplate` function.

## Example Implementation

### Example Clothing Template
```lua
local clothingTemplate = {
  _id = "clothing_001",
  _itemId = "hat_001",
  _palette = 3,
  _displayData = displayTemplate,
}
```

### Starting a Dress-Up Task
```lua
local dressUpTask = GetCurrentDressUpTask()
dressUpTask.Start()
```

### Submitting a Task
```lua
SubmitDressUp()
```

## Key Events

### `OnNPCTapped`
Triggered when an NPC is tapped to start a dress-up task.

### `SubmitDressUp`
Handles the submission of player choices and triggers dialog flow.

### `OnClosetOutfitComplete`
Triggered when the player completes an outfit in the closet.