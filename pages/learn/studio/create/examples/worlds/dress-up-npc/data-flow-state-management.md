# Data Flow & State Management

This document explains how data flows through the game and how various systems manage state. Understanding data flow is critical for maintaining the game's logic and ensuring a seamless player experience.

## Overview
The game relies on a centralized system to manage and share data between different modules. Key elements of data flow include:
- **Initialization:** Data is loaded and initialized at game startup.
- **Runtime Updates:** Systems modify and exchange data during gameplay.
- **Persistence:** Player progress and game state are saved and loaded using `SaveManager.lua`.

## Data Flow Components

### 1. **GameManager.lua**
The `GameManager.lua` script is the central hub for initializing and managing game-wide data.

- **Responsibilities:**
  - Initializes core systems (e.g., `QuestManager.lua`, `ContestManager.lua`).
  - Maintains global variables for game state.
  - Coordinates data flow between subsystems.

- **Example Workflow:**
  1. At startup, `GameManager.lua` calls `SaveManager.lua` to load saved data.
  2. It initializes managers like `QuestManager.lua` and `ContestManager.lua`, passing relevant data.
  3. During gameplay, it updates and tracks global states like active quests or contests.

### 2. **SaveManager.lua**
The `SaveManager.lua` script is responsible for persisting player progress and game data.

- **Responsibilities:**
  - Saves player data, including outfits, quest progress, and rewards.
  - Loads saved data during initialization.
  - Provides utility functions for other scripts to read or write data.

- **Example Workflow:**
  1. When the game starts, `SaveManager.lua` retrieves saved data and passes it to `GameManager.lua`.
  2. During gameplay, systems like `QuestManager.lua` call `SaveManager.lua` to update quest states.
  3. On game exit, `SaveManager.lua` writes the current state to storage.

### 3. **QuestManager.lua**
The `QuestManager.lua` script handles quest-related data and integrates with other systems.

- **Responsibilities:**
  - Tracks active, completed, and available quests.
  - Updates quest states based on player actions.
  - Communicates with `SaveManager.lua` to persist quest progress.

- **Example Workflow:**
  1. A player interacts with an NPC, triggering `DialogManager.lua`.
  2. If a quest is accepted, `QuestManager.lua` adds it to the active quests list.
  3. Upon completion, `QuestManager.lua` marks the quest as completed and updates `SaveManager.lua`.

### 4. **ContestManager.lua**
The `ContestManager.lua` script manages data related to dress-up contests.

- **Responsibilities:**
  - Tracks contest entries, voting progress, and results.
  - Updates player rankings and rewards.
  - Communicates with `SaveManager.lua` to persist player contest participation and results.

- **Example Workflow:**
  1. Players submit contest entries via `UIContest.lua`.
  2. `ContestManager.lua` updates the contest state with the new entry.
  3. After the contest ends, `ContestManager.lua` calculates results and rewards, updating `SaveManager.lua`.

### 5. **UIDressUp.lua and OutfitUtils.lua**
These scripts handle character customization and manage outfit data.

- **Responsibilities:**
  - `UIDressUp.lua` provides the UI for customizing characters.
  - `OutfitUtils.lua` manages outfit data and ensures compatibility across systems.
  - Updates customization data in `SaveManager.lua`.

- **Example Workflow:**
  1. A player customizes their character in `UIDressUp.lua`.
  2. The updated outfit data is saved using `OutfitUtils.lua`.
  3. `SaveManager.lua` persists the new outfit data.

## Data Flow Diagram

### Initialization
1. `GameManager.lua` initializes core systems.
2. `SaveManager.lua` loads saved data.
3. Data is distributed to `QuestManager.lua`, `ContestManager.lua`, and `UIDressUp.lua`.

### Runtime Updates
1. Systems exchange data as events occur (e.g., quests, contests).
2. Updated data is passed back to `SaveManager.lua` for persistence.

### Persistence
1. On game exit, `SaveManager.lua` writes all data to storage.

## Key Considerations
- **Data Consistency:** Ensure systems update shared data consistently to avoid conflicts.
- **Error Handling:** Implement fallback mechanisms for corrupted or missing save data.
- **Extensibility:** Modularize data flow to allow new features to integrate seamlessly.

## Next Steps

Continue exploring the game's data flow by examining the interactions between different systems and how they collectively manage game state. Understanding data flow is crucial for maintaining a robust and scalable game architecture.