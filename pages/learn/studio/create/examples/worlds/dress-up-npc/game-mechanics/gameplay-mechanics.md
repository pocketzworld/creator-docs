# Gameplay Mechanics

This document provides an in-depth overview of the core gameplay mechanics that form the foundation of the game. It explains how players interact with the various systems and how these systems are implemented through the codebase.

## Overview
The game is an interactive experience that allows players to:
- Participate in dress-up contests.
- Customize their characters with a variety of outfits and styles.
- Complete quests assigned by NPCs.
- Earn and spend rewards through in-game systems like the store and loot.

## Core Mechanics

### 1. **Contests**
Players can join themed dress-up contests, vote on entries, and view results. The system includes:
- **Submission:** Players submit their customized characters to contests based on a theme.
- **Voting:** Players vote for the best-matching outfits.
- **Results:** Rankings are displayed, and rewards are distributed.

**Relevant Scripts:**
- `ContestManager.lua`: Manages contest logic.
- `UIContest.lua`: Handles the contest UI.
- `UIContestVoting.lua`: Implements the voting interface.
- `UIContestResults.lua`: Displays contest results.

### 2. **Character Customization**
Players can customize their characters using the dress-up system. Key features include:
- Selecting clothing, hairstyles, and accessories.
- Previewing changes in real-time.
- Saving outfits for later use.

**Relevant Scripts:**
- `UIDressUp.lua`: Main script for the customization interface.
- `UIDressUpCloset.lua`: Handles the inventory of clothing items.
- `OutfitUtils.lua`: Provides utility functions for managing outfits.

### 3. **Quests**
Quests are assigned by NPCs to provide objectives and rewards. Features include:
- **Dialogue Interaction:** Players receive quests through NPC dialogues.
- **Task Completion:** Objectives such as creating specific outfits or participating in contests.
- **Rewards:** Players earn virtual currency or items upon completing quests.

**Relevant Scripts:**
- `QuestManager.lua`: Manages quest progression.
- `DialogManager.lua`: Handles NPC interactions.
- `UIDialog.lua`: Displays dialogue prompts.

### 4. **Store System**
The in-game store allows players to purchase cosmetic items using virtual currency. The system includes:
- A categorized list of items for purchase.
- Integration with the rewards and currency system.
- Dynamic updates to reflect available inventory.

**Relevant Scripts:**
- `ItemStore.lua`: Core logic for managing the store.
- `UIItemStore.lua`: Implements the store UI.

### 5. **Reward System**
Players earn rewards such as loot boxes or virtual currency by completing objectives or achieving rankings. Features include:
- **Reward Notifications:** Informing players of their earnings.
- **Loot Management:** Providing random or specific items based on achievements.

**Relevant Scripts:**
- `LootManager.lua`: Handles reward distribution.
- `UIReward.lua`: Manages the reward display interface.

### 6. **NPC Interactions**
NPCs are a vital part of the game, offering quests and engaging in dialogues. Features include:
- **Dialogue Trees:** Multiple-choice responses or linear narratives.
- **Task Assignment:** NPCs assign tasks that integrate with other mechanics.

**Relevant Scripts:**
- `DialogManager.lua`: Core logic for NPC dialogues.
- `UIDialog.lua`: Displays dialogue UI.

### 7. **User Interface (UI)**
The UI system ensures seamless interaction between players and the game. Features include:
- A main menu for navigation.
- Popups for rewards, quests, and other notifications.
- Dynamic updates to reflect player actions.

**Relevant Scripts:**
- `UIMain.lua`: Central UI logic.
- `UIGenericPopup.lua`: Handles popups for various events.
- `UIManager.lua`: Manages transitions between UI elements.

## Integration Notes
- Each gameplay mechanic is modular, allowing easy maintenance and updates.
- Scripts are grouped by functionality (e.g., `Contest`, `DressUp`, `Quests`) for organization.
- Utility scripts like `OutfitUtils.lua` provide shared functions to reduce redundancy.