# GameManager Module Documentation

The `GameManager.lua` is the central module responsible for orchestrating the game's primary functionalities. It connects various systems, such as quests, rewards, player interactions, and UI management, ensuring seamless gameplay experiences.

## Overview

The `GameManager` module provides:

- **Player Management**: Tracking player data, controlling characters, and handling cutscenes.
- **Quest Integration**: Managing quest progression, rewards, and resets.
- **Reward Systems**: Distributing rewards through loot containers.
- **UI Coordination**: Integrating UI elements like dress-up and rewards.
- **Cheat Commands**: Debugging tools for testing and development.

## Key Components

### 1. **Player Management**

#### Player Tracking
- Maintains a list of all active player models in `_allPlayers`.
- Functions to add and remove players:
  - `AddModelToList(model)`: Adds a player model to the global list.
  - `RemoveModelFromList(model)`: Removes a player model from the global list.

#### Cutscene Integration
- Handles entering and exiting cutscene modes:
  - `EnterCutsceneDisplay(enter, position, forward)`: Adjusts camera settings, fades characters, and toggles chat visibility during cutscenes.

#### Character Fading
- Provides smooth fade-in/out transitions for characters:
  - `FadeCharacter(model, fade, duration)`: Fades a single character.
  - `FadeCharacters(fade, duration)`: Fades all characters.

### 2. **Quest Management**

#### Quest Tracking
- Retrieves quest progress and checks completion:
  - `AreContestsUnlocked()`: Checks if contests are unlocked based on quest progress.
  - `HasCompletedAllQuests()`: Verifies if all quests are completed.

#### Quest Resetting
- Resets all quests using `ResetQuests()` and marks data as needing a reset.

#### Quest Debugging
- Supports cheat commands for quest testing:
  - `DebugQuestsCheat()`: Enables debug mode for quests.
  - `CompleteQuestsCheat(arguments)`: Completes quests up to a specified index.

### 3. **Reward Systems**

#### Reward Distribution
- Manages rewards from loot containers:
  - `RewardLoot(lootContainer, save, showRewardUI, uiCloseCallback)`: Rolls for rewards, saves data, and displays the reward UI.

#### Reward Conversion
- Converts saved reward data to game item formats:
  - `ConvertRewardSaveDataToGameItemAmount(rewardSaveData)`: Translates reward save data into a list of game items.

### 4. **UI Coordination**

#### Dress-Up Integration
- Coordinates dress-up systems with UI elements:
  - `OpenCloset(title, callback, acquiredClothing, usePlayerInventory, defaultOutfit)`: Opens the closet UI for outfit selection.
  - `GetClothingListFromSaveData()`: Retrieves a list of clothing items from saved data.

#### Chat Management
- Toggles chat message visibility:
  - `EnableShowingChats(enable)`: Enables or disables chat messages.

### 5. **Cheat Commands**

#### Command List
- Implements debug commands for testing purposes:
  - `ClearData()`: Clears all saved data.
  - `AddRewardCheat(arguments)`: Adds rewards to a player's inventory.
  - `UnlockContestCheat()`: Unlocks contests by completing prerequisite quests.
  - `DebugQuestsCheat()`: Enables debug mode for quests.

### 6. **Music Management**

#### Background Music
- Controls the main background music:
  - `StartMusic()`: Plays the primary background music using `_mainMusic`.

## Workflow Examples

### Adding a Player Model
1. **Player Joins the Game**:
   - `AddModelToList(model)` adds the player to `_allPlayers`.
2. **Cutscene Handling**:
   - If a cutscene is active, `FadeCharacter` fades the new player in.

### Rewarding a Player
1. **Loot Container Roll**:
   - `RewardLoot` rolls for rewards and saves the data.
2. **Reward UI**:
   - Rewards are displayed through the UI, initialized with a close callback.

### Completing Quests
1. **Player Progresses on Quests**:
   - `SaveManager.ProgressOnQuest` updates quest progress.
2. **Debugging Quests**:
   - `CompleteQuestsCheat(arguments)` completes quests for testing.