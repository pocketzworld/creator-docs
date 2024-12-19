# Script Relations

This document outlines how the various scripts in the game interact with each other to create a cohesive gameplay experience. Understanding these relationships will help developers grasp the architecture and workflow of the game.

## High-Level Overview

The game's scripts are modular and grouped by functionality. Here are the primary categories and their connections:

- **Core Scripts:** Centralized management of game-wide logic, such as `GameManager.lua` and `SaveManager.lua`.
- **UI Scripts:** Control user interface components, such as `UIMain.lua` and `UIDressUp.lua`.
- **Gameplay Mechanics:** Handle specific features like contests (`ContestManager.lua`), quests (`QuestManager.lua`), and rewards (`LootManager.lua`).
- **Utility Scripts:** Provide reusable functions (e.g., `OutfitUtils.lua`).

## Key Relationships

### 1. **GameManager.lua**
The `GameManager.lua` script acts as the central hub, coordinating between other systems.

- **Connected Scripts:**
  - `QuestManager.lua`: Manages quest progression and integrates with the main game flow.
  - `SaveManager.lua`: Saves and loads player progress.
  - `ContestManager.lua`: Tracks active contests and their results.

- **Workflow Example:**
  1. When the game starts, `GameManager.lua` initializes other managers.
  2. It communicates with `SaveManager.lua` to load saved data.
  3. It triggers `QuestManager.lua` and `ContestManager.lua` to update their states based on player progress.

### 2. **QuestManager.lua**
The `QuestManager.lua` script handles quests, ensuring seamless integration with NPCs and rewards.

- **Connected Scripts:**
  - `DialogManager.lua`: Provides quest-related dialogue.
  - `LootManager.lua`: Distributes rewards upon quest completion.
  - `UIDialog.lua`: Displays quest prompts to the player.

- **Workflow Example:**
  1. A player interacts with an NPC, triggering `DialogManager.lua`.
  2. If a quest is accepted, `QuestManager.lua` tracks its status.
  3. Upon completion, it calls `LootManager.lua` to reward the player.


### 3. **ContestManager.lua**
The `ContestManager.lua` script orchestrates the dress-up contests, including submissions, voting, and results.

- **Connected Scripts:**
  - `UIContest.lua`: Displays the contest interface.
  - `UIContestVoting.lua`: Handles the voting interface.
  - `LootManager.lua`: Distributes rewards based on contest rankings.

- **Workflow Example:**
  1. Players submit their looks through `UIContest.lua`.
  2. `ContestManager.lua` collects and organizes entries.
  3. Voting is conducted via `UIContestVoting.lua`, and results are processed by `LootManager.lua`.

### 4. **UIDressUp.lua**
The `UIDressUp.lua` script powers the customization interface, allowing players to modify their characters.

- **Connected Scripts:**
  - `OutfitUtils.lua`: Provides utility functions for managing outfits.
  - `UIDressUpCloset.lua`: Manages inventory and available items.

- **Workflow Example:**
  1. Players open the customization menu via `UIDressUp.lua`.
  2. `UIDressUpCloset.lua` loads available outfits.
  3. Changes are applied and saved using `OutfitUtils.lua`.

### 5. **LootManager.lua**
The `LootManager.lua` script distributes rewards for contests, quests, and other achievements.

- **Connected Scripts:**
  - `QuestManager.lua`: Calls `LootManager.lua` to reward players after quest completion.
  - `ContestManager.lua`: Distributes rewards based on contest results.
  - `UIReward.lua`: Displays the reward notifications to players.

- **Workflow Example:**
  1. A quest or contest triggers `LootManager.lua`.
  2. Rewards are calculated and assigned to the player.
  3. `UIReward.lua` displays the rewards.

### 6. **SaveManager.lua**
The `SaveManager.lua` script handles saving and loading player progress.

- **Connected Scripts:**
  - `GameManager.lua`: Communicates with `SaveManager.lua` during initialization and shutdown.
  - `UIDressUp.lua`, `QuestManager.lua`, `ContestManager.lua`: Retrieve and update save data.

- **Workflow Example:**
  1. At startup, `GameManager.lua` calls `SaveManager.lua` to load player data.
  2. Gameplay systems (e.g., quests, customization) retrieve necessary data.
  3. Progress is saved periodically or when the game exits.

### 7. **DialogManager.lua**
The `DialogManager.lua` script manages NPC dialogues and interactions.

- **Connected Scripts:**
  - `QuestManager.lua`: Provides quest-related dialogue.
  - `UIDialog.lua`: Displays dialogue options to the player.

- **Workflow Example:**
  1. A player interacts with an NPC, triggering `DialogManager.lua`.
  2. Dialogue options are displayed via `UIDialog.lua`.
  3. If a quest is involved, `QuestManager.lua` updates its state.

## Next Steps

Understanding the relationships between scripts is crucial for maintaining a coherent game structure. As you delve deeper into the project, explore how these connections influence gameplay and player experience. For detailed script functionalities, refer to the individual script documentation. 